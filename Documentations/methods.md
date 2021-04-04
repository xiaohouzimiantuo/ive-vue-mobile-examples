# 复制方法 copy
## 调用方法实现复制文案的功能
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
text | 需要被复制的文案 | String | '' | 返回一个Promise对象


### 例子：
copy('这是需要复制的文案').then(() => {
  alert('success');
});



# 校验表单的方法
## 在表单提交之前校验值是否符合要求
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
需要校验的数据 | 每一项包含value和rules | Object | {} | 返回一个Promise对象

### 传入的数据对象例子
{
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
}

### rules说明：
参数 | 说明 | 类型 | 默认值 | 备注
----|------|-----|------|-------
message | 校验结果失败后的提示信息 | String | '' | 
required | 是否必填 | Boolean | false | 
pattern | 校验的正则表达式 | RegExp或者String | '' | 
validate | 校验的方法 | Function | () => {} | 方法返回true则校验成功。否则失败


### 返回的Promise说明
成功：参数返回需要提交的表单数据，没有rules的相关内容
失败：参数返回校验失败的提示信息，用于直接弹出错误提示