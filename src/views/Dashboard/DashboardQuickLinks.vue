<template>
  <b-card bg-color="orange" border-variant="light">
    <div class="widgets">
      <widget-component
        :percentages="[75, 50, 25]"
        title="Temperature sensors"
      />
      <widget-component :percentages="[80, 60, 40, 20]" title="CPU sensors" />
      <widget-component :percentages="[50, 30]" title="Fan sensors" />
    </div>
  </b-card>
</template>
<script>
import WidgetComponent from './WidgetComponent.vue';
export default {
  name: 'DashboardQuickLinks',
  components: {
    WidgetComponent,
  },
};
</script>

<style lang="scss" scoped>
dd,
dl {
  margin: 0;
}
.widgets {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}
</style>
