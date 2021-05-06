
# IveCountdown组件
## 倒计时组件配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
validateData | 发送验证码前需要校验的数据 | Object | {} | 校验格式和validate方法的一样。详见validate方法（点击附1链接查看）
disableStyle | 禁用按钮时候的样式 | Object | {}  | 
disableClass | 禁用按钮时候的样式类名 | String | 59  | 禁用的时候默认会有一个countdown_disable的类名
name | 倒计时前按钮名称 | String | 发送验证码  | 
seconds | 倒计时时长（单位s） | Number | 59  | 

### 事件
<table style="border-collapse: collapse;">
<thead>
  <tr>
    <th>事件名</th>
    <th>说明</th>
    <th>备注</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>
      action
    </td>
    <td>
      点击按钮后触发的事件
    </td>
    <td>
      第一个参数为校验结果，成功状态：status为ok， 失败状态为fail，成功的时候返回校验数据的内容（data），失败返回校验提示内容(errMsg)，<br>
      <span>第二个参数为一个回调函数next，表示是否继续下一步，next(true)开始倒计时，倒计时结束后解除禁用状态，next()直接解除禁用状态</span>
    </td>
  </tr>
 
</tbody>
</table>

<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Countdown.vue">查看示例</a>


#### 附1
<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Validate.vue">validate使用方法</a>