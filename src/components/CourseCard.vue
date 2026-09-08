<template>
  <article class="course-card">
    <div>
      <h3>ชื่อคอร์ส: {{ course.title }}</h3>
      <p>ราคา: {{ course.price }} บาท</p>
    </div>
    <button :disabled="!store.username" @click="addToFavorite">
      เพิ่มในรายการโปรด
    </button>
  </article>
</template>

<script setup>
import { useFavoriteStore } from "../stores/favorite";

const props = defineProps({
  course: {
    type: Object,
    required: true,
  },
});

const store = useFavoriteStore();

function addToFavorite() {
  store.addFavorite(props.course);
}
</script>

<style scoped>
.course-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 16px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fafafa;
  padding: 12px 16px;
  margin-bottom: 16px;
  text-align: left;
}

h3 {
  margin: 0;
  font-size: 16px;
  font-weight: 600;
}

p {
  margin: 0;
  color: #555;
}

button {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 6px;
  cursor: pointer;
  flex-shrink: 0;
}

button:hover {
  background-color: #2c9c6d;
}

button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

button:disabled:hover {
  background-color: #ccc;
}
</style>
