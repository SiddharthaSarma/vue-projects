<script>
import { h } from 'vue';
export const TabContainer = {
  props: {
    activeTabId: {
      type: String,
      required: true
    }
  },
  render() {
    const $slots = this.$slots.default();
    const tabs = $slots.filter((slot) => slot.type === TabTitle);
    const content = $slots.find(slot => slot.type === TabContent && slot.props['tab-id'] == this.activeTabId);
    return [
      h('div', { class: 'tabs' }, tabs),
      h('div', content)
    ]
  },
};
const TabItem = (content) => ({
  ...content,
  props: {
    tabId: {
      type: String,
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
