// This is not used

<template>
  <div class="filter-sort-search">
    <p>Ordered by {{ order }}</p>
    <button @click="handleClick('title')">Order by title</button>
    <button @click="handleClick('salary')">Order by salary</button>
    <button @click="handleClick('location')">Order by location</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, PropType } from 'vue'
import OrderTerm from '@/types/OrderTerm'

export default defineComponent({
  setup() {
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }
    return { handleClick, order }
  },
  provide() {
    return {
      //term: Vue.computed(() => this.order)
    }
  }
})

</script>