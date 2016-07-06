# CSS规范
本文档的目标是使CSS代码风格保持一致，容易被理解和被维护。

##代码风格

   **[强制]** 文件使用用无BOM的UTF-8编码

   **[强制]** 使用4个空格作为一个缩进层级

   **[强制]** 选择器 与 { 之间必须包含空格

        .selecter {

        }
   **[强制]** 属性名之后与`:`之间不留空格，`:`与属性值间必须包含一个空格

        margin: 0;

   **[强制]** 当一个规则中有多个选择器，每个选择器独占一行，在`,`后面进行换行

        .selecter1,
        .selecter2,
        .selecter3 {

        }

   **[强制]** 单行只能书写一个属性

        .selecter {
            line-height: 1.5;
            overflow: hidden;
         }

   **[强制]** 一个属性定义后必须以`;`结尾

   **[强制]** 每行不得超过120个字节，除非单行不可分割，如超长URL。
               遇到超长样式，建议以`空格`或`,`处进行换行

        .selecter {
            background:
                url(//img7.meiquapp.com/201605_23_19_58_40_1464004720577.jpg)
                center center no-repeat;
            font:
                14px/1.5 #333
                "Helvetica Neue,Helvetica", "Arial,PingFang SC", "Hiragino Sans GB",
                "WenQuanYi Micro Hei", "Microsoft Yahei", sans-serif;
        }

   **[建议]** 超长样式的属性值建议另取一行开始，并以一个缩进层级缩进,建议按逻辑分组

        .selecter {
            background:
                url(//img7.meiquapp.com/201605_23_19_58_40_1464004720577.jpg)
                center center no-repeat;
        }

   **[强制]** 单个属性中有多个值的，值与值之间必须一个空格进行分隔

        .selecter {
            margin: 10px 0 20px 20px;
            font-family: "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
        }

   **[强制]** `>`, `+`, `~`选择器前后必须保留一个空格

        .selecter > a {
            color: #fff;
        }
        .selecter + p {
            margin-bottom: 10px;
        }

##命名

   **[建议]** 命名时最好以功能命名而不以样式命名，便于后期维护，比如

        <h2 class="font-title">我是标题</h2>

        /* 前期UI设计标题为粉红 */
        .font-title {
            color: #d8085c;
        }

        /* 后期设计修改为红色 */
        .font-title {
            color: #ff0;
        }

        /* 这样只要修改属性值而不用去修改html上的class */

   例外，部分辅助类样式，如bootstrap的左浮动pull-left，左对齐text-left等常用排版样式

   **[强制]** 不许使用拼音，用常用简短的功能性单词来表示，下面列表可做参考


        CSS样式命名 -> 说明
        ----------------------------------
        wrapper     -> 页面外围控制整体布局宽度
        container   -> 容器,用于最外层
        layout      -> 布局
        head或header-> 页头
        foot或footer-> 页脚
        nav         -> 主导航
        subnav      -> 二级导航
        menu        -> 菜单
        submenu     -> 二级菜单
        sideBar     -> 侧栏
        main        -> 页面主体
        msg         -> 提示信息
        tag         -> 标签
        friendlink  -> 友情链接
        title       -> 标题
        summary     -> 摘要
        login       -> 登录
        regsiter    -> 注册
        search-bar  -> 搜索条
        search-input -> 搜索输入框
        search-results -> 搜索结果
        siteinfo    -> 网站信息
        joinus      -> 加入我们
        partner     -> 合作伙伴
        arrow       -> 箭头
        sitemap     -> 网站地图
        dropmenu    -> 下拉菜单
        status      -> 状态
        tabs        -> 标签页
        review      -> 评论

   这些只是作为参考，欢迎补充和订正

   **[强制]** 类选择器统一使用小写字母，用 `-` 分隔单词；ID选择器以驼峰法命名

   **[建议]** 类选择器命名不建议在模块父级使用过于简单的名字，一般以“模块-功能"的形式命名。部分最低层级的元素可以考虑用简单的单词

##选择器

   **[建议]** 选择优先使用类选择器 `.selecter` ，注重其可重复性

   **[建议]** ID选择器 `#select` 使用前提其是唯一的并是父级的，主要是大模块上使用，如页头页脚之类；

   **[建议]** 元素选择器 `p` 不建议过多使用，只能是用于reset解决浏览器的兼容性和操作上的便利，
   根据每个项目的实际需求进行适当修改。比较经常使用的有

        body, h1, h2, h3, h4, h5, h6, p {
            margin: 0;
        }
        ul {
            margin: 0;
            padding: 0;
            list-style: none;
        }
        a,
        a:hover {
            text-decoration: none;
        }
        img {
            border: 0;
        }

   **[建议]** 元素选择器还可以用于组件最末级，对最后的元素进行筛选，最忌讳在组件父级使用，不易维护，不利于后期组件添加

   **[建议]** 子元素选择器、相邻兄弟选择器 `>` 、 `+` 主要用于组件部分元素筛选

   **[强制]** 选择器嵌套不要超过3级，过多层级不利于阅读也不利于封装

##属性

   **[建议]** 属性值能缩写的尽量使用缩写

        body {
            font: 12px/1.5 arial, sans-serif;
        }

   **[建议]** padding、margin、border这类具有方向性的属性时，除非确认需要四个方向都设定，
   否则请不要使用缩写，避免对其他类的设定造成覆盖

        <p>我是正文</p>
        <p class="image"><img src="image.jpg" alt="我是正文图片"></p>

        p {
            margin-bottom: 10px;
        }
        p.image {
            margin: auto 20px;
        }

        /* 按原设计段落间距统一为10px，为使图片不与段落两端对齐，原本只是要增加左右20px的边距，却因此覆盖掉原来margin-bottom: 10px */

        p.image {
            margin-left: 20px;
            margin-right: 20px;
        }

        /* 这样写就没有问题了 */

   **[建议]** 当属性值中有0时，不要为0加单位

        margin: 0

   **[建议]** 避免使用!important

   **[强制]** 字体名称中如果有空格必须使用双引号包围

        font-family: "Microsoft YaHei", sans-serif;



