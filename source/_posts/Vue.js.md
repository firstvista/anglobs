---
title: Vue.js
tages: 学习
keywords: 学习
cover: /img/comment_bg.png
abbrlink: 3212ea86
---
# Vue.js

一套用于构建用户界面的渐进式JavaScript框架

​			JavaScript框架

​			简化Dom操作

​			响应式数据驱动



官方网址：[Vue.js (vuejs.org)](https://cn.vuejs.org/)

awesome vue

图表：charts



特点：

​		■	1、采用组件化（HTML+CSS+JS）模式，提高代码复用率、且让代码更好维护

​		■	2、声明式编码，让编码人员无需直接操作DOM，提高开发效率

​		■	3、使用虚拟DOM+优秀Diff算法，尽量复用DOM节点



命令式编码（一步一步走）		=对立=>		声明式编码



## 初识Vue

### 	axios框架全称	（[ajax](https://so.csdn.net/so/search?q=ajax&spm=1001.2101.3001.7020) – I/O – system）：



这不是一种新技术，本质上还是对原生XMLHttpRequest的封装，可用于浏览器和nodejs的HTTP客户端，只不过它是基于Promise的，符合最新的ES规范。具备以下特点：

在浏览器中创建XMLHttpRequest请求
在node.js中发送http请求
支持Promise API
拦截请求和响应
转换请求和响应数据
取消要求
自动转换JSON数据
客户端支持防止CSRF/XSRF(跨域请求伪造)





删除整行：ctrl+shift+k

## 常用标签：

### el：（element）

​	■	el用于指定当前Vue实例为那个容器服务，值通常为css选择器字符串

```
id="root"

el:'#root'
```



```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>初识Vue</title>
    <!--引入vue-->
    <script type="text/javascript" src="../js/vue.js"></script>
</head>
<body>
    <!--
        1、想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象
        2、root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法
        3、root容器中里的代码被称为【Vue模板】
        4、Vue实例和容器是一一对应的
        5、真实开发中只有一个Vue实例，并且会配合着组件一起使用
        6、{{xxx}}中的xxx要写js表达式，且xxx可以自动读取到data中的所有属性
        7、一旦data中的数据发生了改变，那么页面中用到该数据的地方也会自动更新

        注意区分js代码（语句）和js表达式
            1、表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方
                (1).a
                (2).a+b
                (3).demo(1)
                (4).x == y ? 'a' : 'b'

           2、js代码（语句）
                (1).if(){}
                (2).for(){}

    -->
    <!--准备好一个容器-->
    <div class="root">
        <h1>{{name}},{{address.toUpperCase()}}</h1>
    </div>

    <script type="text/javascript">
        Vue.config.productionTip = false  //阻止 vue 在启动时生成生产提示。

        //创建Vue实例
        new Vue({
            el:'.root' , //el用于指定当前Vue实例为那个容器服务，值通常为css选择器字符串
            data:{  //data用于存储数据，供el所指定的容器去使用，值暂时写为一个对象
                name:'宋一鲤',
                address:'甘肃'
            }
        })

    </script>
</body>
</html>
```



## html 中包含了一些 JS 语法代码，语法分为两种，分别为： 

1. ### 插值语法（双大括号表达式） 

   1. 功能: 用于解析标签体内容 

   2. 语法: {{xxx}} ，xxxx 会作为 js 表达式解析

### 

```
<!--准备好一个容器-->
    <div id="root">
        <h1>插值语法</h1>
        <h3>你好，{{name}}</h3>
    </div>
</body>

    <script type="text/javascript">
        Vue.config.productionTip = false //阻止 vue 在启动时生产提示

        new Vue({
            el:'#root',
            data:{
                name:'jack'
            }
        })
    </script>
```



2. ### 指令语法（以 v-开头）

   1. 功能: 解析标签属性、解析标签体内容、绑定事件 

   2. 举例：v-bind:href = 'xxxx' ，xxxx 会作为 js 表达式被解析 



```
 <a v-bind:href="school.url">点我去{{school.name}}学习1</a>
        <a :href="school.url">点我去{{school.name}}学习2</a>
    </div>
</body>

    <script type="text/javascript">
        Vue.config.productionTip = false //阻止 vue 在启动时生产提示

        new Vue({
            el:'#root',
            data:{
                name:'jack',
                school:{
                    name: '尚硅谷',
                    url: 'http://atguigu.com'
                }
            }
        })
    </script>
```



单向数据绑定：

​		语法：v-bind:href ="xxx" 或简写为 :href

双向数据绑定：

​		语法：v-mode:value="xxx" 或简写为 v-model="xxx"



```js
<!--普通写法-->
单向数据绑定：<input type="text" v-bind:value="name"><br/>
双向数据绑定：<input type="text" v-model:value="name"><br/>

<!--简写-->
单向数据绑定：<input type="text" :value="name"><br/>
双向数据绑定：<input type="text" v-model="name">
```



### idea在setting中添加代码片段

![image-20220604211017446](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20220604211017446.png)



el与data的两种写法：

```
 //el的两种写法
       /* const  v = new Vue({
            // el: '#root',     //第一种写法
            data: {
                name: '宋一鲤'
            }
        })
        console.log(v)
        setTimeout(() =>{
            v.$mount('#root')   //第二种写法
        },1000);*/

        //data的两种写法
        new Vue({
            el: '#root',
            //data的第一种写法：对象式
            /*data: {
                name: '宋一鲤'
            }*/

            //data的第二种写法：函数式
            data:function (){
                return{
                    name:'宋一鲤'
                }
            }
        })

```

 

Object.defineProperties方法在控制台打印输出错误：

Uncaught TypeError: Property description must be an object: a     at Function.defineProperties (<anonymous>)

正确解决方案：

```js
let person = {

​      name:'张三',

​      sex:'男',

​      // age:18 

​    }



​    Object.defineProperties(person,{'age':{

​      value : 18,

​    }

​    })

​    console.log(person)
```



数据代理原理图（06_数据代理——3.Vue中的数据代理）：

![image-20220615100952611](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20220615100952611.png)



console.log(event.target)：打印目标文件中的元素



```
v-on:xxx=@xxx
```

### 设置滚动事件：

```
overflow: auto;
```

@scroll="demo"：设置滚动条的滚动事件

@wheel="demo"：设置鼠标滑轮滚动事件







vm为Vue实例对象：

```
const vm = new Vue({
        el:'#root',
        data:{
        name:'尚硅谷',
        },
        methods:{
          showInfo(event){
            // console.log(event.target.innerText);
            console.log(this==vm);
            //alert('同学你好')
             } 
        }
    })
```







### Vue中事件的基本使用：

​      1.使用v-on:xxx或@xxx绑定事件。其中xxx是事件名；

​      2.事件的回调需要配置在methods对象中，最终会在xm上；

​      3.methos中配置的函数，不要用箭头函数！否则this就不是vm了；

​      4.methods中配置的函数，都是被Vue所管理的函数，this是指向vm或组件实例对象；

​      5.@click="demo"和@click="demo($event)"效果一致，但后者可以传参；





键盘事件：@keydown和@keyup。



###  1.Vue中常用的按键别名：

​        回车   =>  enter

​        删除   =>  deelete（捕获“删除”和“退格”键）

​        退出   =>  esc

​        空格   =>  space

​        换行   =>  tab	（特殊，必须配合keydown使用）

​        上    =>  up

​        下    =>  down

​        左    =>  left

​        右    =>  right



 2.Vue未提供别名的按钮，可以使用原始的key值去绑定，但要注意转为kebab-case（短横线命名）



​      3.系统修饰键（用法特殊）：ctrl、alt、shift、meta

​        (1).配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发

​        (2).配合keydown使用：正常触发事件



​      4.也可以使用keyCode去指定具体的按键（不推荐）



​      5.Vue.config.keyCode.自定义键名 = 键码，可以去定制案件别名



Visual Studio Code同时选中多行输入，Alt + Shift + 鼠标左键选取多行

IntelliJ IDEA同时选中多行输入，Alt+左键选中多行



split()：拆分[字符串。通过指定分隔符对字符串进行切片，并返回分割后的字符串列表（list）



###  计算属性：

​      1.定义：要用的属性不存在，要通过已有的属性计算得来

​      2.原理：底层借助了Object.defineproperty方法提供的getter和setter

​      3.get函数什么时候执行？

​        (1).初次读取时会执行一次

​        (2).当依赖的数据发生改变时会再次调用

​      4.优势：与methods实现相比，内部缓存机制（复用），效率更高，调试方便。

​      5.备注：

​        1.计算属性最终会出现在vm上，直接读取使用即可。

​        2.如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生变化



shift+tab：减少缩进



记住箭头函数的特点：本身不存在this，但是可以通过调用上下域中的this供自己使用



## 面试题：react、vue中的key有什么作用？（key内部原理）



​      1.虚拟DOM中key的作用：

​        key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】，

​        随后Vue就行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下：



​      2.对比规则：

​        (1).旧虚拟DOM中找到了与新虚拟DOM相同的key：

​          <1>.若虚拟DOM中的内容没变，直接使用之前真实的DOM!

​          <2>.若虚拟DOM中内容变了，则生成新的真实DOM，随后替换掉页面中之前的真实DOM



​        (2).旧虚拟DOM中未找到与新虚拟DOM相同的key

​            创建新的真实DOM，随后渲染到界面



​      3.用index作为key可能会引发的问题

​            1.若对数据进行：逆序添加、逆序添加等破坏顺序操作：

​              会对没有必要的真实DOM更新 ==>> 界面效果没问题，但效率低



​            2.如果结构中还包含输入类DOM：

​              会产生错误的DOM更新 ==>> 界面有问题



​      4.开发中如何选择key？：

​            1.最好选用每条数据的唯一标识为key，比如id、手机号、身份证号、学号等唯一值

​            2.如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示

​              使用index作为key是没有问题的



### 代码折叠：

​	

```
// #region
.......
// endregion
```







DevTools





 收集表单数据：

​      若：<input type="text"/>，则v-model收集的是value的值，用户输入的就是value值。

​      若：<input type="radio"/>，则v-model收集的是value的值，且要给标签配置value值。

​      若：<input type="checkbox"/>

​        1.没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​        2.配置input的value属性

​          (1).v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​          (2).v-model的初始值是数组，那么收集的就是value组成的数组

​      备注：v-model的三个修饰符：

​          lazy:失去焦点再收集数据

​          number：输入字符串转为有效的数字

​          trim：输入首尾空格过滤





## 我们学过的指令：

​      v-bind  : 单向绑定解析表达式，可简写为：xxx

​      v-model : 双向数据绑定

​      v-for  : 遍历数组/对象/字符串

​      v-on   : 绑定监听事件，可简写为@

​      v-if   : 条件渲染（动态控制节点是否存在）

​      v-else  : 条件渲染（动态控制节点是否存在）

​      v-show  : 条件渲染（动态控制节点是否展示）

v-text指令：

​      1.作用：向其所在的节点中渲染文本内容。

​      2.与插值语法的区别：v-text会替换掉节点中的内容，{{xx}}则不会



autofocus：自动获取焦点事件





## 生命周期（钩子）：



红色的框：生命周期；

 绿色：环节；

![生命周期](H:\mongod111\资料（含课件）\02_原理图\生命周期.png)                                        



### 生命周期类比：



张三的一生（张三的生命周期）：

​										将要出生

​						（重要）呱呱坠地	===>	检查生体各项指标。

​										学会说话

​										学会走路

​										··················

​										··················

​						（重要）将要永别	===>	交代后事

​										已经永别



vm的一生（vm的生命周期）：

​										将要创建	===>	调用beforeCreate函数

​										创建完毕	===>	调用created函数。

​										将要挂载	===>	调用beforeMount函数。

​						（重要）挂载完毕	===>	调用mount函数。====>【重要的钩子】



​			   1.mounted：发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】



​										将要更新	===>	调用beforeUpdate函数。

​										更新完毕	===>	调用update函数

​		（重要）将要销毁	===>	调用beforeDestroy函数。====>【重要的钩子】



​		   2.beforeDestroy：清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】 



​										销毁完毕	===>	调用destroyed函数。



# 组件



### 定义:    实现应用中**局部**功能**代码**和**资源**的**集合**



非单文件组件：

​				一个文件中包含有n个组件

单文件组件：

​				一个文件中只包含有一个组件



原型对象：通过prototype可以扩展js对象

实例的隐式原型对象永远指向自己缔造者的原型对象

![image-20220821211242224](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20220821211242224.png)





## Vue中使用组件的三大步骤：

​      一、定义组件（创建组件）

​      二、注册组件

​      三、使用组件（写组件标签）



###     一、如何定义一个组件？

​      使用Vue.extend(options)创建，其中options和new Vue(options)时传入的那个options几乎一样，但也有点区别：

​      区别如下：

​        1.el不要写，为什么？ —— 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务那个容器。

​        2.data必须写成函数，为什么？   ——  避免组件被复用时，数据存在引用关系。

​      备注：使用template可以配置组件结构。



###     二、如何注册组件？

​        1.局部注册：靠new Vue的时候传入components选项

​        2.全局注册：靠new.component('组件名'，组件)



###     三、编写组件标签：

​        <school></school>

# Vue脚手架（CLI）

**初始化脚手架** 

**3.1.1** 

**说明** 

\1. Vue 脚手架是 Vue 官方提供的标准化开发工具（开发平台）。 

\2. 最新的版本是 4.x。 

\3. 文档: https://cli.vuejs.org/zh/。 

**3.1.2** **具体步骤** 

备注： 

\1. 如出现下载缓慢请配置 npm 淘宝镜像：npm config set registry 

https://registry.npm.taobao.org



第一步（仅第一次执行）：全局安装@vue/cli。 

npm install -g @vue/cli 

第二步：**切换到你要创建项目的目录**，然后使用命令创建项目 

vue create xxxx 

第三步：启动项目 

npm run serve 



\2. Vue 脚手架隐藏了所有 webpack 相关的配置，若想查看具体的 webpakc 配置， 

请执行：vue inspect > output.js



后续笔记见：H:\vue_test\README



uuid生成id：全球唯一

nanoid：生成随机数较短

78节

闲了学一下nodejs写服务器





































































































