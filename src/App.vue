<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Job'
import JobsList from './components/JobsList.vue';
import OderTerm from './types/OrderTerm'

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

    const order = ref<OderTerm>('title')

    const handleClick = (term: OderTerm) => {
      order.value = term
    }

    return {
      jobs,
      handleClick,
      order
    }
  }
})
</script>

<template>
  <div class="app">
    <header>
      <h1 class="title">Missions</h1>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order"/>
  </div>
</template>

<style scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
header .title{
  display: flex;
  justify-content: center;
}
header h1 {
  font-size: 3em;
}
button {
  margin: 0 10px;
  color: #198b28;
  border: 3px solid #198b28;
  background: #d5ffd8;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
