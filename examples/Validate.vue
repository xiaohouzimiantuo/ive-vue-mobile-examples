<template>
  这是validate的示范页面：
  <view class="mobile_mask animated">
      <view class="input_item">
        <input type="text" v-model="formData.account.value" placeholder="输入手机号" />
      </view>
      <view class="input_item">
        <input type="text" v-model="formData.pwd.value" placeholder="输入密码" />
      </view>
      <button
        class="sub_btn"
        @click="submit"
      >
        提交
      </button>
    </view>
</template>

<script lang="ts">
import {
  defineComponent,
  onBeforeMount,
  onMounted,
  reactive
} from "vue";

import { validate } from "ive-vue-mobile";
export default defineComponent({
  setup() {
    const formData = reactive({
      account: {
					value: "",
					rules: [
						{
							required: true,
							message: '请填写手机号码'
						},
						{
							pattern: /^1(3|4|5|7|8|9|6)\d{9}$/i,
							message: '请输入正确的手机号码'
						},
					],
				},
				pwd: {
					value: '',
					rules: [
						{
							required: true,
							message: '请填写密码'
						},
						{
							pattern: '/^[\w\d]+$/i',
							message: '请输入正确的验证码'
						},
            {
              validate(value) {
                return value !== '123456';
              },
              message: '传入的值是123456'
            }
					]
				}
    });
    onBeforeMount(() => {});
    onMounted(() => {
    });
    return {
      formData,
      submit() {
        validate(formData).then(data => {
          // 返回的data只有提交表单所需要的数据
          console.log(data);
        }).catch(errMsg => {
          alert(errMsg);
        });
      }
    };
  },

});
</script>

<style lang="scss" scoped>

</style>

