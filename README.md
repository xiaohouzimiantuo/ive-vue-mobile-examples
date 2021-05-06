# ive-vue-mobile

## 介绍 
ive-vue-mobile 基于vue3封装了一些简单手机端常用的组件和方法，库的总大小为400kb+，推荐使用按需引入的方法，方便Tree-Sharking。更多组件还在完善中，敬请期待。
## 目录
### 组件

<table style="border-collapse: collapse;">
<thead>
  <tr>
    <th>组件名称</th>
    <th>说明</th>
    <th>详细用法</th>
    <th>文档</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>
      IveModal
    </td>
    <td>
      弹窗组件
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Modal.vue">查看</a>
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/IveModal.md">查看</a>
    </td>
  </tr>
  <tr>
    <td>
      IveDrager
    </td>
    <td>
      拖拽组件
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Drager.vue">查看</a>
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/IveDrager.md">查看</a>
    </td>
  </tr>
  <tr>
    <td>
      IveLoading
    </td>
    <td>
      加载组件
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Loading.vue">查看</a>
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/IveLoading.md">查看</a>
    </td>
  </tr>
  <tr>
    <td>
      IveCountdown
    </td>
    <td>
      倒计时组件
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Countdown.vue">查看</a>
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/IveCountdown.md">查看</a>
    </td>
  </tr>
  <tr>
    <td>
      IvePullRefresh
    </td>
    <td>
      下拉刷新&&触底加载组件
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/PullRefresh.vue">查看下拉刷新示例</a> <br>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/LoadMore.vue">查看触底加载示例</a> <br>
  <a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/PullAndDown.vue">查看下拉刷新和触底加载同时存在的示例</a>
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/IvePullRefresh.md">查看</a>
    </td>
  </tr>
</tbody>
</table>

### 方法
<table style="border-collapse: collapse;">
<thead>
  <tr>
    <th>方法名称</th>
    <th>说明</th>
    <th>详细用法</th>
    <th>文档</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>
      copy
    </td>
    <td>
      复制方法
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Copy.vue">查看</a>
    </td>
    <td>
      <a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/methods.md">查看</a>
    </td>
  </tr>
  <tr>
    <td>
      validate
    </td>
    <td>
      表单校验方法
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Validate.vue">查看</a> 
    </td>
    <td>
      <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/Documentations/methods.md">查看</a>
    </td>
  </tr>
 
</tbody>
</table>

## 安装
```
yarn install ive-vue-mobile --save
```

### use in html 简单的介绍，以IveModal组件为例
```
<script src="vue3_path/vue.runtime.global.js"></script>
<script src="your_path/iveVueMobile.umd.js"></script>

<script>
  iveVueMobile.IveModal.show({
    title: "自定义模板",
    content: '{{label}}<input v-modal="name">',
    data: { name: "我和content模板中的值关联", label: 'exaxple'},
    footer: [
      {
        type: 'delete',
        text: '取消',
        onClick: (data, close) => {
          console.log(data);
          alert("你取消了");
          close();
        },
      },
      {
        type: 'primary',
        text: '确定',
        onClick: (data, close) => {
          console.log(data);
          if (data.name.length > 18) {
            close();
          } else {
            alert("name的长度小于18");
          }
        },
      },
    ]
  });
</script>

```
### use in es2015 
#### 全局注册
```
import { createApp } from 'vue';
import IveVueMobile from 'ive-vue-mobile';

const app = createApp(App);
app.use(IveVueMobile);
```
#### On-demand 按需引入

```
import { IveModal } from 'ive-vue-mobile';
IveModal.show({
  title: "modalFormTemplate默认模板",
  content: IveModal.modalFormTemplate,
  data: { name: "name", label: 'modalFormTemplate的label'},
  footer: [
    {
      onClick: (data, close) => {
        console.log(data);
        if (data.name.length > 10) {
          close();
        } else {
          alert("name的长度小于10");
        }
      },
    },
  ]
});
```

## More examples

```
For more examples, please visit 
```
<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples">https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples</a>
