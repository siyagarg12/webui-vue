<template>
  <div class="rainbow-widget">
    <svg viewBox="-2 -2 40 40" class="circular-chart">
      <path
        v-for="(percentage, index) in percentages"
        :key="index"
        class="circle-bg"
        :d="getCirclePath(index)"
      />
      <path
        v-for="(percentage, index) in percentages"
        :key="`circle-${index}`"
        class="circle"
        :class="`circle-${index}`"
        :stroke-dasharray="`${percentage}, 100`"
        :d="getCirclePath(index)"
        :style="{ stroke: getColor(index) }"
      />
      <text
        v-if="title === 'CPU usage'"
        x="18"
        y="22"
        class="percentage-text"
        text-anchor="middle"
        :fill="getColor(0)"
        font-size="8"
      >
        {{ percentages[0] }}%
      </text>
    </svg>
    <h3>{{ title }}</h3>
  </div>
</template>

<script>
export default {
  props: {
    percentages: {
      type: Array,
      required: true, // Default to 3 circles if not provided
    },
    title: {
      type: String,
      required: true,
    },
  },
  methods: {
    getCirclePath(index) {
      const radius = 16.9155 - index * 4; // Adjust radius for each circle
      return `
        M18 ${18 - radius}
        a ${radius} ${radius} 0 0 1 0 ${2 * radius}
        a ${radius} ${radius} 0 0 1 0 -${2 * radius}
      `;
    },
    getColor(index) {
      // You can modify this color array or create a more sophisticated color calculation
      const colors = ['#1E90FF', '#00BFFF', '#87CEEB', '#4682B4', '#5F9EA0'];
      return colors[index % colors.length];
    },
  },
};
</script>

<style scoped>
.circular-chart {
  max-width: 150px;
  max-height: 150px;
  display: block;
  margin: 10px auto;
}

.circle-bg {
  fill: none;
  stroke: #eee;
  stroke-width: 3.8;
}

.circle {
  fill: none;
  stroke-width: 2.8;
  stroke-linecap: round;
  animation: progress 1s ease-out forwards;
}

.percentage {
  fill: #fff;
  font-family: Arial, sans-serif;
  font-size: 0.5em;
  text-anchor: middle;
}

.rainbow-widget {
  min-height: 150px;
  min-width: 150px;
}
</style>
