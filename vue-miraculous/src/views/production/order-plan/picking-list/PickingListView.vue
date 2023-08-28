<template>
  <div class="container-fluid">
    <h2>ชื่อฟอร์ม</h2>
    <div class="row">
      <div class="col-sm-3">
        <form>
          <div class="form-group>">
            <img src="@/assets/ring.jpg" class="img-rounded img-responsive" height="200">
          </div>
          <div class="form-group>">
            <button type="button" class="btn btn-primary center">upload image</button>
          </div>
          <div class="form-group>">
            <label>แม่พิมพ์ : </label>
            <input type="text" class="form-control" id="num_wo">
          </div>
        </form>
      </div>
      <div class="col-sm-4">
        <form>
          <div class="form-group>">
            <label>เลขที่ W.O. : </label>
            <input type="text" class="form-control" id="num_wo">
          </div>
          <div class="form-group>">
            <label>ลำดับ W.O. : </label>
            <input type="text" class="form-control" id="num_wo">
          </div>
          <div class="form-group>">
            <label>รหัสสินค้า : </label>
            <input type="text" class="form-control" id="num_wo">
          </div>
        </form>
      </div>
      <div class="col-sm-4">
        <form>
          <div class="form-group>">
            <label>ใบจ่าย/รับคืนงาน : </label>
            <input type="date" class="form-control" id="num_wo">
          </div>
          <div class="form-group>">
            <label>Require Date : </label>
            <input type="date" class="form-control" id="num_wo">
          </div>
          <div class="form-group>">
            <label>รหัสลูกค้า : </label>
            <input type="text" class="form-control" id="num_wo">
          </div>
        </form>
      </div>
      <div class="col-sm-9">
        <form>
          <div class="form-group>">
            <label>Remark : </label>
            <input type="date" class="form-control" id="num_wo">
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
  .center {
    position: center;
  }
</style>
