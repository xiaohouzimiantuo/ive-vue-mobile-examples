<template>
  这是validate的示范页面：
  <view class="mobile_mask animated">
    <br>
      <view class="input_item">
        <input type="text" v-model="formData.account.value" placeholder="输入手机号" />
      </view>
      <br>
      <view class="input_item">
        <input type="text" v-model="formData.pwd.value" placeholder="输入验证码" />
        <ive-countdown 
          class="code_btn"
          :seconds="30"
          :validateData="countdownData"
          @action="sendCode"
        />
      </view>
      <br>
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
  computed,
  reactive
} from "vue";

import { validate, IveCountdown } from "ive-vue-mobile";
export default defineComponent({
  components: {
    IveCountdown
  },
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
    const countdownData = computed(() => {
      const account = formData.account;
      return { account };
    });
    onBeforeMount(() => {});
    onMounted(() => {
    });
    return {
      formData,
      countdownData,
      sendCode(res, next) {
        if(res.status == 'ok') {
          console.log(res.data);//countdownData的值，用于发送请求
          if(Math.random() < 0.3) {
            //模拟失败场景
            next();
            window.alert('发送失败');
          }else {
            // 模拟成功场景
            setTimeout(() => {
              next(true);
            }, 500);
          }
        }else {
          // 发送请求前的条件校验失败
          next();
          window.alert(res.errMsg);
        }
      },
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

