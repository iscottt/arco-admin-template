<template>
  <a-config-provider :locale="locale">
    <router-view />
    <global-setting />
  </a-config-provider>
</template>

<script lang="ts" setup>
import { computed } from 'vue';
import enUS from '@arco-design/web-vue/es/locale/lang/en-us';
import zhCN from '@arco-design/web-vue/es/locale/lang/zh-cn';
import GlobalSetting from '@/components/global-setting/index.vue';
import useLocale from '@/hooks/locale';
import { useTabBarStore } from '@/store';
const tabBarStore = useTabBarStore();
const { currentLocale } = useLocale();
console.log('tabBarStore.getTabList', tabBarStore.getTabList)
const locale = computed(() => {
  switch (currentLocale.value) {
    case 'zh-CN':
      return zhCN;
    case 'en-US':
      return enUS;
    default:
      return enUS;
  }
});
</script>
