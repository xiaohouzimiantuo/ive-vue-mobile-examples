
# IveDrager组件
## 拖拽组件配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
isFixed | 是否使用固定定位 | Boolean | true | 如果不是固定定位，则使用的是绝对定位，外层需要用一个容器包裹 
k | 组件的唯一key值 | String | '' | 用于记录用户上一次拖拽的位置，下次打开位置依旧在上一次的位置，一个页面上有多个拖拽组件的时候必须设置一个唯一的key值 
aside | 拖拽停止后靠边 | String | '' | 空值的时候不靠边，值为v(vertical的首字母)时，靠上或者靠下，值为h(horizontal的首字母)时，靠左或者靠右
initX | 水平的初始位置 | Number | 0 | 
initY | 垂直的初始位置 | Number | 0 | 


<a target="_blank" href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples/blob/master/examples/Drager.vue">查看示例</a>