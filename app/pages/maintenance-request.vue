<template>
  <div class="container">
    <h1>تقديم طلب الصيانة</h1>
    <form @submit.prevent="submitRequest">
      <!-- الخطوة 1: بيانات الفرع -->
      <div v-if="currentStep === 1">
        <h2>الخطوة 1: بيانات الفرع</h2>
        <label>معرف الفرع:</label>
        <input v-model="request.branchId" type="text" placeholder="أدخل معرف الفرع" required />
        <label>اسم الفرع:</label>
        <input v-model="request.branchName" type="text" placeholder="أدخل اسم الفرع" required />
        <label>اسم المسؤول:</label>
        <input v-model="request.managerName" type="text" placeholder="أدخل اسم المسؤول" required />
        <label>بريد الفرع:</label>
        <input v-model="request.branchEmail" type="email" placeholder="أدخل البريد" required />
        <label>رقم التواصل:</label>
        <input v-model="request.branchPhone" type="tel" placeholder="أدخل رقم التواصل" required />
        <label>تاريخ الطلب:</label>
        <input v-model="request.requestDate" type="date" required />
      </div>

      <!-- الخطوة 2: بيانات الصيانة -->
      <div v-if="currentStep === 2">
        <h2>الخطوة 2: بيانات الصيانة</h2>
        <div class="categories">
          <!-- قسم الصيانة -->
          <div>
            <h3>الصيانة</h3>
            <div v-for="category in maintenanceCategories" :key="category.id">
              <input type="checkbox" :value="category.name" v-model="request.maintenanceCategories" />
              <label>{{ category.name }}</label>
            </div>
          </div>
          <!-- قسم التجديدات -->
          <div>
            <h3>التجديدات</h3>
            <div v-for="category in renovationCategories" :key="category.id">
              <input type="checkbox" :value="category.name" v-model="request.maintenanceCategories" />
              <label>{{ category.name }}</label>
            </div>
          </div>
        </div>
        <label>تفاصيل الصيانة:</label>
        <textarea v-model="request.maintenanceDetails" placeholder="أدخل تفاصيل الصيانة"></textarea>
      </div>

      <!-- الخطوة 3: التاريخ والوقت والأولوية -->
      <div v-if="currentStep === 3">
        <h2>الخطوة 3: التاريخ والوقت والأولوية</h2>
        <label>التاريخ المتوقع للصيانة:</label>
        <input v-model="request.maintenanceDate" type="date" required />
        <label>أفضل وقت للصيانة:</label>
        <input v-model="request.preferredTime" type="time" required />
        <label>أولوية الصيانة:</label>
        <select v-model="request.priority" required>
          <option value="عادي">عادي</option>
          <option value="متوسط">متوسط</option>
          <option value="عاجل">عاجل</option>
        </select>
      </div>

      <!-- الخطوة 4: رفع الصور والملفات -->
      <div v-if="currentStep === 4">
        <h2>الخطوة 4: رفع الصور والملفات</h2>
        <label>رفع صور الأعطال:</label>
        <input type="file" @change="handleFiles($event, 'images')" multiple />
        <label>رفع ملفات الأعطال:</label>
        <input type="file" @change="handleFiles($event, 'files')" multiple />
      </div>

      <!-- الخطوة 5: تقييم الخدمة -->
      <div v-if="currentStep === 5">
        <h2>الخطوة 5: تقييم الخدمة</h2>
        <div>
          <label>التقييم:</label>
          <div>
            <span v-for="star in 5" :key="star" @click="request.rating = star" :class="{'active-star': star <= request.rating}">
              ★
            </span>
          </div>
        </div>
      </div>

      <!-- أزرار التنقل بين الخطوات -->
      <div class="buttons">
        <button type="button" @click="prevStep" v-if="currentStep > 1">السابق</button>
        <button type="button" @click="nextStep" v-if="currentStep < 5">التالي</button>
        <button type="submit" v-if="currentStep === 5">إرسال الطلب</button>
      </div>
    </form>

    <!-- صفحة الشكر -->
    <div v-if="submitted">
      <h2>تم إرسال الطلب بنجاح!</h2>
      <p>سيتم الرد عليكم في أقرب وقت.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentStep: 1,
      submitted: false,
      maintenanceCategories: [
        { id: 1, name: "كهرباء" },
        { id: 2, name: "إضاءة" },
        { id: 3, name: "Fiar / IT" },
        { id: 4, name: "الشبكة" },
        { id: 5, name: "تكييف الهواء" },
        { id: 6, name: "أعمال الزجاج" },
        { id: 7, name: "النجارة" },
        { id: 8, name: "رسم" },
        { id: 9, name: "كسر" },
        { id: 10, name: "آخر" },
      ],
      renovationCategories: [
        { id: 11, name: "وحدات العرض" },
        { id: 12, name: "وحدات التخزين" },
        { id: 13, name: "وحدات العداد" },
        { id: 14, name: "تركيب الديكور" },
        { id: 15, name: "التجهيز" },
        { id: 16, name: "عربة" },
        { id: 17, name: "سقف الجبس" },
        { id: 18, name: "حجران الجبس" },
        { id: 19, name: "البلاط" },
        { id: 20, name: "الواجهات" },
      ],
      request: {
        branchId: "",
        branchName: "",
        managerName: "",
        branchEmail: "",
        branchPhone: "",
        requestDate: "",
        maintenanceCategories: [],
        maintenanceDetails: "",
        maintenanceDate: "",
        preferredTime: "",
        priority: "",
        images: [],
        files: [],
        rating: 0,
      },
    };
  },
  methods: {
    nextStep() {
      if (this.currentStep < 5) this.currentStep++;
    },
    prevStep() {
      if (this.currentStep > 1) this.currentStep--;
    },
    handleFiles(event, type) {
      const files = Array.from(event.target.files);
      this.request[type] = files;
    },
    submitRequest() {
      console.log(this.request);
      this.submitted = true;
    },
  },
};
</script>

<style>
.categories {
  display: flex;
  gap: 2rem;
  justify-content: space-between;
}
.categories div {
  flex: 1;
}
.categories h3 {
  margin-bottom: 0.5rem;
}
.categories label {
  margin-left: 0.5rem;
}
.buttons {
  margin-top: 1rem;
  display: flex;
  gap: 1rem;
}
.active-star {
  color: gold;
  cursor: pointer;
}
</style>
