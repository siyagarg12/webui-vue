<template>
  <dashboard-card :title="$t('pageOverview.eventLogs')"></dashboard-card>
</template>

<script>
import DashboardCard from './DashboardCard';

export default {
  name: 'EventLogs',
  components: {
    DashboardCard,
  },
};
</script>
