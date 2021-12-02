<template>
  <div class="w-full md:w-1/2">
    <label for="input-video">{{ isLoading ? "読み込み中..." : "動画を選択" }}</label>
    <input
      type="file"
      accept="video/mp4,video/x-m4v"
      @change="handleFileSelect"
    />
    
    <video controls v-if="src" class="w-full">
      <source :src="src" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"' />
    </video>
  </div>
</template>

<script>
import { ref, defineComponent } from 'vue'

export default defineComponent({
  setup() {
    const isLoading = false;
    const src = ref("");

    const handleFileSelect = (event) => {
      src.value = "";
      const file = event.target.files[0];
      if (!file || !file.type.match('video/*')) return

      // read file
      const reader = new FileReader()
      reader.onload = (evt) => {
        src.value = evt.target.result;
        isLoading.value = false;
      }
      reader.readAsDataURL(file);
      isLoading.value = true;
    }

    return{
      isLoading,
      src,
      handleFileSelect
    }
  },
})
</script>
