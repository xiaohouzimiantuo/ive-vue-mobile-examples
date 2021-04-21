<template>
<!-- 下拉刷新 -->
  <div>
    <ive-pull-refresh @refresh="refresh" class="scroll_wrapper" loosing-text="释放刷新">
      <div style="height: 100px; background: orange;">刷新次数{{times}}</div>
    </ive-pull-refresh>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { IvePullRefresh } from "ive-vue-mobile";
export default defineComponent({
  props: {
    
  },
  setup(props) {
    const times = ref(0);
    return {
      times,
      refresh(end: Function) {
        // 更新逻辑
        setTimeout(() => {
          times.value++;
          end();
        }, 2000);
      }
    }
  },
  
  components: {
    IvePullRefresh
  },
});
</script>

<style lang="scss" scoped>
.scroll_wrapper{
  height: 100vh;
}
</style>
