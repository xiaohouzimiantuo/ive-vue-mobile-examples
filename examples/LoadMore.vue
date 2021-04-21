<template>
<!-- 触底加载 -->
  <div>
    <ive-pull-refresh :refreshable="false" :loadmoreable="true" @loadmore="loadmore" class="scroll_wrapper" :downLoadingText="'加载中'">
      <p style="padding: 10px;" v-for="i in list" :key="i">ceshi{{i}}</p>
    </ive-pull-refresh>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from "vue";
import { IvePullRefresh } from "ive-vue-mobile";
export default defineComponent({
  props: {},
  setup(props) {
    const listarr: number[] = [];
    const list = ref(listarr);
    const requestTimer = ref(0);
    const state = reactive({
      page: 1,
    });
    // 模拟数据请求
    const getList = (cb?: Function) => {
      if (requestTimer.value) return;
      requestTimer.value = setTimeout(() => {
        requestTimer.value && clearTimeout(requestTimer.value);
        requestTimer.value = 0;
        const moreData: number[] = [];
        const start = list.value[list.value.length - 1] || 0;
        for (let i = 0; i < 4; i++) {
          moreData.push(start + 1 + i);
        }
        // 请求成功返回数据
        cb && cb(moreData);
      }, 1000);
    };

    return {
      list,
      loadmore(next: Function) {
        getList((data: number[]) => {
          state.page++;
          list.value = [...list.value, ...data];
          if (state.page > 10) {
            // 模拟没有更多了
            next(true);
          } else {
            // 还可以加载下一页
            next();
          }
        });
      },
    };
  },

  components: {
    IvePullRefresh,
  },
});
</script>

<style lang="scss" scoped>
.scroll_wrapper {
  height: 100vh;
}
</style>
