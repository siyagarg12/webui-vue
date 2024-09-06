<template>
  <div>
    <button @click="pickFile">Pick a File</button>
    <input
      type="file"
      ref="fileInput"
      @change="handleFileChange"
      style="display: none"
    />
    <div v-if="fileName">Selected File: {{ fileName }}</div>
  </div>
</template>

<script>
export default {
  name: 'CdacFeture',
  data() {
    return {
      fileName: null,
    };
  },
  methods: {
    pickFile() {
      this.$refs.fileInput.click();
    },
    handleFileChange(event) {
      const file = event.target.files[0];
      if (file) {
        this.fileName = file.name;
      }
    },
  },
};
</script>
