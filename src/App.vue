<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import JobsList from './components/JobsList.vue';

export default defineComponent({
  name: 'App',
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: 'Infiltration',
        location: 'New York, NY',
        salary: 3000000,
        id: '1'
      },
      {
        title: 'Recon environment',
        location: 'Shadow Moses Island, Alaska',
        salary: 10000,
        id: '2'
      },
      {
        title: 'Rescue Hostage',
        location: 'Off-shore plant',
        salary: 100000000,
        id: '3'
      },
      {
        title: 'Sabotage Grozny Grad',
        location: 'Grozny Grad, Russia',
        salary: 25000000,
        id: '4'
      },
      {
        title: 'Eliminate Liquid Ocelot',
        location: 'Unknown Location',
        salary: 99999999,
        id: '5'
      }
    ])

    return {
      jobs
    }
  }
})
</script>

<template>
  <div class="app">
    <JobsList :jobs="jobs" />
  </div>
</template>

<style scoped>
</style>
