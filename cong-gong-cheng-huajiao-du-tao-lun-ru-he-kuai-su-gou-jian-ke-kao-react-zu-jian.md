# 从工程化角度讨论如何快速构建可靠React组件

为了提高开发效率，去年10月份也开始有意识地私下封装一些组件，并且于今年年初在项目组里发起了百日效率提升计划，其中就包含组件化开发这一块。

本文并不是要谈如何去写一个 React 组件，这一块已经有不少精彩的文章。例如像这篇[《重新设计 React 组件库》](http://mp.weixin.qq.com/s/8dZV0oKfBKp-jERguNxflw)，里面涉及一个组件设计的各方面，如粒度控制、接口设计、数据处理等等（不排除后续也写一篇介绍组件设计理念哈）。

本文关键词是三个，工程化、快速和可靠。我们是希望利用工程化手段去保障快速地开发可靠的组件，工程化是手段和工具，快速和可靠，是我们希望达到的目标。

前端工程化不外乎两点，规范和自动化。

读文先看此图，能先有个大体概念：  


![](/assets/5abbdc42-02d5-11e7-9dbf-4b603fdee1ad.png)



[http://www.alloyteam.com/2017/03/from-an-engineering-point-of-view-discusses-how-to-construct-reliable-components-react/](http://www.alloyteam.com/2017/03/from-an-engineering-point-of-view-discusses-how-to-construct-reliable-components-react/)

