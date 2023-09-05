<template>
  <div class="app-container">
    <div class="form-container">
      <form>
        <div class="data-container">
          <h6>1. {{ $t('view.pickinglist.dataTitle') }} <i class="bi bi-card-list"></i></h6>
          <div class="data-input-container">
            <div class="input-container">
              <div>
                <label>{{ $t('view.pickinglist.title.wo') }}</label>
                <input type="text" class="form-control box-input" v-model="form.wo" required />
              </div>
              <div>
                <label>{{ $t('view.pickinglist.title.nowo') }}</label>
                <input
                  type="number"
                  min="1"
                  class="form-control box-input"
                  v-model="form.nowo"
                  required
                />
              </div>
              <div>
                <label>{{ $t('view.pickinglist.title.requestDate') }}</label>
                <input
                  type="date"
                  class="form-control box-input"
                  v-model="form.requestDate"
                  required
                />
              </div>
            </div>
          </div>
          <div class="data-input-container">
            <div class="input-container">
              <div>
                <label>{{ $t('view.pickinglist.title.mold') }}</label>
                <input type="text" class="form-control box-input" v-model="form.mold" required />
              </div>
              <div>
                <label>{{ $t('view.pickinglist.title.productNumber') }}</label>
                <input
                  type="text"
                  class="form-control box-input"
                  v-model="form.productNumber"
                  required
                />
              </div>
              <div>
                <label>{{ $t('view.pickinglist.title.customerNumber') }}</label>
                <input
                  type="text"
                  class="form-control box-input"
                  v-model="form.customerNumber"
                  required
                />
              </div>
            </div>
          </div>
          <div class="data-input-remark-container">
            <div class="input-container">
              <label>{{ $t('view.pickinglist.title.remark') }}</label>
              <textarea class="box-text-area" v-model="remark"></textarea>
            </div>
          </div>
        </div>
        <div class="upload-container">
          <h6 style="padding-bottom: 20px">
            2. {{ $t('view.pickinglist.uploadImag') }} <i class="bi bi-image"></i>
          </h6>
          <div class="select-preview-container">
            <div class="preveiw-container" v-if="imageUrls.length">
              <div class="image-container" v-for="(imageUrl, index) in imageUrls" :key="index">
                <img :src="imageUrl" alt="Preview" class="preview-image" />
                <span @click="deleteImage(index)" class="delete-icon">&#10006;</span>
              </div>
            </div>
            <div class="select-continer">
              <input
                type="file"
                multiple
                name="file"
                class="hidden-input"
                @change="previewImages"
                ref="file"
                accept=".jpg, .png"
              />
              <i class="bi bi-plus-circle" style="font-size: 30px"></i>
            </div>
          </div>
        </div>
        <div class="data-container">
          <h6>3. {{ $t('view.pickinglist.dataTitle') }}</h6>
          <div class="data-input-container"></div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
//import UploadImg from '@/components/btn-import/UploadImages.vue'
export default {
  components: {
    //UploadImg
  },
  data() {
    return {
      imageUrls: [],
      form: {
        wo: null,
        nowo: null,
        requestDate: new Date().toISOString().substr(0, 10),
        mold: null,
        productNumber: null,
        customerNumber: null,
        remark: null
      }
    }
  },
  methods: {
    previewImages() {
      console.log(this.$refs.file)
      const temFiles = this.$refs.file
      const files = temFiles.files

      for (let i = 0; i < files.length; i++) {
        const file = files[i]
        if (file) {
          const reader = new FileReader()
          reader.onload = (event) => {
            this.imageUrls.push(event.target.result)
          }
          reader.readAsDataURL(file)
        }
      }
    },
    deleteImage(index) {
      this.imageUrls.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
.app-container {
  padding: 20px 150px 20px 150px;
}
.form-container {
  //border: 1px solid white;
  //border-radius: 5px;
  //box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  //background-color: #f7f7f7;
  //padding: 20px;
  //height: 100px;
  h6 {
    padding: 10px 0px 10px 0px;
    color: var(--base-font-color);
  }

  .upload-container {
    border: 1px solid white;
    border-radius: 5px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    background-color: #f7f7f7;
    padding: 20px;
    margin-bottom: 20px;
    //display: grid;
    //justify-content: center;
    .select-preview-container {
      display: flex;
      flex-direction: row;
      .preveiw-container {
        display: flex;
        //justify-content: center;
        width: auto;
        overflow-x: auto; /* เพิ่มการเลื่อนในแนวนอน */
        white-space: nowrap; /* ป้องกันข้อความขึ้นบรรทัดใหม่ */
        //width: 100%;
      }
      .select-continer {
        display: flex;
        justify-content: center;
        align-items: center;
        //background-color: var(--base-color);
        height: 130px;
        width: 130px;
        border: 1px solid var(--base-color);
        color: var(--base-color);
        //margin: 0px 0px 0px 0px;
        .hidden-input {
          opacity: 0;
          overflow: hidden;
          position: absolute;
          width: 130px;
          height: 130px;
        }
      }
      .select-continer:hover {
        border: 1px solid var(--base-font-color);
        color: var(--base-font-color);
        //margin: 0px 0px 0px 10px;
      }
      .image-container {
        display: inline-block;
        position: relative;
        .preview-image {
          height: 130px;
          width: 130px;
          margin-right: 5px;
          border: 0.1px solid var(--base-color);
        }
        .delete-icon {
          position: absolute;
          top: 0;
          right: 0;
          margin-right: 10px;
          cursor: pointer;
          padding: 5px;
          color: var(--base-color);
          &:hover {
            color: var(--base-font-color);
          }
        }
      }
    }
  }
  .data-container {
    border: 1px solid white;
    border-radius: 5px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    background-color: #f7f7f7;
    //padding: 20px;
    padding: 20px;
    margin-bottom: 20px;

    .data-input-container {
      .input-container {
        padding: 5px 70px 0px 70px;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; /* แบ่งหน้าจอออกเป็นสองส่วนเท่าๆ กัน */
        gap: 50px; /* ระยะห่างระหว่างส่วน */
      }
      .box-input {
        width: calc(100% - 20px);
        min-width: 128px;
      }
    }
    .data-input-remark-container {
      .input-container {
        padding: 5px 70px 0px 70px;
        display: grid;
        //grid-template-columns: 1fr; /* แบ่งหน้าจอออกเป็นสองส่วนเท่าๆ กัน */
        //gap: 50px; /* ระยะห่างระหว่างส่วน */
        .box-text-area {
          width: calc(100% - 20px);
          min-width: 128px;
          border: 0.1px solid var(--base-color);
          overflow: auto;
          height: 80px;
        }
      }
    }
  }
}
</style>
