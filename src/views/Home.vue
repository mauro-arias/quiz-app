<template>
  <div class="container mx-auto mt-2">
    <CategorySelector />
  </div>
</template>

<script>
// @ is an alias to /src
import CategorySelector from '@/components/CategorySelector.vue'

export default {
  name: 'Home',
  components: {
    CategorySelector
  }
}
</script>
