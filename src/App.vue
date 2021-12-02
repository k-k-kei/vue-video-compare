<template>
  <div class="flex">
    <VideoInputForm />
    <VideoInputForm />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import VideoInputForm from "./components/VideoInputForm.vue";

export default defineComponent({
  components: {
      VideoInputForm
  },
})
</script>

