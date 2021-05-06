<template>
  <div>
    这是imodal的示范页面：
  <br />
  在footer的onClick事件中，从回调取当前v-modal绑定数据的值,
  <br />
  
  
  <ive-modal 
    :visible="visible"
    :title="'你取消了'"
    :footer="[{
      text: '确定',
      onClick: closeIveModal
    }]"
    @clickMask="clickMask"
  >
    代码是写出来给人看的，附带能在机器上运行
  </ive-modal>
  </div>
</template>

<script lang="ts">
import { defineComponent, onBeforeMount, onMounted, ref } from "vue";

import { IveModal } from "ive-vue-mobile";

export default defineComponent({
  setup() {
    const visible = ref(false);
    onBeforeMount(() => {

    });
    onMounted(() => {
      function showTem() {
        IveModal.show({
          title: "modalFormTemplate默认模板",
          content: IveModal.modalFormTemplate,
          data: { value: "name", label: "modalFormTemplate的label" },
          footer: [
            {
              type: "err",
              text: "取消",
              onClick: (data: unknown, close: Function) => {
                console.log(data);
                close();
                visible.value = true;
              },
            },
            {
              type: "pri",
              text: "确定",
              onClick: (d: any, close: Function) => {
                console.log(d);
                if (d.value.length > 18) {
                  close();
                  IveModal.show({
                    title: "modalFormTemplate默认模板",
                    content: IveModal.modalFormTemplate,
                    data: { value: "name", label: "modalFormTemplate的label" },
                  });
                } else {
                  alert("name的长度小于18");
                }
              },
            },
          ],
        });
      }
      IveModal.show({
        maskClose: true,
        title: "从回调取当前v-modal绑定数据的值",
        content: `<input v-model="test" class="test" />
        <p>{{test2}}</p>
        <input v-model="test1" class="test" />`,
        data: {
          test: "第一个input的数据",
          test1: "第二个input的数据",
          test2: "通过v-modal绑定input中的数据",
        },
        footer: [
          {
            onClick: (data: any, close: Function) => {
              console.log(data);
              close();
              showTem();
            },
          },
        ],
      });
    });
    return {
      visible,
      clickMask() {
        console.log('click mask')
      },
      closeIveModal() {
        visible.value = false;
      }
    };
  },
  components: {
    IveModal,
    
  },
});
</script>

<style lang="scss" scoped>
</style>

