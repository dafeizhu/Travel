# travel
>Vue2.5去哪儿网App开发学习项目
## 效果展示图
![](https://github.com/dafeizhu/Travel/blob/master/imgs/GIF.gif)

## 项目技术总览
* Vue：Vue、Vue-router、Vuex、Vue-cli
* 插件：vue-awesome-swiper、better-scroll、axios
* CSS框架：stylus
* 数据来源api：本地static目录下mock文件夹内的3个json文件

## 项目结构预览
### 首页部分
* iconfont的导入与使用
* awesome-swiper的使用
* icons图标部分轮播的实现
* 组件间的数据传递
* 使用axios获取本地json模拟数据

### 城市选择部分
* better-scroll的使用
* 右侧字母表布局实现
* 搜索框搜索功能实现
* Vuex数据共享
* localStorage实现页面数据存储
* keep-alive优化路由性能

### 详情部分
* 画廊公共组件拆分与使用
* 使用transition和slot实现渐隐渐显动画
* 实现顶部fixed-top渐隐渐显效果
* 递归组件实现详情列表
* 动态的路由配置

## 项目相关的依赖包
* fastClick: 用来处理移动端<code>click</code>事件 300毫秒延迟
* stylus: CSS 预处理框架
* stylus-loader
* vue-awesome-swiper: 轮播插件
* axios: 实现<code>ajax</code>
* better-scroll: scroll插件
* vuex: 实现数据共享

## 首页
### Swiper组件
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-1.PNG)<br><br>
Swiper组件是顶部的轮播图，它需要自动播放，我们设置其<code>loop: true, autoplay:3000</code>自动播放，轮播时间3秒<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-2.PNG)

### Icons组件
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-3.PNG)<br><br>
computed生命周期中的pages函数，即是分页的函数，使用<code>Math.floor</code>方法向下取整<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-4.PNG)<br><br>
首页中为防止页面加载时，轮播区域的抖动效果，我们给包裹轮播图的<code>class="wrapper"</code>添加一段CSS关键代码<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/swiper-wrapper.PNG)<br><br>
<code>width</code>设置为100%展示全图，<code>padding-bottom</code>的取值是图片的高宽比，使图片还未加载时就能够自动撑开页面，防止页面抖动

### 使用axios获取本地数据
首先，我们需要在Home的全局组件中导入<code>axios</code><br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-5.PNG)<br><br>
在Home的全局组件中，我们要现在<code>data</code>函数里定义几个我们要传给子组件的空的数组或字符串，然后通过<code>axios</code>动态获取到数据后，再将数据更新到<code>data</code>中，再通过父组件向子组件传递数据如<code>:list="swiperList"</code>的方式将数据传给子组件，子组件只要在其<code>props</code>中接收一下，就可以使用父组件传过来的数据了，这样我们就可以做到一次ajax请求就能完全展示一个页面<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-6.PNG)
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-7.PNG)

## 城市页


## 详情页



















