---
layout: default
title: {{ site.name }}
---
# Web Components
前端组件化其实是个持续了很长时间的过程了，从最开始的jquery的插件开始。我们就在封装一些js，css，html来方便下次的复用了。基本各个公司都有自己的组件库，比如我在的点评就是npm的组件。现在组里随着一些项目往React上转，React的组件化工作也在不断的整理中。组件化的过程中出现了一些普遍的痛点。Web components解决了其中的一些棘手的问题，在这里介绍一下Web Components的一些现状。

## 问题
组件化的过程中主要遇到的一些问题：

 - 资源分来管理，重用不便
 - 缺乏封装
 - 缺乏移植性

首先，js，css和html基本是分开放置的，我们想要重用某块功能的时候，我们需要在我们的js里面想办法引入需要的js；然后得根据组件要求的DOM结构引入HTML；然后在我们的css里引入组件需要的css，这其实是个很痛苦的过程。二是缺乏封装，尤其体现在CSS上，CSS一直都是全局的，没有局部CSS的概念，虽然可以通过Css Modules来模拟，但是还是有一些限制的，下文也会进行比较。三是组件缺乏移植性，就比如迁到了react的环境。当然我们可以在webpack上做一些文章，让以前的组件支持在React项目中使用。可是React自有自己的一套状态管理的机制，很多组件我们还是要重写的，将来切换到新的环境，迁移是有很大代价的。Web Components能够解决上面的这些问题

## Web Components简介
Web Components它本身不是一个规范，他是由W3C提出的另外4个规范的合集。这四个规范是：

 - Shadow Dom(草案阶段)
 - Custom Elements(草案阶段)
 - HTML Template(html5)
 - HTML Imports(草案阶段)

如上，这四个规范除了template已经成为了HTML5的规范，其他3个还是处于草案阶段的，所以浏览器的支持情况比较差也是可以理解的了。接下来这四个规范一个个聊一聊。

## Shadow Dom
他的作用是：管理多DOM树的层级关系，更好的合成DOM。他的中心思想是封装一个完全独立于文档流的子DOM树。他完美的做到了css的封装。当然还有文档内容的封装。以及通过重定向事件做了事件层面的封装。当然封装是他提供的能力，作为使用者的我们其实很关心的是主文档与Shadow Dom的交互，这个在下面会提到。

### 创建Shadow Dom
使用的第一步是创建，Shadow Dom的创建是得基于
