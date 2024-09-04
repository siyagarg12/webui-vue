<template>
  <b-container fluid="xl">
    <dashboard-quick-links class="mb-4 dashboard" />
    <page-section
      :section-title="$t('pageOverview.systemInformation')"
      class="mb-1"
    >
      <b-card-group deck>
        <overview-server class="dashboard-server" />
        <overview-firmware class="dashboard-firmware" />
        <overview-network class="dashboard-server" />
        <overview-power class="dashboard-firmware" />
      </b-card-group>
    </page-section>
    <page-section :section-title="$t('pageOverview.security')" class="mb-1">
      <b-card-group deck>
        <ransomware class="security" />
        <network-anamoly class="security" />
        <event-logs class="security" />
      </b-card-group>
    </page-section>
  </b-container>
</template>

<script>
import LoadingBarMixin from '@/components/Mixins/LoadingBarMixin';
import OverviewFirmware from '@/views/Overview/OverviewFirmware.vue';
import OverviewNetwork from '@/views/Overview/OverviewNetwork';
import OverviewPower from '@/views/Overview/OverviewPower';
import OverviewServer from '@/views/Overview/OverviewServer';
import PageSection from '@/components/Global/PageSection';
import DashboardQuickLinks from './DashboardQuickLinks.vue';
import Ransomware from './Ransomware.vue';
import NetworkAnamoly from './NetworkAnamoly.vue';
import EventLogs from './EventLogs.vue';
export default {
  name: 'Dashboard',
  components: {
    OverviewFirmware,
    OverviewNetwork,
    OverviewPower,
    OverviewServer,
    PageSection,
    DashboardQuickLinks,
    Ransomware,
    NetworkAnamoly,
    EventLogs,
  },
  mixins: [LoadingBarMixin],
  data() {
    return {
      showDumps: process.env.VUE_APP_ENV_NAME === 'ibm',
    };
  },
  created() {
    this.startLoader();
    const dumpsPromise = new Promise((resolve) => {
      this.$root.$on('overview-dumps-complete', () => resolve());
    });
    const eventsPromise = new Promise((resolve) => {
      this.$root.$on('overview-events-complete', () => resolve());
    });
    const firmwarePromise = new Promise((resolve) => {
      this.$root.$on('overview-firmware-complete', () => resolve());
    });
    const inventoryPromise = new Promise((resolve) => {
      this.$root.$on('overview-inventory-complete', () => resolve());
    });
    const networkPromise = new Promise((resolve) => {
      this.$root.$on('overview-network-complete', () => resolve());
    });
    const powerPromise = new Promise((resolve) => {
      this.$root.$on('overview-power-complete', () => resolve());
    });
    const quicklinksPromise = new Promise((resolve) => {
      this.$root.$on('overview-quicklinks-complete', () => resolve());
    });
    const serverPromise = new Promise((resolve) => {
      this.$root.$on('overview-server-complete', () => resolve());
    });

    const promises = [
      eventsPromise,
      firmwarePromise,
      inventoryPromise,
      networkPromise,
      powerPromise,
      quicklinksPromise,
      serverPromise,
    ];
    if (this.showDumps) promises.push(dumpsPromise);
    Promise.all(promises).finally(() => this.endLoader());
  },
};
</script>

<style lang="scss">
.container-xl {
  max-width: none;
}
.dashboard {
  min-height: 200px;
  background-color: orange !important;
}
.dashboard-server {
  background-color: yellow !important;
}
.dashboard-firmware {
  background-color: aqua !important;
}
.security {
  background-color: black !important;
  color: white !important;
  min-height: 300px;
}
</style>
