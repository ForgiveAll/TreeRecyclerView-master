# TreeRecyclerView
树形的reyclerView.使用可以参考demo.

# 要点:
1.可以通过后台控制Item的展示.

2.TreeRecyclerAdapter,可以展开,折叠.多级展示

3.可以扩展支持EmptyAdapter.可以添加headview和footview

4.item的样式可以编写文档,与type进行对应,可以实现复用,以及后台控

5.抽取的adapter可以使用装饰者模式进行扩展.

# 思路:

1.Treeadapter应该只需要关心List<TreeAdapterItem> datas 的内容

2.把每个item看成独立的个体. 布局样式，每行所占比,bindViewHolder都自实现。

3.每一个item应该只关心自己的数据和自己的下一级的数据，不会去关心上上级，下下级

4.展开的实现,点击时item把子数据拿出来,然后添加到adapter的datas中，变成同级，因为只会展开自己的下级数据。

5.折叠的实现,拿到下级数据（可以理解因为一个文件夹下文件)，然后从adapter的datas中删除这些数据。

6.后台控制可以通过初始化注册的方法,将Item的Class注册.保存到集合里

7.后台返回字段,获取对应class文件,通过Class.newInstance()方法构建实例.

8.将ViewHolder与adapter写成通用的,则不需要写多个adatper与viewholder,只需要写多个item.与javabean.


# 目录介绍

+ 1.Adapter
  * Wapper------扩展Adapte的wapper目录
     * EmptyWapper  --------当无数据时显示页面.
     * HeaderAndFootWapper --------添加头部view和尾部view

  - BaseRecyclerAdapter --------封装的Adatper基类
  - ItemManager --------接口,管理Adatper刷新,增删操作
  - TreeRecyclerAdapter ----多级列表,树形结构的adapter
  - TreeRecyclerViewType ----多级列表的显示样式,枚举
  - ViewHolder----封装的通用viewHodler

 + 2.base
   - BaseItem<D extends BaseItemData> ------item的封装
   - BaseItemData-----item的数据要求.javabean需要继承该类.

 + 3.factory
   - ItemConfig ----添加item的class,配置样式
   - Itemfactory----通过class生成BaseItem的工厂类

 + 4.view
   - TreeItem  ----树形列表的子item
   - TreeItemGroup ----树形列表的父item
   - TreeParent---TreeItemGroup 实现该接口
   - TreeSelectItemGroup---可以选中子item的TreeItemGroup.  demo:见购物页面




### QQ交流群:493180098
