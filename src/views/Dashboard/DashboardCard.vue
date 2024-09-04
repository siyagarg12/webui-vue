<template>
  <b-card bg-variant="light" border-variant="light" class="mb-4">
    <div class="justify-content-between align-items-center d-flex flex-wrap">
      <h3 class="h5 mb-0">{{ title }}</h3>
    </div>
    <slot></slot>
  </b-card>
</template>

<script>
export default {
  name: 'OverviewCard',
  props: {
    data: {
      type: Array,
      default: () => [],
    },
    disabled: {
      type: Boolean,
      default: true,
    },
    downloadButton: {
      type: Boolean,
      default: false,
    },
    exportButton: {
      type: Boolean,
      default: false,
    },

    fileName: {
      type: String,
      default: 'data',
    },
    title: {
      type: String,
      default: '',
    },
    to: {
      type: String,
      default: '/',
    },
  },
};
</script>

<style lang="scss" scoped>
a {
  vertical-align: middle;
  font-size: 14px;
}
.card {
  min-width: 310px;
}
</style>
