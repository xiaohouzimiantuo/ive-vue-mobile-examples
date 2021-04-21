<template>
<!-- 下拉刷新&&触底加载 -->
  <div>
    <ive-pull-refresh :loadmoreable="true" @loadmore="loadmore" @refresh="refresh" class="scroll_wrapper">
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
      page: 1, //页数，请求的时候用，在本例子中没有使用
      pageSize: 10,
    });
    // 模拟接口获取数据的过程
    const getList = (cb?: Function) => {
      if (requestTimer.value) return; //模拟正在加载中
      // 模拟请求数据
      requestTimer.value = setTimeout(() => {
        // 模拟请求成功
        requestTimer.value && clearTimeout(requestTimer.value);
        requestTimer.value = 0;
        // 模拟接口返回的数据
        const moreData: number[] = [];
        const start = list.value[list.value.length - 1] || 0;
        // 随机生成返回数据的长度
        const langth =
          Math.random() > 0.4 ? 10 : Math.floor(Math.random() * 10) + 1;
        for (let i = 0; i < langth; i++) {
          moreData.push(start + 1 + i);
        }
        // 将获取到的数据传递给回调函数
        cb && cb(moreData);
      }, 1000);
    };
    const loadmore = (next: Function) => {
      // 获取列表
      getList((data: number[]) => {
        state.page++;
        list.value = [...list.value, ...data];
        // 当返回的数据内容小于pageSize的时候说明没有更多了
        if (data.length < state.pageSize) {
          // 传入true表示没有更多了，不再触发触底加载
          next(true);
        } else {
          // 不传参数状态变为：上拉显示更多状态， 为下一次触底加载做准备
          next();
        }
      });
    };

    return {
      list,
      refresh(next: Function) {
        // 初始化数据
        list.value = [];
        state.page = 1;
        /**
         * 当loadmoreable为false（默认为false）的时候，需要写更新页面数据的逻辑,更新成功后调用next
         * setTimeout(() => {list.value = [1,2,3,4,5]; next()}, 1000);
         */
        // loadmoreable 为true， 直接调用next，next函数会调用loadmore去初始化页面，直到更新完成，回到下拉前的状态
        next();
      },
      loadmore,
    };
  },

  components: {
    IvePullRefresh,
  },
});
</script>

<style lang="scss" scoped>
.scroll_wrapper {
  height: 500px;
  margin-top: 40px;
  background: #f5f5f5;
}
</style>
