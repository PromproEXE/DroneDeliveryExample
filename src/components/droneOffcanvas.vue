<script setup>
defineProps({
  id: {
    type: String,
    required: true,
  }
})
</script>
<template>
  <div class="offcanvas offcanvas-start" data-bs-scroll="true" data-bs-backdrop="false" tabindex="-1"
   :id="'drone-offcanvas-' + id" aria-labelledby="offcanvasScrollingLabel">
    <div class="offcanvas-header">
      <h2 class="offcanvas-title fw-bold" id="offcanvasScrollingLabel">ข้อมูลโดรน</h2>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body pt-0">
      <div class="rounded-4 shadow my-3">
        <div class="text-center mb-3">
          <div class="p-3 d-flex justify-content-end">
                                          <small class="text-muted me-2"><i class="fa-solid fa-battery-three-quarters"></i> {{ randomNumber()
                }}%</small>
                <small class="text-muted fw-bold"><i class="fa-solid fa-signal"></i></small>
          </div>
          <img src="/src/assets/img/drone.png" class="w-50 mb-3" alt="station" />
          <h2 class="fw-bold">โดรนที่ {{ id }}</h2>
          <h5 class="text-muted">สถานีกระจายทวีวัฒนา</h5>
        </div>

        <div class="row px-5">
          <div class="col-5">
            <p class="fw-bold">ออเดอร์:</p>
          </div>
          <div class="col-7">
            <p>12709747</p>
          </div>
          <div class="col-5">
            <p class="fw-bold">เป้าหมาย:</p>
          </div>
          <div class="col-7">
            <p>23 หมู่ 8 สถาบันกัลยาณ์ราชนครินทร์ ทวีวัฒนา ทวีวัฒนา กรุงเทพฯ 10170</p>
          </div>
        </div>
      </div>
      <button class="btn shadow rounded-3 w-100 text-start text-success mb-2">ดูข้อมูลออเดอร์</button>
      <button class="btn shadow rounded-3 w-100 text-start text-warning mb-2">เรียกโดรนกลับศูนย์</button>
      <button class="btn shadow rounded-3 w-100 text-start text-danger">ควบคุมโดรนด้วยตัวเอง</button>
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