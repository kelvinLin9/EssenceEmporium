<template>
<div class="modal fade" id="editMyCourseModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true" data-bs-backdrop="static">
  <div class="modal-dialog modal-lg">
    <div class="modal-content">
      <div class="modal-header">
        <h1 class="modal-title fs-5" id="exampleModalLabel">編輯我的課程資料</h1>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <!-- <VForm class="mx-auto"
                v-slot="{ errors }"
                @submit="UpdateFirebaseUserCourseData(courseData.id)">
          <div class="row mb-3">
            <div class="col-auto">
              <label for="courseName" class="col-form-label">
                課程名稱：
              </label>
            </div>
            <div class="col-4">
          <VField
            name="課程名稱"
            id="courseName"
            type="text"
            rules="required|min:3|max:20"
            class="form-control"
            :class="{ 'is-invalid': errors['課程名稱'] }"
            placeholder="請輸入課程名稱"
            v-model="courseData.courseName"
          />
          <ErrorMessage class="invalid-feedback" name="課程名稱"/>
            </div>
          </div>
          <div class="row mb-3">
            <div class="col-auto">
              <label for="coursePrice" class="col-form-label">
                課程費用：
              </label>
            </div>
          <div class="col-4">
            <VField
              name="課程費用"
              id="coursePrice"
              type="number"
              rules="required|min_value:100|max_value:100000"
              class="form-control"
              :class="{ 'is-invalid': errors['課程費用'] }"
              placeholder="請輸入課程費用"
              v-model="courseData.price"
            />
            <ErrorMessage class="invalid-feedback" name="課程費用"/>
          </div>
          </div>
          <div class="row mb-3">
            <div class="col-auto">
              <label for="courseTime" class="col-form-label">
                授課時間：
              </label>
            </div>
            <div class="col-4">
              <VField
                name="授課時間"
                id="courseTime"
                type="number"
                rules="required|min_value:30|max_value:600"
                class="form-control"
                :class="{ 'is-invalid': errors['授課時間'] }"
                placeholder="請輸入授課時間(分鐘)"
                v-model="courseData.time"
              />
              <ErrorMessage class="invalid-feedback" name="授課時間"/>
            </div>
          </div>


        
          <div class="row mb-3">
            <div class="col-12 col-lg-8 mb-3">
              <div class="row">
                <div class="col-4">
                  <label for="coursePhoto" 
                      class="col-form-label"
                      accept="image/png, image/jpeg">
                    上傳一張課程封面照：
                  </label>
                </div>
                <div class="col-8">
                  <VField
                  name="課程封面"
                  type="file"
                  id="coursePhoto"
                  class="form-control"
                  rules="required"
                  v-model="courseData.courseImg"
                  :class="{ 'is-invalid': errors['課程封面'] }"
                  @change="uploadPhoto('course',$event)"
                >
              </VField>
              <ErrorMessage class="invalid-feedback" name="課程封面"/>
                  <img class="img-fluid mt-3" 
                      :src="beATeacherData.courseImg" 
                      alt="課程封面照(新)"
                      v-if="beATeacherData.courseImg"/>
                  <img class="img-fluid mt-3" 
                      :src="courseData.courseImg" 
                      alt="課程封面照(舊)"
                      v-else/>
                </div>
              </div>
            </div>
          </div>
          <button type="button" class="btn btn-secondary me-3" data-bs-dismiss="modal">
            取消
          </button>
          <button type="submit" class="btn btn-primary" data-bs-dismiss="modal">
            確認
          </button>
        </VForm> -->
      </div>
      <div class="modal-footer">
      </div>
    </div>
  </div>
</div>
</template>
  
<script setup>
import { ref } from 'vue'

</script>

<style lang="scss" scoped>

</style>