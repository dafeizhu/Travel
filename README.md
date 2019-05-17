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
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-6.PNG)<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/home-7.PNG)

### gitignore 设置
添加<code>staitc/mock</code>，防止被推送到仓库

### 设置 mock数据 开发环境转发代理
打开<code>config</code>目录下的<code>index.js</code>文件，找到<code>module.exports</code>里的<code>dev</code>下边的<code>proxyTable</code>代理，修改代码如下图后，<code>webpack-dev-server</code>工具会自动将<code>/api</code>替换成<code>/static/mock</code><br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/proxyTable.PNG)

## 城市页
### 使用<code>router-link</code>实现从首页右上角的城市点击跳转到城市选择页面
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Home-Header.PNG)<br><br>
做此操作需要在router文件夹下的index.js做路由配置。对<code>path</code>、<code>name</code>和<code>component</code>的声明，并进行<code>import from</code><br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/router-index.PNG)<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/router-index2.PNG)

### List组件
修改<code>border-topbottom</code>的颜色<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/border-topbottom.PNG)<br><br>
固定List页面，使用后续使用<code>better-scroll</code>插件实现类似原生APP上下拖动效果<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/class-list.PNG)

### better-scroll插件的使用
```npm
npm install better-scroll --save
```
在HTML模板代码的最外层，再套上一层<code>ref="wrapper"</code>的<code>div</code>，导入插件，并在<code>mouted()</code>生命周期中新建这个DOM引用的实例<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/import-better-scroll.PNG)

### Alphabet组件
是一个显示在右的<code>a-z</code>字母缩略指引<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Alphabet.PNG)<br><br>
定义<code>handleTouchStart</code>、<code>handleTouchMove</code>、<code>handleTouchEnd</code>这三个函数来完成手指动态滑动字母表，展示首字母城市列表的功能，其中使用判断状态配合<code>setTimeout</code>来进行函数节流，提升网页性能<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Alphabet-setTimeout.PNG)<br><br>

### 城市页兄弟组件间的传值
Alphabet组件向List组件传递数据，是<code>Alphabet.vue</code>先将数据传给<code>City.vue</code>，再由<code>City.vue</code>传给<code>List.vue</code>完成的<br><br>
首先是在Alphabet组件的模板中定义<code>@click="handleLetterClick"</code>，由这个事件向外（父组件）触发一个<code>change</code>事件<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/handeLetterClick.PNG)<br><br>
紧接着，在City父组件中监听这个<code>change</code>事件，将其带过来的参数保存到父组件的<code>data</code>函数中，再由父组件将这个参数传给List组件<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/City-change.PNG)<br><br>
父组件中更新数据<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/City-handleLetterChange.PNG)<br><br>
父组件将更新好的数据传给List组件，子组件在其内部接收参数，从而实现兄弟组件的传值<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/City-List.PNG)

### Search搜索功能实现
在<code>input</code>中做<code>v-model="keyword"</code>的双向绑定<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Search-v-model.PNG)<br><br>
data函数中定义<code>keyword</code>、<code>list</code>、<code>timer</code>，使用监听器<code>watch</code>监听<code>keyword</code>的变化，并使用节流函数进行优化<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Search-watch.PNG)

### 输入逻辑优化
当输入框的内容为空时，清空<code>list</code>数组<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Search-keyword-null.PNG)<br><br>
在<code>computed</code>函数中定义一个<code>hasNoData</code>的函数，使用<code>v-show="hasNoData"</code>将其绑定到一个搜索结果为空则展示的<code>li</code>标签上，实现当<code>list</code>为空时，页面能够展示“没有找到匹配数据”<br><br>
![](https://github.com/dafeizhu/Travel/blob/master/imgs/Search-content.PNG)

### search-item添加better-scroll
```vue
import Ascroll from 'better-scroll'
export default {
  name: 'CitySearch',
  mounted () {
    this.scroll = new Ascroll(this.$refs.search)
  }
}
```
给用于展示搜索结果的<code>div</code>添加<code>ref="search"</code>就能实现better-scroll在搜索页面上的应用


## 详情页


## 项目总结：
















