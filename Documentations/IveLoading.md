
# IveLoading组件
## 加载组件配置参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
visible | 是否显示 | Boolean | false | 
text | 加载文案 | String | '' | 
icon | 加载图案 | String | '' | 
spin | 加载图案是否旋转 | Boolean | '' | 
font | 字体样式 | Object | {} | { color: '#385f66', fontSize: '24px' }



# IveLoading.show方法（返回当前实例）
---
创建IveLoading实例
---
## 加载方法传入参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
text | 加载文案 | String | '' | IveLoading.show可以只传入一个字符串，此时的options相当于text
icon | 加载图案 | String | '' | 
spin | 加载图案是否旋转 | Boolean | '' | 
font | 字体样式 | Object | {} | { color: '#385f66', fontSize: '24px' }

## 返回实例中有close方法
### 使用instance.close()来关闭当前loading


# IveLoading.setOptions 设置默认值
## 加载方法传入参数options
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
text | 加载文案 | String | '' | IveLoading.show可以只传入一个字符串，此时的options相当于text
icon | 加载图案 | String | '' | 
spin | 加载图案是否旋转 | Boolean | '' | 
font | 字体样式 | Object | {} | { color: '#385f66', fontSize: '24px' }


# IveLoading.clear 关闭所有loading
## 使用IveLoading.clear()来清除所有loading
