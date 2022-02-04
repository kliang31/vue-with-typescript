<template>
  <div class="app">
    <div>
      <p>Ordered by {{ order }}</p>
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from './types/Jobs';
import OrderTerm from './types/OrderTerm';
import JobList from './components/JobsList.vue';

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {title: 'farm worker', location: 'lonlon reanch', salary: 3000, id: 'A'},
      {title: 'ranch worker', location: 'cattle farm', salary: 5000, id: 'B'},
      {title: 'fish worker', location: 'fish farm', salary: 500, id: 'C'},
      {title: 'dominoes worker', location: 'gig economy', salary: 3, id: 'D'}
      
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }

    return {jobs, handleClick, order}
  },

});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #0a7555;
    border: 3px solid #0a7555;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
