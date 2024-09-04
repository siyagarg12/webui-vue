<template>
  <dashboard-card :title="$t('pageOverview.ransomware')"></dashboard-card>
</template>

<script>
import DashboardCard from './DashboardCard';

export default {
  name: 'Ransomware',
  components: {
    DashboardCard,
  },
};
</script>
