<script setup>
import stationOffcanvas from "./components/stationOffcanvas.vue";
import droneOffcanvas from "./components/droneOffcanvas.vue";
import NavBar from "./components/navBar.vue";
import RestStationOffcanvas from "./components/restStationOffcanvas.vue";
</script>

<template>
  <NavBar></NavBar>
  <div id="mapDiv"></div>

  <!-- STATION -->
  <stationOffcanvas id="1" stationName="ทวีวัฒนา"></stationOffcanvas>
  <stationOffcanvas id="2" stationName="พุทธมณฑลสาย 3"></stationOffcanvas>
  <RestStationOffcanvas id="1" stationName="ทวีวัฒนา"></RestStationOffcanvas>

  <!-- DRONE -->
  <droneOffcanvas id="1"></droneOffcanvas>
  <droneOffcanvas id="2"></droneOffcanvas>
  <droneOffcanvas id="3"></droneOffcanvas>
</template>

<script>
async function initMap() {
  var map = null
  let mapData = {
    id: "mapSample",
    logo: true,
    scalebar: true,
    basemap: "streetmap",
    slider: false,
    level: 15,
    lat: 13.760458,
    lon: 100.333664,
    country: "TH",
  }

  function showPosition(position) {
    console.log(position.coords.latitude)
    console.log(position.coords.longitude)
    mapData.lat = position.coords.latitude
    mapData.lon = position.coords.longitude
  }

  if (navigator.geolocation) {
    try {
      await navigator.geolocation.getCurrentPosition(showPosition);
      console.log('sus')
    } catch (err) {
      location = {
        lat: 13.722944,
        on: 100.530449,
      };
    }
  } else {
    location = {
      lat: 13.722944,
      on: 100.530449,
    };
  }
  map = new nostra.maps.Map("mapDiv", mapData);

  map.events.load = function () {
    //map is ready
    var myGraphicLayer = new nostra.maps.layers.GraphicsLayer(map, {
      id: "myGLayer",
    });
    map.addLayer(myGraphicLayer);

    let myLabel = new nostra.maps.symbols.Label({
      text: "DRONE@THAWI-WATTHANA #1",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let myPin = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: myLabel,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/drone.png'
    });
    myGraphicLayer.addMarker(13.787697, 100.327534, myPin);

    let drone2Label = new nostra.maps.symbols.Label({
      text: "DRONE@THAWI-WATTHANA #2",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let drone2 = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: drone2Label,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/drone.png'
    });
    myGraphicLayer.addMarker(13.766606, 100.338906, drone2);

    let drone3Label = new nostra.maps.symbols.Label({
      text: "DRONE@THAWI-WATTHANA #3",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let drone3 = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: drone3Label,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/drone.png'
    });
    myGraphicLayer.addMarker(13.759054, 100.324406, drone3);


    let myStation = new nostra.maps.symbols.Label({
      text: "THAWI WATTHANA STATION",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let station = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: myStation,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/helipad.png',
    });
    myGraphicLayer.addMarker(13.760458, 100.333664, station);

    let myStation2 = new nostra.maps.symbols.Label({
      text: "PHUTTHAMONTHON SAI 3 STATION",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let station2 = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: myStation2,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/helipad.png',
    });
    myGraphicLayer.addMarker(13.76316044998705, 100.36309502787836, station2);

        let myrestStation1 = new nostra.maps.symbols.Label({
      text: "REST STATION - THAWI WATTHANA",
      size: 10,
      position: "top",
      color: "#f9d628",
      haloColor: "#2b2727",
    });
    let restStation1 = new nostra.maps.symbols.Marker({
      width: 50,
      height: 50,
      label: myrestStation1,
      draggable: false,
      attribute: {
        class: 'cursor-hand'
      },
      url: '/src/assets/img/hourglass.png',
    });
    myGraphicLayer.addMarker(
      13.764044288730265,
      100.34713577907472,
      restStation1
    );

        restStation1.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let restStationCanvasEl = document.getElementById("rest-station-1-offcanvas");
      let restStationCanvas = new bootstrap.Offcanvas(restStationCanvasEl);
      restStationCanvas.show();
    };

    station.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let stationCanvasEl = document.getElementById("station-1-offcanvas");
      let stationCanvas = new bootstrap.Offcanvas(stationCanvasEl);
      stationCanvas.show();
    };

    station2.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let stationCanvasEl = document.getElementById("station-2-offcanvas");
      let stationCanvas = new bootstrap.Offcanvas(stationCanvasEl);
      stationCanvas.show();
    };

    myPin.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let droneCanvasEl = document.getElementById("drone-offcanvas-1");
      let droneCanvas = new bootstrap.Offcanvas(droneCanvasEl);
      droneCanvas.show();
    }

    drone2.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let droneCanvasEl = document.getElementById("drone-offcanvas-2");
      let droneCanvas = new bootstrap.Offcanvas(droneCanvasEl);
      droneCanvas.show();
    }

    drone3.onClick = function () {
      let otherCanvasEl = document.querySelectorAll('.offcanvas.show')
      otherCanvasEl.forEach((el) => {
        el.classList.remove('show')
      })

      let droneCanvasEl = document.getElementById("drone-offcanvas-3");
      let droneCanvas = new bootstrap.Offcanvas(droneCanvasEl);
      droneCanvas.show();
    }
  };
}
nostra.onready = function () {
  initMap();
};
</script>

<style scoped>
html,
body,
#mapDiv {
  padding: 0;
  margin: 0;
  height: 100%;
}
</style>
