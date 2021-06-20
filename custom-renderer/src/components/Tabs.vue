<template>
  <tab-container v-model:activeTabId="activeTabId">
    <tab-title :tabId="1">Tab 1</tab-title>
    <tab-title :tabId="2">Tab 2</tab-title>
    <tab-title :tabId="3">Tab 3</tab-title>
    <tab-title :tabId="4">Tab 4</tab-title>
    <tab-content tab-id="1">Tab content 1</tab-content>
    <tab-content tab-id="2">Tab content 2</tab-content>
    <tab-content tab-id="3">Tab content 3</tab-content>
    <tab-content tab-id="4">Tab content 4</tab-content>
  </tab-container>
</template>

<script>
import { TabContainer, TabTitle, TabContent } from './TabComponent.vue';
export default {
  name: 'tabs',
  components: {
    TabContainer,
    TabTitle,
    TabContent,
  },
  data() {
    return {
      activeTabId: 2,
    };
  },
};
</script>

<style scoped></style>
