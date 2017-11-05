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