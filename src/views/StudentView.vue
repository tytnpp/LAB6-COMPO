<script setup lang="ts">
import StudentCard from '../components/StudentCard.vue'
import type { StudentItem } from '@/type'

import { ref } from 'vue'
import StudentService from '@/services/StudentService'
const students = ref<StudentItem[]>([])
StudentService.getEvent().then((response) => {
  students.value = response.data
})
</script>

<template>
  <h1>Events For Good</h1>
  <main class="events">
    <StudentCard v-for="student in students" :key="student.id" :student="student"></StudentCard>
  </main>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
