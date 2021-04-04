<template>
  这是copy的示范页面：
  <br>
  <button @click="copyText">点击复制局部</button>
  <br>
  <button @click="copyText1">点击复制global</button>
</template>

<script lang="ts">
import {
  defineComponent,
  onBeforeMount,
  onMounted,
  getCurrentInstance
} from "vue";

import { copy } from "ive-vue-mobile";
export default defineComponent({
  setup() {
    const instance:any = getCurrentInstance();
    onBeforeMount(() => {});
    onMounted(() => {
    });
    return {
      copyText(){
        copy('这是copy的示范页面').then(() => {
          alert('success');
        });
      },
      copyText1() {
        instance.ctx._copy('copyText1').then(() => {
          alert('success');
        });
      }
    };
  },

});
</script>

<style lang="scss" scoped>

</style>

