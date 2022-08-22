<script setup>
defineProps({
    id: {
        type: String,
        require: true
    },
    'stationName': {
        type: String,
        require: true
    }
})
</script>
<template>
  <div class="offcanvas offcanvas-start" data-bs-scroll="true" data-bs-backdrop="false" tabindex="-1"
    :id="'station-' + id + '-offcanvas'" aria-labelledby="offcanvasScrollingLabel">
    <div class="offcanvas-header">
      <h2 class="offcanvas-title fw-bold" id="offcanvasScrollingLabel">ข้อมูลสถานี</h2>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body pt-0">
      <div class="rounded-4 shadow my-3">
        <div class="text-center">
          <img src="/src/assets/img/headquarters.png" class="w-50 mb-3" alt="station" />
          <h2 class="fw-bold">สถานีกระจาย{{ stationName }}</h2>
        </div>

        <div class="row px-5">
          <div class="col-7">
            <p class="fw-bold">จำนวนโดรนทั้งหมด</p>
          </div>
          <div class="col-5 text-center">
            <p>10 ลำ</p>
          </div>
          <div class="col-7">
            <p class="fw-bold">กำลังใช้งาน</p>
          </div>
          <div class="col-5 text-center">
            <p>3 ลำ</p>
          </div>
          <div class="col-7">
            <p class="fw-bold">พร้อมใช้งาน</p>
          </div>
          <div class="col-5 text-center">
            <p>3 ลำ</p>
          </div>
          <div class="col-7">
            <p class="fw-bold">ไม่พร้อมใช้งาน</p>
          </div>
          <div class="col-5 text-center">
            <p>4 ลำ</p>
          </div>
        </div>
      </div>
      <button class="btn shadow rounded-3 w-100 text-start text-danger mb-3">เรียกโดรนทั้งหมดกลับศูนย์</button>
      <button class="btn btn-light text-success mb-3" type="button" data-bs-toggle="collapse"
        data-bs-target="#used-drone" aria-expanded="false" aria-controls="used-drone">
        <i class="fa-solid fa-chevron-down me-2"></i>โดรนที่กำลังใช้งาน
      </button>
      <div class="collapse" id="used-drone">
        <div class="rounded-4 shadow my-3 custom-card" v-for="n in 3">
          <div class="row p-4">
            <div class="col-5">
              <div class="text-center">
                <img src="/src/assets/img/drone.png" class="w-75" alt="station" />
              </div>
            </div>
            <div class="col-7">
              <div class="d-flex align-items-end">
                <h4 class="fw-bold mb-0 me-2 custom-card-text">โดรนที่ {{ n }}</h4>
                <small class="text-muted"><i class="fa-solid fa-battery-three-quarters"></i> {{ randomNumber()
                }}%</small>
              </div>
              <small class="text-muted mb-1">DJI Matrice 600</small>
              <p class="fw-bold mb-0">ออเดอร์:</p>
              <p class="mb-0">12709747</p>
            </div>
          </div>
        </div>
      </div>
      <div>
        <button class="btn btn-light text-warning mb-3" type="button" data-bs-toggle="collapse"
          data-bs-target="#standby-drone" aria-expanded="false" aria-controls="standby-drone">
          <i class="fa-solid fa-chevron-down me-2"></i>โดรนที่พร้อมใช้งาน
        </button>
      </div>

      <div class="collapse" id="standby-drone">
        <div class="rounded-4 shadow my-3 custom-card" v-for="n in 3">
          <div class="row p-4">
            <div class="col-5">
              <div class="text-center">
                <img src="/src/assets/img/drone.png" class="w-75" alt="station" />
              </div>
            </div>
            <div class="col-7">
              <div class="d-flex align-items-end">
                <h4 class="fw-bold mb-0 me-2 custom-card-text">โดรนที่ {{ n + 3 }}</h4>
                <small class="text-muted"><i class="fa-solid fa-battery-three-quarters"></i> {{ randomNumber()
                }}%</small>
              </div>
              <small class="text-muted mb-1">DJI Matrice 600</small>
            </div>
          </div>
        </div>
      </div>
      <div>
        <button class="btn btn-light text-danger mb-3" type="button" data-bs-toggle="collapse"
          data-bs-target="#notready-drone" aria-expanded="false" aria-controls="notready-drone">
          <i class="fa-solid fa-chevron-down me-2"></i>โดรนที่ไม่พร้อมใช้งาน
        </button>
      </div>

      <div class="collapse" id="notready-drone">
        <div class="rounded-4 shadow my-3 custom-card" v-for="n in 4">
          <div class="row p-4">
            <div class="col-5">
              <div class="text-center">
                <img src="/src/assets/img/drone.png" class="w-75" alt="station" />
              </div>
            </div>
            <div class="col-7">
              <div class="d-flex align-items-end">
                <h4 class="fw-bold mb-0 me-2 custom-card-text">โดรนที่ {{ n + 6 }}</h4>
                <small class="text-muted"><i class="fa-solid fa-battery-three-quarters"></i> {{ randomNumber()
                }}%</small>
              </div>
              <small class="text-muted mb-1">DJI Matrice 600</small>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    randomNumber() {
      return Math.floor(Math.random() * (100 - 1 + 1)) + 1
    }
  }
}
</script>