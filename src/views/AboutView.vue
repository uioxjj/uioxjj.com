<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script>
// @ is an alias to /src
import topHead from '@/components/head.vue'

export default {
  name: 'AboutView',
  components: {
    topHead
  }
}
</script>

<style>
body {
  margin: 0px;
}
</style>
