<template>
  <dashboard-card :title="$t('pageOverview.networkAnamoly')"></dashboard-card>
</template>

<script>
import DashboardCard from './DashboardCard';

export default {
  name: 'NetworkAnamoly',
  components: {
    DashboardCard,
  },
};
</script>
