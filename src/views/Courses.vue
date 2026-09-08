<template>
  <div class="page-container">
    <header>
      <h2>📚 Course List</h2>
      <p>❤️ ถูกใจแล้ว {{ store.favorites.length }} คอร์ส</p>
    </header>

    <section class="form-section">
      <label for="username">ชื่อผู้ใช้:</label>
      <input
        id="username"
        v-model="username"
        placeholder="กรอกชื่อของคุณ"
      />
    </section>

    <section class="course-list">
      <CourseCard
        v-for="course in courses"
        :key="course.id"
        :course="course"
      />
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from "vue";
import axios from "axios";
import CourseCard from "../components/CourseCard.vue";
import { useFavoriteStore } from "../stores/favorite";

const store = useFavoriteStore();
const courses = ref([]);

const username = computed({
  get: () => store.username,
  set: (value) => store.setUsername(value),
});

onMounted(async () => {
  const { data } = await axios.get("https://fakestoreapi.com/products");
  courses.value = data;
});
</script>

<style scoped>
.page-container {
  max-width: 600px;
  margin: auto;
  text-align: center;
}
.form-section {
  margin-top: 16px;
}
.form-section input {
  margin-left: 8px;
  padding: 6px 10px;
  border-radius: 6px;
  border: 1px solid #ccc;
}
.course-list {
  margin-top: 24px;
}
</style>
