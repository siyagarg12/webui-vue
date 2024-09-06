<template>
  <div>
    <label for="dropdown">Select an option:</label>
    <select v-model="selectedOption" id="dropdown">
      <option disabled value="">Please select one</option>
      <option v-for="option in options" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
    <div v-if="selectedOption">You selected: {{ selectedOption }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedOption: '',
      options: ['Option 1', 'Option 2', 'Option 3', 'Option 4'],
    };
  },
};
</script>
