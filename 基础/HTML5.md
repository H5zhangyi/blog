## HTML5新特性

- 绘画canvas
- 用于媒介回放的video和audio元素
- 本地离线存储localStorage长期存储数据，浏览器关闭后数据不丢失
- sessionStorage的数据在浏览器关闭后自动删除
- 语义化更好的内容元素，比如article,footer,header,nav,section
- 表单控件，calendar,date,time,email,url等
- 新的技术webworker,websockt,Geolocation
- 移出的元素
    - 纯表现的元素：basefont,big,center,font等
    - 产生负面影响的元素：frame frameset等
- ie8 7 6 支持通过document.createElemet方法产生新的标签，可以利用这一特性让这些浏览器支持html5新标签

## CSS3新增动画

### transform: 2d变换

    transform(x,y) 平移
    scale(2,2) 缩放
    rotate(45deg) 旋转
    skew(30deg,30deg) 倾斜
```
    tansform-origin: 0px 0px; // 旋转坐标
    transition: all 1s linear;  // 过渡
```

### background: linear-gradient(to right,red,yellow)

```
                线性渐变        (to right,green 0%,yellow 20%,red 50%)
                               (to right,rgba(255,0,0,0),rgba(255,0,0,1)
                radial-gradient(0px 100px,yellow,green,red)
                  径向渐变          坐标
```

### box-shadow(0px  0px  0px  5px  red) 外阴影 

```
              x偏移 y偏移 模糊半径 向外扩展 颜色
              .........................inset  内阴影
    border-radius: (50px)
                   (50px/100px)
                   (50px,20px,30px,10px/10px,20px,30px,40px)
    border-image(url() 20px round) 常用
                            repeat
                            stretch 默认
                            space
```
