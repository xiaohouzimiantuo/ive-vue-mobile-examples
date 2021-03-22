
# IveModal组件
## 对话框组件配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
visible | 是否显示 | Boolean | false | 
title | 对话框标题 | String | '' | 
footer | 对话框底部按钮 | Array | [{class: "", type: 'pri',text: "确定"}] | 不显示传入空数组即可

## event
时间名 | 说明 | 回调参数
clickMask | 点击遮罩层的回调函数 | 无参数

## footer
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
type | 当前底部按钮的类型 | String | '' |  详见###type
class | 当前底部按钮的class类名 | String | '' | 通过类名修改样式
text | 当前底部按钮的文案 | String | '' | 默认为"确定"
onClick | 当前底部按钮的点击回调 | Function | undefined | 在IveModal.show方法中的回调中含有两个参数

# IveModal.show方法 （返回当前实例）
---
创建IveModal对话框实例
---
## 对话框的方法传入配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
title | 对话框标题 | String | '' | 
content | 对话框内容 | String | '' | 可以使用vue的template,默认值需要配合data一起使用 
data | 对话框内容 | Object | '' | 配合content使用，对应template中的数据
footer | 对话框底部按钮 | Array | [{class: "", type: 'pri',text: "确定"}] | 不显示传入空数组即可
maskClose | 点击遮罩层是否关闭弹窗 | Boolean | false 

### footer
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
type | 当前底部按钮的类型 | String | '' |  详见###type
class | 当前底部按钮的class类名 | String | '' | 通过类名修改样式
text | 当前底部按钮的文案 | String | '' | 默认为"确定"
onClick | 当前底部按钮的点击回调 | Function | undefined | 回调携带两个参数，第一个参数为当前modal实例的详细信息及当前按钮的详细信息，第二个参数为关闭modal实例的回调方法，用于关闭对话框

### footer数组中type取值说明
取值 | 字体颜色 | 类型 | 是否是默认值 |备注
----|------|-----|------|-------
def | 不设置字体颜色 | String | 否 | default的前三个字母
pri | 红色 | String | 是| primary的前三个字母
err | 蓝色 | String | 否 | primary的前三个字母

### modalFormTemplate提供好的默认输入框模板
label | value 
----|------
此时data中应该出现label值 | 此时data中应该出现value值

### cteateFormTemplate创建默认输入框模板

参数 | 说明 | 类型 
----|------|-----
label | data中对应label的值 | String 
value | data中对应value的值 | String 


