<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Job from '../types/Job';
import OrderTerm from '../types/OrderTerm';
import { computed } from '@vue/reactivity';

export default defineComponent({
  props: {
    jobs: {
      required: true,
      type: Array as PropType<Job[]>
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>
    }
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a: Job, b: Job) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return {
      orderedJobs
    }
  }
})
</script>

<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>$ {{ job.salary }}</p>
        </div>
        <div class="description">
          Lorem, ipsum dolor sit amet consectetur adipisicing elit. Voluptates, harum. Officiis placeat illo molestiae similique officia eveniet enim voluptates dolores laborum assumenda, voluptatum aperiam beatae non harum unde quas sunt.
        </div>
      </li>
    </transition-group>
  </div>
</template>

<style scoped>
.job-list {
  padding: 0;
  max-width: 960px;
  margin: 40px auto;
}
.job-list li {
  list-style-type: none;
  background: #1f1b24;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
.list-move {
  transition: all 500ms;
}
</style>