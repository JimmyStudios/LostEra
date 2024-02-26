<template>
  <a-layout has-sider>
    
    <a-layout :style="{ marginRight: '200px' }">
      <a-layout-header :style="{ background: '#fff', padding: 0 }" />
      <a-layout-content :style="{ margin: '24px 16px 0', overflow: 'initial' }">
        <div :style="{ padding: '24px', background: '#fff', textAlign: 'center' }">
            <CategoriesGrid />
        </div>
      </a-layout-content>
      <a-layout-footer :style="{ textAlign: 'center' }">
          FOOTER
      </a-layout-footer>
    </a-layout>

    <a-layout-sider
      :style="{ overflow: 'auto', height: '100vh', position: 'fixed', right: 0, top: 0, bottom: 0 }"
    >
      <p style="color: #fff;">BASKET</p>      
    </a-layout-sider>

  </a-layout>
</template>
<script lang="ts" setup>
import { ref } from 'vue';
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
  BarChartOutlined,
  CloudOutlined,
  AppstoreOutlined,
  TeamOutlined,
  ShopOutlined,
} from '@ant-design/icons-vue';
const selectedKeys = ref<string[]>(['4']);
</script>
<style scoped>
#components-layout-demo-fixed-sider .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
}
.site-layout .site-layout-background {
  background: #fff;
}

[data-theme='dark'] .site-layout .site-layout-background {
  background: #141414;
}
</style>
