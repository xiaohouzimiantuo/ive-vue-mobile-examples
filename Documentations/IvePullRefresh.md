
# IvePullRefresh组件
## 介绍：该组件集成了局部下拉刷新和触底加载的功能
### 配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
refreshable | 是否可以下拉刷新 | Boolean | true | 默认启用下拉刷新的开关
pullDistance | 触发刷新的距离 | Number | 50 | 
pullMaxDistance | 下拉刷新可下拉的最大距离 | Number | 120 | 到达这个值的时候下拉的效果将受到阻力
pullingText | 下拉刷新的未到达距离的提示 | String | '下拉即可刷新' | 
loosingText | 下拉刷新到达释放距离的提示 | String | '释放即可刷新' | 
pullLoadingText | 下拉刷新加载中的提示 | String | '加载中...' | 
pullArrowIconShow | 是否显示下拉刷新的箭头 | Boolean | true | 
pullArrowIcon | 自定义下拉刷新的箭头图标 | String | '' | 图片的链接
pullLoadingIconShow | 是否显示下拉刷新的时候的loading 图标 | Boolean | true | 
pullLoadingIcon | 自定义下拉刷新的loading图标 | String | '' |  图片的链接
loadmoreable | 是否可以触底加载 | Boolean | false |  默认不启用触底加载
downText | 触底加载的加载前的文案 | String | '上拉显示更多' | 
downLoadingText | 触底加载的加载中的文案 | String | '正在加载...' | 
nomoreText | 触底加载的没有更多了的文案 | String | '没有更多数据了' | 
downLoadingIconShow | 是否显示触底加载的loading Icon | Boolean | true | 
downLoadingIcon | 触底加载的loading Icon | String | '' | 图片的链接

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
      refresh
    </td>
    <td>
      下拉刷新事件
    </td>
    <td>
      携带了一个next回调函数，在刷新内容成功后调用next()可以关闭下拉的加载状态，<span style="color: orange;">注意：当下拉刷新和触底加载同时出现的时候，只需将页面数据恢复到初始状态后直接调用next，组件会自动调用loadmore初始页</span>
    </td>
  </tr>
  <tr>
    <td>
      loadmore
    </td>
    <td>
      触底加载事件
    </td>
    <td>
      携带了一个next回调函数，在加载内容成功后调用next()可以关闭加载状态，其中调用next(true)的情况下表示告诉组件，没有更多内容了，next()调用的时候则可以继续加载。<span style="color: orange;">注意：页面初始化的时候，如果内容没有填充满，则触发不了滚动事件，所以在没填充满的情况下，组件会再次调用loadmore回调内容，直到内容填满或者next(true)为止</span>
    </td>
  </tr>
 
</tbody>
</table>


#### 具体使用方法请看examples中的PullRefresh、PullAndDown、LoadMore三个vue文件
<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/PullRefresh.vue">查看下拉刷新示例</a>

<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/LoadMore.vue">查看触底加载示例</a>

<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/PullAndDown.vue">查看下拉刷新和触底加载同时存在的示例</a>





