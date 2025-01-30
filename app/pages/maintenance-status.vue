<template>
  <div class="maintenance-status">
    <h1>Maintenance Status</h1>
    <div v-if="loading" class="loading">Loading...</div>
    <div v-else>
      <ul>
        <li v-for="request in maintenanceRequests" :key="request.id">
          <h2>{{ request.title }}</h2>
          <p>Status: {{ request.status }}</p>
          <p>{{ request.description }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const maintenanceRequests = ref([])
const loading = ref(true)

const fetchMaintenanceRequests = async () => {
  try {
    const response = await fetch('/api/maintenance-requests')
    maintenanceRequests.value = await response.json()
  } catch (error) {
    console.error('Failed to fetch maintenance requests:', error)
  } finally {
    loading.value = false
  }
}

onMounted(fetchMaintenanceRequests)
</script>

<style scoped>
.maintenance-status {
  padding: 20px;
}

.loading {
  text-align: center;
  font-size: 20px;
}
</style>
