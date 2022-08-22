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
    :id="'rest-station-' + id + '-offcanvas'" aria-labelledby="offcanvasScrollingLabel">
    <div class="offcanvas-header">
      <h2 class="offcanvas-title fw-bold" id="offcanvasScrollingLabel">ข้อมูลสถานี</h2>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body pt-0">
      <div class="rounded-4 shadow my-3">
        <div class="text-center">
          <img src="/src/assets/img/separate.png" class="w-50 mb-3" alt="station" />
          <h2 class="fw-bold">สถานีเชื่อมต่อ{{ stationName }}</h2>
        </div>

        <div class="row px-5">
          <div class="col-7">
            <p class="fw-bold">จำนวนออเดอร์ที่ค้างอยู่</p>
          </div>
          <div class="col-5 text-center">
            <p>1 ออเดอร์</p>
          </div>
        </div>
      </div>
                    <button class="btn btn-light text-danger mb-3" type="button" data-bs-toggle="collapse"
        data-bs-target="#used-drone" aria-expanded="false" aria-controls="used-drone">
        <i class="fa-solid fa-chevron-down me-2"></i>ออเดอร์ที่ค้างอยู่
      </button>
      <div class="collapse" id="used-drone">
        <div class="rounded-4 shadow my-3 custom-card" v-for="n in 1">
          <div class="row p-4">
            <div class="col-5">
              <div class="text-center">
                <img src="/src/assets/img/diet.png" class="w-75" alt="station" />
              </div>
            </div>
            <div class="col-7">
              <h4 class="fw-bold mb-0 me-2 custom-card-text">192847509</h4>
              <small class="text-muted mb-1">จากคุณชาญวิช มาศมัณฑนะ</small>
            </div>
          </div>
        </div>
      </div>
      <!-- <button class="btn shadow rounded-3 w-100 text-start text-danger mb-3">เรียกโดรนทั้งหมดกลับศูนย์</button> -->
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