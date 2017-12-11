## class如何命名更规范

相信写css的人都会遇到下面的问题：

-  糟糕，怎么命名这个class，好像不太贴切，要是冲突了怎么办，要不要设计成通用一点...
- 而改别人css代码的时候则会一直有个疑问：这个class到底是只在这个地方用了，还是其他地方都用了？

于是就有了下面的做法：

- 最后终于被逼出了个class，简洁也好，中英混搭也罢，看着一头雾水也没关系，反正最后页面显示出来的。
- 这个class应该是只有这个地方用到，我可以放心写。上线之后。如果没问题，则暗自自我欣赏，看吧问题就这么简单，分分钟搞定呀；如果冲突了，则无限感慨，哎，改的时候我就隐隐不安啊，妈蛋，深坑，这是谁写的，谁写的！！！
- 不好，这个class说不定其他地方也用到了，我得加个限制范围，加个父元素？要不重新再命名个class吧，比较保险。最后如果没问题则表示还好比较机智，怎么说哥也是混过的，还是有几斤几两的；如果有问题则表示防不慎防啊，这也太太太坑了吧。

由此可见，class的命名真不是一件简单的事，尤其还要兼顾可辨别性与可读性。

### class命名到底有多难

第一，class跟id不一样，class本来就是设计用来可以重复利用的，而id才是设计唯一的（如果遵循BEM，class几乎也都是唯一的了）。

第二，样式是可以覆盖的，而且先按照权重，再按照定义的先后顺序。也许你花了十分钟设计定义的一个class样式，人家分分钟就给你干掉了，这得多恼火；也许这个页面好好的，跑到另一个页面就跟原先的样式有了冲突。

所以class命名的难就难在既要重复利用，又要避免样式的冲突。如果要重复利用，那么当然是越简单越好，越抽象可用的地方越大，太具体了就完蛋了。而如果要避免样式冲突。BEM的方式最简单，class都唯一了，那还冲突个毛线；其次就是通过父元素限定作用域，可以搞几个层级，而不是单独一个class定义样式；还有就是追加class，来实现差异化；最后不同的页面不同的文件，你用你的我用我的。

    // BEM
    .imgslide__item__img{}
     
    // 父元素限定
    .imgslide .item .img{}
     
    // 追加class
    .img{}
    .img--special{}
     
    // 不同页面不同文件
    // a.html & a.css
    .img{}
    // b.html & b.css
    .img{}

总之，不管有多难，我们还是得试试去解决问题，去寻找一些规律。

### class命名的发展历程

关于class的命名，其实跟人名也差不多，如果要想别人看得懂，那关键还是在于可识别性。到目前为止class的命名大概经历了下面几个重要阶段：

- 混沌阶段，没有规则就是最好的规则
- 原子类阶段，聚集神龙现身手
- 模块阶段，以职能划分，添加前缀
- BEM阶段，规则有序

#### 混沌阶段

这个没什么好说的，刚开始学html的都是这样，名字先简单的来，不够再添加1，2，3什么后缀，或者中英混搭等等，如下：

    h1.title
    h2.title2
    h2.title2-1
    h2.title2-2
    div.hd
    div.hd-s
    div.hd2
    div.hd-xiangxi

一个字，太乱。完全无章程，规律可循，想怎么写就怎么写，写到哪里是哪里。看class去猜意思很可能就是错误的，如.red{color:red;font-size:14px;}，明明说好的红色，却顺带定义了个字体大小。

#### 原子类阶段

这个关键在于拼凑组合，足够多的原子类拼成一个完整的样式：

    .fl{float:left;}
    .fr{float:right;}
    .pr{position:relative;}
    .pa{position:absolute;}
    .tal{text-align:left;}
    .tac{text-align:center;}
    .tar{text-align:right;}
    .fs12{font-size:12px;}
    div.fs12.fl.pr.tac
    div.pa.tal

这种有两个缺点，第一是稍微复杂点的样式都要使用很多class组合，第二是如果要修改样式的时候得修改html文件，而不是css样式，而纯静态的页面是很少的，所以如果是前后端分离的，由php或后端语言渲染页面的话，改个样式还要通知后端同事去修改文件，那估计人家得疯掉。

#### 模块阶段

到了这个时候，css经过这么多年的发展，页面的复杂性已经翻了好几倍了，那些无规划的混沌根本不够用，满眼的class看起来长得都差不多，后面全是1，2，3都不知道标到多少了，却不知道到底是啥区别；而原子类已经不适合频繁的修改调整更新，每更新下都是前后齐心协力。于是按职能划分的class命名规则就出现了

// l表示layout,  g表示global,  m表示mod,

    .l-960
    .l-left
    .l-right
    .g-red
    .g-title
    .g-price
    .m-login
    .m-breadcrumb
    .m-slide

这种命名方式在一定程度解决了混乱不堪的问题，所有的按照职能划分看起来很美好，不过动不动加个前缀确实不怎么优雅，再者随着mod的增加，这个以m开头的前缀根本就不够用，于是又乱了，有加二级前缀的，也有另起前缀的。

#### BEM

这个估计地球上做前端的都知道吧，实在是太火了，所以不用来解释了。优点就是你只管写你自己的，99.99%的几率不会去干掉别人的样式，class实在太长了，能一样那得多高的几率啊。缺点还是class太长，太长，太长，重要的事情说三遍。一般都记不住自己定义的class，写css的时候只好对着去拷贝。然后最痛苦的就是去修改更新，明明很简单的东西，然后你还要搞个超长的class，那叫一个烦躁，想想都懒得动手。

### 他山之石

其实每个命名的发展经历都有其特定的历史意义，也当然有其价值。所以吸取之长，弃之短缺就很好了。比喻写简单demo的时候，我们就可以用到混沌阶段的命名，足够简单，不需要纠结思考；而原子类尤其是一些简单的样式，如一行代码就可以搞定，起个class名甚是纠结，还不如直接上原子类；至于模块类，说真的应用的场景就更多了，如布局，js操作类等；而BEM我们同样可借鉴其思想，如.class.class--name使用--表示特殊化，以区分-。

这里我们站在前人的肩膀上，试着去开辟一条道路，可以兼顾简洁可读性及可理解辨别性。当然class的简洁肯定离不开关键词的应用，这里我们先来过一遍常见的class关键词。

### 常见class关键词：

- 布局类：header, footer, container, main, content, aside, page, section
- 包裹类：wrap, inner
- 区块类：region, block, box
- 结构类：hd, bd, ft, top, bottom, left, right, middle, col, row, grid, span
- 列表类：list, item, field
- 主次类：primary, secondary, sub, minor
- 大小类：s, m, l, xl, large, small
- 状态类：active, current, checked, hover, fail, success, warn, error, on, off
- 导航类：nav, prev, next, breadcrumb, forward, back, indicator, paging, first, last
- 交互类：tips, alert, modal, pop, panel, tabs, accordion, slide, scroll, overlay,
- 星级类：rate, star
- 分割类：group, seperate, divider
- 等分类：full, half, third, quarter
- 表格类：table, tr, td, cell, row
- 图片类：img, thumbnail, original, album, gallery
- 语言类：cn, en
- 论坛类：forum, bbs, topic, post
- 方向类：up, down, left, right
- 其他语义类：btn, close, ok, cancel, switch; link, title, info, intro, more, icon; form, label, search, contact, phone, date, email, user; view, loading...

有了关键词之后，我们先来制定一些简单的规则

### 制定简单规则：

- 以中划线连接，如.item-img
- 使用两个中划线表示特殊化，如.item-img.item-img--small表示在.item-img的基础上特殊化
- 状态类直接使用单词，参考上面的关键词，如.active, .checked
- 图标以icon-为前缀（字体图标采用.icon-font.i-name方式命名）。
- 模块采用关键词命名，如.slide, .modal, .tips, .tabs，特殊化采用上面两个中划线表示，如.imgslide--full, .modal--pay, .tips--up, .tabs--simple
- js操作的类统一加上js-前缀
- 不要超过四个class组合使用，如.a.b.c.d

关键词及规则都有了，就剩实战操作啦。


原文作者：结一

转载自：http://www.w3cplus.com/css/css-class-name.html
