<script>
import { h } from 'vue';
export const TabContainer = {
  props: {
    activeTabId: {
      required: true,
    },
  },
  render() {
    const $slots = this.$slots.default();
    const tabs = $slots
      .filter((slot) => slot.type === TabTitle)
      .map((tab) =>
        h(tab, {
          class: { tab: true, active: tab.props.tabId === this.activeTabId },
          onClick: () => {
            this.$emit('update:activeTabId', tab.props.tabId);
          },
        })
      );
    const content = $slots.find(
      (slot) =>
        slot.type === TabContent && slot.props['tab-id'] == this.activeTabId
    );
    return [
      h(() => h('div', { class: 'tabs' }, tabs)),
      h(() => h('div', content)),
    ];
  },
};
const TabItem = (content) => ({
  ...content,
  props: {
    tabId: {
      required: true,
    },
  },
  render() {
    return h('div', this.$slots.default());
  },
});
export const TabTitle = TabItem({ name: 'TabTitle' });
export const TabContent = TabItem({ name: 'TabContent' });
</script>
