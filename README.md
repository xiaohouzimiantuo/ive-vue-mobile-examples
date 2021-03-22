# ive-vue-mobile

## Project setup
```
yarn install ive-vue --save
```

### use in html
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
```

```
#### Global introduction
```
import { createApp } from 'vue';
import IveVueMobile from 'ive-vue-mobile';

const app = createApp(App);
app.use(IveVueMobile);
```
#### On-demand introduction
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
For more examples, please visit <a href="https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples">https://github.com/xiaohouzimiantuo/ive-vue-mobile-examples</a>
```
