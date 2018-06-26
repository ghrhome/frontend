# Styled Components：让样式也成为组件

## 前言

为了应对越来越复杂的web应用，组件化应运而生，React、Vue等组件化框架使我们的程序更简单更加可维护。在一个组件内会将结构、样式和逻辑写在一起，虽然这违背了关注点分离的原则，但是这有利于组件间的隔离。为了顺应组件化的潮流，人们开始考虑使用JS上编写CSS，[styled components](https://github.com/styled-components/styled-components)就是其中一种解决方案。styled components是一个React第三方库，作用是可以将样式写成组件的形式，实现在JS上编写CSS。





## 分离逻辑组件和展示组件

使用styled components，可将组件分为逻辑组件和展示组件**，逻辑组件只关注逻辑相关的部分，展示组件只关注样式**。通过解耦成两种组件，可以使代码变得更加清晰可维护。  
当逻辑有变化，如后台拉取的数据的格式有所变化时，只需关注并修改逻辑组件上的代码，展示组件的代码不用动。而当UI需要变化时，只需改变展示组件上的代码，并保证展示组件暴露的props接口不变即可。逻辑组件和展示组件各司其职，修改代码时错误发生率也会有所减少。

## CSS Module vs Styled Components

CSS Module是另一种解决全局作用域的方案，还没了解CSS Module的朋友可以参考[CSS Modules 入门及 React 中实践](http://www.alloyteam.com/2017/03/getting-started-with-css-modules-and-react-in-practice/)和[CSS Modules 用法教程](http://www.ruanyifeng.com/blog/2016/06/css_modules.html)这两篇博文。  
CSS Module只需修改构建代码和使用模块依赖引入className的方式即可使用，且支持less和sass的语法，样式代码不用修改即可让使用CSS语法的旧项目零成本接入。而styled components是一种全新的样式组件化的编程方式，不支持less和sass语法。  
CSS Module还是JS和CSS分离的写法，而styled components实际上是在JS上写CSS。习惯JS、CSS和HTML都分离的人或许不习惯styled components的写法。

## 最后

styled components一种全新的控制样式的编程方式，它能解决CSS全局作用域的问题，而且移除了样式和组件间的映射关系。传统的web开发推崇HTML、CSS、Javascript都分离，styled components则有点“离经叛道”的味道——在JS上编写CSS，什么东西都在JS里写感觉是近几年前端开发的趋势，React就是一个活生生的例子。究竟这是不是一个好趋势，现在还不好判断，但是实践和时间总会给我们一个答案。

