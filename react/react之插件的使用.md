#### 1、react-virtualized 可视区域渲染

git地址：https://github.com/bvaughn/react-virtualized/blob/master/docs

用于：在展示大型列表和表格数据, 如: 城市列表、通讯录、微博等，会导致页面不流畅、卡顿等性能问题。
 原因: 大量的DOM节点的重绘和重排，设备老旧；导致移动设备耗电耗电加快，设备发热。
 优化方案:  1.懒渲染   2. react-virtualized (可视区域渲染)

常用的组件有：

List:列表的组件

AutoSizer:让List组件占满屏幕

WindowScroller:用于设置List跟随window滚动而不是List自己滚动

InfiniteLoader:滚动的时候加载新的数据

#### 2、babel-react-optimize

生产环境移除proTypes检验，因为检验主要是开发用，发布之后没意义，用户不会去控制台看错误信息，而且设置校验也会占用空间，处理也会消耗cpu；

