# 这是是一个 vue2.0 的移动端项目
## 制作首页 App 组件 
- Header 区域使用了 Mint UI 组件库中的 Header 组件
- Tabbar 区域使用了 MUI 组件库的 Tabbar.html
  - 在制作购物车图标时
  - 先把扩展图标的 css 样式，拷贝到项目中
  - 再把扩展字体库 ttf 文件，拷贝到项目中
  - 在 main.js 导入
  - 最后为小图标加上如下样式 `class="mui-icon mui-icon-extra mui-icon-extra-cart"` 
- 在中间区域放置 router-view 来展示路由匹配到的组件
## 改造 tabber 为 router-link
## 设置路由高亮
## 点击 tabbar 中的路由链接，展示对应的路由组件
## 制做首页轮播图布局
## 加载首页轮播图数据
1. 获取数据，使用 vue-resource(需要安装)
2. 使用 vue-resource 的this.$http.get 获取数据
3. 获取抓到的数据，要保存到 data 身上
4. 使用 v-for 循环渲染每个 item 项

## 改造九宫格区域的样式

## 改造新闻资讯路由链接

## 新闻资讯页面制作
1. 绘制界面 使用 MUI 中的 media-list.html
2. 使用 vue-resource 获取数据
3. 渲染真实数据

## 实现新闻资讯列表 点击跳转到新闻详情
1. 把列表中的每一项改造为 router-link 同时，在跳转的时候应该提供唯一的Id标识符
2. 创建新闻详情的组件页面 NewsInfo.vue
3. 在路由模块中，将 新闻详情的 路由地址 和 组件页面对应起来

## 实现新闻详情的页面布局和数据渲染

## 单独封装一个 comment.vue 评论子组件
1. 先创建一个 comment.vue 组件模板
2. 在需要使用 comment 组件的页面中，先手动带入 comment 组件
 `import comment from './comment.vue'`
3. 在父组件中，使用 `components` 属性，将刚才导入的 comment 组件，注册为自己的子组件
4. 将注册子组件时候的，注册名称，以标签形式，在页面中引用即可

## 获取所有的评论数据显示到页面中

## 实现点击加载更多评论的功能
1. 未加载更多按钮，绑定点击事件，在事件中，去请求下一页数据
2. 点击加载更多，让 pageIndex++ 然后重新调用 this.getComments() 方法重新获取一页的数据
3. 为了防止新数据 覆盖旧数据 我们在点击加载更多的时候，每当获取新数据，应该让老数据 调用数组的 concat 方法，拼接上新数组