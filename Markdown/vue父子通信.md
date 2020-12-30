## 父组件调用一个子组件，父组件的属性如何传递给子组件使用，子组件的数据如何传递给父组件？

总结：父组件通过`prop`给子组件下发数据(父组件data的数据用`v-bind`绑定相应的data，然后在子组件中`prop:{  属性名  }`)，子组件通过`$emit`触发事件给父组件发送消息（父组件事先定于好了事件的名称），即`prop`向下传递，事件向上传递。

```JavaScript
<template>
  <div class="parent">
    我是父组件
    <!--父组件监听子组件触发的say方法，调用自己的parentSay方法-->
    <!--通过:msg将父组件的数据传递给子组件-->
    <children :userMsg="msg" @say="parentSay"></children>
  </div>
</template>
user
<script>

import Children from './children.vue'

export default {
  data () {
    return {
      msg: 'hello, children'
    }
  },

  methods: {
      // 参数就是子组件传递出来的数据
      parentSay(msg){
          console.log(msg) // hello, parent
      }
  },

  // 引入子组件
  components:{
      children: Children
  }
}
</script>
```

```JavaScript
<template>
  <div class="hello">
    <div class="children" @click="say">
      我是子组件
      <div>
        父组件对我说：{{msg}}
      </div>
    </div>

  </div>
</template>

<script>

  export default {
      //父组件通过props属性传递进来的数据
      props: {
          userMsg: {
              type: String,
              default: () => {
                  return ''
              }
          }
      },
      data () {
        return {
            childrenSay: 'hello, parent'
        }
      },

      methods: {
          // 子组件通过emit方法触发父组件中定义好的函数，从而将子组件中的数据传递给父组件
          say(){
              this.$emit('say' , this.childrenSay);
          }
      }
  }
</script>
```
