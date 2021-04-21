<template>
  这是loading的示范页面：
  <ive-loading 
    text="" 
    :visible="visible" 
    icon="https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=4111588356,669513736&fm=26&gp=0.jpg"
    :font="{color: '#000', fontSize: '18px'}"
    />
    <button @click="clickLoading">点击加载</button>
</template>

<script lang="ts">
import {
  defineComponent,
  onBeforeMount,
  onMounted,
  ref
} from "vue";

import { IveLoading } from "@/components";
// import { IveLoading } from "ive-vue-mobile";
export default defineComponent({
  setup() {
    const visible = ref(true);
    onBeforeMount(() => {
      
    });
    onMounted(() => {
      setTimeout(() => {
        visible.value = false;
        const loadingInstance = IveLoading.show({text:'加载中'});
        setTimeout(() => {
          // 关闭当前实例
          loadingInstance.close();
        }, 2000);
        setTimeout(() => {
          IveLoading.setOptions({
            text: '加载中...',
            icon: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fpic.pc6.com%2Fup%2F2015-5%2F201551010315.png&refer=http%3A%2F%2Fpic.pc6.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1618645082&t=f103b283c955dff673d7d58becbf09e5',
            spin: true,
            font: {
              color: '#385f66',
              fontSize: '24px'
            }
          });
          IveLoading.show('再次加载');
          setTimeout(() => {
            // 清除所有
            IveLoading.clear();
          }, 2000);
        }, 3000);
      }, 2000);

    });
    return {
      visible,
      clickLoading() {
        const loadingInstance = IveLoading.show('加载中');
        setTimeout(() => {
          // 关闭当前实例
          loadingInstance.close();
        }, 2000);
      }
    };
  },
  components: {
    IveLoading
  }
});
</script>

<style lang="scss" scoped>

</style>

