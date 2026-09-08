<template>
  <div class="page-container">
    <h2>📋 Summary</h2>
    <section v-if="store.username && store.favorites.length">
      <p>ชื่อผู้ใช้: {{ store.username }}</p>
      <p>จำนวนคอร์สที่ถูกใจ: {{ store.favorites.length }}</p>
    </section>
    <p v-else>ยังไม่มีข้อมูลการเลือกคอร์ส</p>
    <RouterLink to="/">กลับไปหน้า Course</RouterLink>
  </div>
</template>

<script setup>
import { RouterLink } from "vue-router";
import { useFavoriteStore } from "../stores/favorite";

const store = useFavoriteStore();
</script>

<style scoped>
.page-container {
  text-align: center;
  padding: 40px;
}
</style>
