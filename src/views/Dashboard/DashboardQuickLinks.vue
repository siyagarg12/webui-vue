<template>
  <b-card bg-color="orange" border-variant="light">
    <div class="widgets">
      <widget-component
        :percentages="temperaturePercentages"
        title="Temperature sensors"
      />
      <widget-component :percentages="cpuPercentages" title="CPU usage" />
      <widget-component :percentages="fanPercentages" title="Fan speed" />
    </div>
  </b-card>
</template>
<script>
import WidgetComponent from './WidgetComponent.vue';
import jsonData from '../../../public/data.json';
export default {
  name: 'DashboardQuickLinks',
  components: {
    WidgetComponent,
  },
  data() {
    return {
      jsonData,
    };
  },
  computed: {
    temperaturePercentages() {
      const temperatures = jsonData.Temperature;
      return temperatures;
    },
    cpuPercentages() {
      const cpuUsages = jsonData.CPU;
      return cpuUsages;
    },
    fanPercentages() {
      const fanUsages = jsonData['Fan Usage'];
      return fanUsages;
    },
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
