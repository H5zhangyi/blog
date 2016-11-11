###transform: 2d变换
    transform(x,y) 平移
    scale(2,2) 缩放
    rotate(45deg) 旋转
    skew(30deg,30deg) 倾斜
```
    tansform-origin: 0px 0px; // 旋转坐标
    transition: all 1s linear;  // 过渡
```
###background: linear-gradient(to right,red,yellow)
```
                线性渐变        (to right,green 0%,yellow 20%,red 50%)
                               (to right,rgba(255,0,0,0),rgba(255,0,0,1)
                radial-gradient(0px 100px,yellow,green,red)
                  径向渐变          坐标
```
###box-shadow(0px  0px  0px  5px  red) 外阴影 
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
