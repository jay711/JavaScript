# 基本问题

***
## 好好学 package.json
### --save-dev 和 --save
```
–save-dev 是你开发时候依赖的东西，–save 是你发布之后还依赖的东西

我的js代码是ES6规范的，在当前浏览器中并未普及，因此我需要将js代码编成ES5。这时我就需要引入babel模块，
因为只有在编译时需要babel模块，在发布代码后就不需要了，因此在引入babel模块时我们用 ‘npm install babel-core –save-dev’

如果我用了 jQuery，由于发布之后还是依赖jQuery，所以是 ‘npm install jquery –save’
```

***
## 好好学 webpack.config.js
### 箭头函数
```
该配置文件出现了大量的箭头函数，我们需要了解他
let pow=x=>x*x;
console.log(pow);
console.log(pow(10));//100

ƒ pow(x) {
  return x * x;
}

//两个参数
let add=(x,y)=>x+y;
console.log(add(1,2));  //3

//无参数  这里在配置文件中运用的最多了
let a=()=>123;
console.log(a());    //123

//可变参数
let addMore=(x,y,...rest)=>{
  console.log(rest);            //[3,4]
  let i,sum=x+y;
  rest.forEach(function(item){
    sum+=item;
  });
  return sum;
};
console.log(addMore(1,2,3,4));  //10

//返回对象
let person=(str)=>({
  name: str
});
console.log(person("Harrdy"),toString.call(person));  //{name: "Harrdy"} "[object Function]"

箭头函数看上去是匿名函数的一种简写，但实际上，箭头函数和匿名函数有个明显的区别：箭头函数内部的this是词法作用域，由上下文确定
现在，箭头函数完全修复了this的指向，this总是指向词法作用域，也就是外层调用者

在配置文件中箭头函数一般作匿名函数的用处
```
* ***[跑马灯 sorce code js](./source%20code/pmd.js)***
* ***[跑马灯 sorce code html](./source%20code/pmd.html)***

***
## 好好学 npm
### npm 装包技巧
```
设置npm为淘宝镜像
npm config set registry https://registry.npm.taobao.org

设置npm为南邮镜像
npm config set registry https://mirrors.njupt.edu.cn/nexus/repository/npm/

查看镜像的配置结果
[harrdy@localhost ~]$ npm config get registry
https://registry.npm.taobao.org/

临时使用镜像来安装包
npm install some-package --registry=https://mirrors.njupt.edu.cn/nexus/repository/npm/

设为默认  修改 ~/.npmrc,如果没有则创建一个
registry=https://mirrors.njupt.edu.cn/nexus/repository/npm/

有时候设置镜像都下载不了，但是手动可以下载，则手动安装
npm install --save-dev /home/harrdy/Downloads/style-loader-0.13.2.tgz
```

***
## 好好学 Vue
### v-if 和 v-show
```
v-if 是动态添加，当值为 false 时，是完全移除该元素，即 dom 树中不存在该元素。
v-show 仅是隐藏 / 显示，值为 false 时，该元素依旧存在于 dom 树中。若其原有样式设置了 display: none 则会导致其无法正常显示。
```
