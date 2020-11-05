# CSS

------

官方文档：https://www.w3.org/TR/CSS22/propidx.html

中文文档(MDN)：https://developer.mozilla.org/zh-CN/docs/Web/CSS

CSS颜色：flat ui colors

1. CSS外部引入的两种方式：

   不建议使用@import导入CSS文件，它的效率比link低；

   ```css
   <!-使用link引用-->
   <link rel="stylesheet" href="./css/style.css">
   
   <!-使用@import引用-->
   @import url('./css/style.css')
   ```

2.  CSS选择器：

   - 通用选择器： *{ } 

     - 匹配到所有的元素

     - 一般用来给所有的元素做一些通用的设置

   - 元素选择器（标签选择器）：  html标签 { }
   - **类选择器**： .{ }  
     - 一个元素可以有多个类，以空格为分割
     - 类名称最好用 中划线- 连接
   - **id选择器**：#{ }
     - 在同一个页面中id不要重复

   - 属性选择器：
     - 一般用法：[title]{ }
     - 选值用法：[title="one"]{ }
       - 包含one：[title*="one"]{ }
       - 以one开头：[title^="one"]{ }
       - 以one结尾：[title$="one"]{ }
       - 以one开头且后面紧跟着连字符- ：[title｜="one"]{ }
       - 包含one，且与其他单词必须用空格分割：[title～="one"]{ }

   - **后代选择器**：div  span{ }
     - 包括直接子代和间接子代
   - 子代选择器：div > span{ }
     - 只包括直接子元素

   - 相邻兄弟选择器：div+p{ }
     - div元素后面紧挨着的p元素（两者是兄弟关系）

   - 全体兄弟选择器：div~p{ }
     - div元素后面的所有p元素（两者是兄弟关系）

   - **交集选择器**：div.one{ }
     - 同时符合2个条件：div元素、class的值是one

   - **并集选择器**：div, .one{ }
     - 符合一个条件即可：div元素或者class的值是one

3. 驼峰标识：
   - 小驼峰：第一个单词首字母小写，后面遇到一个单词首字母就大写；一般用在js的函数名字中；
   - 大驼峰：所有的单词首字母都大写；一般用在js定义类的名字；

4. div元素一般作为其他元素的父容器，把其他元素包住，代表一个整体，用于把网页分割成多个独立的部分，一个小技巧用来快速调试网页布局：

   ```css
   div{
     outline: 2px solid green !important;
   }
   ```

5. 文字属性：

   - text-decoration:用于给文字设置装饰线

     - none:不设置

     - underline:下划线
     - overline:上划线
     - line-through:中划线（删除线）

   - letter-spacing:设置字母直接的间距

   - word-spacing:设置单词直接的间距

   - text-transform:用于设置大小写的转换

     - none:不设置

     - capitalize:首字母变大写
     - uppercase:所有字母变大写
     - lowercase:所有字母变小写

   - text-indent:用于设置第一行文字的缩进
   - text-align:用于设置元素内容在元素中的水平对齐方式
     - left:左对齐
     - right:右对齐
     - center:中间显示

6. 字体属性：

   - font-size:决定字体大小
   - font-family:用于设置字体名称
     - 为了防止设置的字体刚好操作系统没有，会设置多个字体
     - 如果在开发中，中英文要使用不同的字体时，中文字体写在后面

   - font-weight:设置文字的粗细
     - 一般用的比较多的是700
   - font-style:设置文字的常规、斜体显示
     - normal:常规显示
     - italic:用字体的斜体显示（前提是font-family字体本身支持斜体）
     - oblique:文本倾斜显示（将文字倾斜)

   - line-height

     - 用于设置文本的最小行高，即一行文字所占据的高度
     - 行高的严格定义是两行文字基线（baseline）之间的间距
     - 基线：与小写字母x最底部对齐的线

     ![截屏2020-11-01 下午9.54.53](https://gitee.com/baolk/typora_images/raw/master/img/css_%E8%A1%8C%E9%AB%98.png)

     - 行高可以用来让div中的一行文字垂直居中:让line-height等于div的height

       ```css
       div{
         width:200px;
         height:50px;
         backgroud-color:skyblue;
         line-height:50px;
       }
       ```

   - font是一个缩写属性

     font-style font-variant font-weight font-size/line-height font-family

     ```css
     div{
       font:italic small-caps 700 20px/40px "微软雅黑"
     }
     ```

     - font-style  font-variant  font-weight可以调换顺序，也可以省略
     - /line-height可以省略，如果不省略，必须跟着font-size后面
     - font-size font-family不可以调换顺序，不可以省略

7. 伪类选择器：

   - 动态伪类（dynamic pseudo-classes）：

     - a标签的伪元素
       - a:link  未访问的链接 
       - a:visited  已访问过的链接
       - a:hover 鼠标挪动到链接上
       - a:active 激活的链接（鼠标在链接上长按住未松开）
       - **必须严格按照以上顺序才会生效**

     - :hover和 :active也能用在其他元素上
     - :focus指当前拥有输入焦点的元素（能接受键盘输入）
       - 例如文本框一聚焦后，背景变成红色

   - 结构伪类（structural pseudo-classes）:

     - :nth-child-n

       ```html
       <!--1.基本使用-->
       <html>
         <head>
           <style>
             /*要同时满足是p标签以及
             p标签是子元素中的第三个元素
             */
             p:nth-child(3){
               color:red;
             }
           </style>
         </head>
         <body>
           <div>
             <p>1</p>
             <p>2</p>
             <p>3</p>  <!--变红-->
           </div>
           
           <div>
             <strong>1</strong>
           </div>
           
           <p>				<!--因为p是body元素中的第三个子元素-->
             <span>1</span>   <!--变红-->
             <span>2</span>   <!--变红-->
             <span>3</span>	 <!--变红-->
           </p>
           
         </body>
       </html>
       
       <!--n的取值是0，1，2，3，4，5，7，……-->
       
       <!--2.选择偶数项-->
       p:nth-child(2n)
       p:nth-child(even)
       
       <!--3.选择奇数项-->
       p:nth-child(2n+1)
       p:nth-child(odd)
       
       <!--3.取前几-->
       p:nth-child(-n+3)  <!--表示取前3-->
       
       ```

     - :nth-last-child-n

       - 与:nth-child-n类似，但是从后往前数

     - :nth-of-type

       - 与:nth-child-n唯一不同的是，它忽略其他类型，只数某个相同元素的子元素

         ```html
         <html>
           <title>
             <style>
               p:nth-of-type(2){
                 color:red;
               }
             </style>
           </title>
           <body>
             <div>
               <div>1</div>
               <p>1</p>
               <p>2</p>   <!--该项变红，p标签的第2项-->
               <p>3</p>
               <p>4</p>
             </div>
           </body>
         </html>
         ```

     - :nth-last-of-type
       - 与:nth-last-of-type类似，但是从后往前数
     - :first-child等同于:nth-child(1)
     - :last-child等同于:nth-last-child(1)
     - :first-of-type等同于:nth-of-type(1)
     - :last-of-type等同于:nth-last-of-type(1)
     - :only-child，是父元素中唯一的子元素
     - :only-of-type，是父元素中唯一的这种类型的子元素
     - :root，根元素，就是HTML元素
     - :empty，选中元素内容为空的元素

   - 否定伪类

     - :not(x)
     - x是一个简单选择器，可以是元素选择器，通用选择器，属性选择器，类选择器，id选择器以及伪类
     - 只支持简单选择器，不可以放组合选择器

8. 伪元素

   - ::first-line 可以针对首行文本设置属性

   - ::first-letter 可以针对首字母设置属性

   - ::before和::after 

     - 用来在一个元素的前面或后面插入其他内容（文字或图片）

       ```html
       <html>
         <title>
           <style>
             span::before{
               content:"1"  
               /*这个元素不能少，且可以是文字也可以是图片*/
             }
           </style>
         </title>
         <body>
           <span>我是span元素</span>
         </body>
       </html>
       
       <!--1我是span元素-->
       ```

     - 伪元素可以看成行内元素，不能设置宽度

9. Emmet语法使用

   - 生成html5代码：！

   - 生成子代元素：div > h2 > p

   - 生成兄弟元素：div + h2 + p

   - 生成多个元素：p*3

   - 生成一个层级元素：div>p>span^^h1+strong

     ```html
     <div>
       <p>
         <span></span>
       </p>
     </div>
     <h1></h1>
     <strong></strong>
     ```

   - 对元素进行分组：(div>(p>span))+h1+strong

     ```html
     <div>
       <p>
         <span></span>
       </p>
     </div>
     <h1></h1>
     <strong></strong>
     ```

   - 生成元素的属性
     - div#main：id属性
     - div.box：class属性
     - div[ title="hahaha" ]：普通属性

   - 生成元素的内容：div{我是div元素}

   - 生成结构中有数字：div.box$*4

     ```html
     <div>
       <div class="box1">1</div>
       <div class="box2">2</div>
       <div class="box3">3</div>
       <div class="box4">4</div>
     </div>
     ```

   - 隐士标签

     - div的省略写法

       ```html
       .box  #main
       <!--默认生成div标签-->
       ```

     - 列表的省略写法：

       ```html
       <!--完整写法-->
       ul>li.item*3
       <!--省略写法-->
       ul>.item*3
       ```

     - 表格的省略写法：

       ```html
       table>#row$*4>[colspan=2]
       ```

10. CSS的继承特性
    - 一个元素没有设置某属性的值，就会跟随父元素的值，一旦设置了自己的值，就会使用者自己设置的值
    - 不能继承的属性，一般可以用inherit值强制继承
    - CSS属性继承的是**计算值**，而不是当初编写属性时的指定值（字面量），即把计算出来的结果继承过来
11. CSS的层叠
    - CSS允许多个相同名字的CSS属性层叠到同一个元素上
    - 不同选择器时，看权重大小：
      - ！important：10000
      - 内联样式：1000
      - id选择器：100
      - 类选择器、属性选择器、伪类：10
      - 元素选择器：1
      - 通配符：0

12. 与列表相关的CSS属性

    - 以下元素都可以继承，所以设置给ol、ul元素时，默认会应用到li元素

    - list-style-type：设置li元素前面标记的样式
      - disc(实心圆)、circle(空心圆)、square(实心方块)、decimal(数字)、none(什么都没有)
    - list-style-image：设置某张图片为li元素的标记
    - list-style-position：设置li元素前面标记的位置
      - inside
      - outside
    - list-style：以上属性的缩写，顺序可以任意

13. 与表格相关的CSS属性

    - 实现一个细线表格：合并边框

      ```html
      <html>
        <title>
          <style>
            td{
              border:1px solid #666;
              border-collapse:collapse; /*将边框合并*/
              margin:100px auto  /*table的居中显示*/
            }
          </style>
        </title>
        <body>
          <table>
            <tr>
              <td>1</td>
              <td>2</td>
              <td>3</td>
            </tr>
          </table>
        </body>
      </html>
      ```

    - 实现单元格的合并：

      - 合并的要领：合并方向是向右、向下

      - 使用colspan和rowspan

        ```html
        <!--column列-->
        <!--row:行-->
        <table>
          <tr>
            <td colspan="2">1</td>
           <!-- <td>2</td> -->
            <td>3</td>
          </tr>
          <tr>
            <td>4</td>
            <td>5</td>
            <td>6</td>
          </tr>
          <tr>
            <td>7</td>
            <td>8</td>
            <td>9</td>
          </tr>
        </table>
        ```

      - border-spacing：用于设置单元格之间的水平、垂直间距

        ```css
        table{
          border-spacing:10px 15px; /*上下10px 左右15px*/
        }
        ```

14. 去除input的Tab键选中效果

    ```css
    input{
      outline:none;
    }
    ```

15. textarea 缩放设置

    ```css
    textarea{
      resize:none; /*禁止缩放*/
      resize:horizontal; /*水平缩放*/
      resize:vertical; /*垂直缩放*/
      resize:both; /*同时缩放*/
    }
    ```

16. CSS元素类型：

    ![截屏2020-11-04 下午1.42.33](https://gitee.com/baolk/typora_images/raw/master/img/css_%E5%85%83%E7%B4%A0%E5%88%86%E7%B1%BB.png)

    - 元素显示类型（是否独占一行）：
      - 块级元素：独占**父元素**的一行
      - 行内元素：可以和其他元素在同一行显示
    - 元素内容类型（是否浏览器会替换元素）：
      - 替换元素：元素本身没内容，浏览器根据元素的类型和属性来决定元素的具体显示内容；
      - 非替换元素：元素本身有内容，浏览器直接根据元素内容来显示；

17. CSS的display属性

    - block：块级元素

    - inline：行内元素

    - none：隐藏元素

    - inline-block：行内块级元素（可以实现行内元素，并设置宽高）

    - 其余取值：

      ![截屏2020-11-04 下午2.07.37](https://gitee.com/baolk/typora_images/raw/master/img/css_display%E4%B8%80%E4%BA%9B%E5%8F%96%E5%80%BC.png)

18. CSS的visibility属性

    - 控制元素的可见性，有两个取值
      - visible：默认显示
      - hidden：隐藏，与display：none区别是：
        - display:none不再占据空间
        - visibility:hidden隐藏之后仍然占据空间

19. CSS的overflow属性

    - 用于控制内容溢出时的行为，有两个取值
      - visible：溢出的内容照样可见
      - hidden：溢出的内容直接被裁减
      - scroll：溢出的内容被裁减，但增加滚动机制查看，滚动条区域占据width和height
      - auto：自动根据内容是否溢出来判断是否提供滚动机制

20. 元素间的空格

    - 行内级元素(inline-level-elements)都会产生空格，原因是代码中间的空格会被浏览器解析出来成为空格；
    - 解决方法：给元素加float

21. CSS属性—盒子模型

    ![截屏2020-11-04 下午3.10.44](https://gitee.com/baolk/typora_images/raw/master/img/css_%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B.png)

    - content 内容
      - width：宽度
      - min-width：最小宽度，当父容器变小时会产生滚动条
      - max-width：最大宽度
      - height：高度
      - min-height：最小高度，当父容器变小时会产生滚动条
      - max-width：最大高度
    - padding 内边距
      - padding-top：上内边距
      - padding-right：右内边距
      - padding-bottom：下内边距
      - padding-left：左内边距
      - padding：顺序是上右下左，可省略

    - margin 外边距

      - margin-top：上外边距
      - margin-right：右外边距
      - margin-bottom：下外边距
      - margin-left：左外边距
      - margin：顺序是上右下左，可省略
      - **上下margin传递（左右不会传递）**：
        - margin-top传递：如果块级元素的顶部线和父元素的顶部线重叠，那么这个块级元素的margin-top值会传递给父元素；
        - margin-bottom传递：如果块级元素的底部线和父元素的底部线重叠，并且父元素的高度是auto，那么这个块级元素的margin-top值会传递给父元素；
        - **防止传递：触发BFC，设置overflow为auto/hidden**
        - 建议使用margin设置兄弟元素的间距，使用padding设置父子元素的间距
      - 上下margin折叠（左右不会折叠）
        - 垂直方向上2个margin会合并成1个margin（取较大值），这种现象叫做collapse（折叠）
        - 如何防止：只设置一个margin

    - border 边框

      - 各个属性都可以拆分成top、right、bottom、left

      - 边框宽度：border-width

      - 边框颜色：border-color

      - 边框样式：border-style（常用是dashed和solid）

      - border：border-width  border-style  border-color  （不区分顺序）

      - 圆角：border-radius（使用百分比会参考当前元素的border+padding+width）

      - 用border实现三角形（开发的技巧）：

        ```html
        
        ```

22. 行内元素的特殊性（margin padding border）

    - 以下属性对行内非替换元素不起作用
      - width、height、margin-top、margin-bottom
    - 以下属性对行内非替换元素的效果比较特殊（设置之后不占据空间）
      - padding-top、padding-bottom、border-top、border-bottom
    - 如何防止：设置成display：inline-block

23. CSS的outline属性

    - 表示元素的外轮廓，同时不占空间，默认在border的外面

    - 用途：1.浏览器调试，可以使用outline来参考别人的布局

      ​			2.去除a元素、input元素的focus轮廓效果

      ```css
      a,html,textarea{
      	outline:none
      }
      ```

24. CSS的box-shadow属性

    - 为盒子设置一个或者多个阴影
    - <shadow> = inset?<length>{2,4}&&<color>?
      - inset表示外框阴影变成内框阴影
      - 第一个<length>表示水平方向的偏移，正数向右偏移
      - 第二个<length>表示垂直方向的偏移，正数向下偏移
      - 第三个<length>表示模糊半径
      - 第四个<length>表示向四周伸缩
      - <color>表示颜色

25. CSS的text-shadow属性

    - 与box-shadow类似使用，用于给文字添加阴影效果

26. CSS的box-sizing属性

    - 用于设置盒子模型的宽高行为，即指定宽高包括哪些部分

    - 有两个取值：

      - content-box：宽高只包括content

      - ![截屏2020-11-04 下午6.11.23](https://gitee.com/baolk/typora_images/raw/master/img/css_content-box.png)

      - border-box：宽高包括content+padding+border

        ![截屏2020-11-04 下午6.12.04](https://gitee.com/baolk/typora_images/raw/master/img/css_border-box.png)

27. 水平居中—不同类型的方式

    - 普通文本

      ```css
      text-align:center;
      ```

    - 行内元素

      ```css
      text-align:center;
      ```

    - 行内替换元素（图片）

      ```css
      text-align:center;
      ```

    - 行内块级元素：inline-block

      ```css
      text-align:center;
      ```

    - 块级元素

      ```css
      margin:0 auto;
      /*浏览器均分左右两边*/
      ```

28. CSS属性—背景

    - background-image
      - 用于设置元素的背景图片
      - 会盖在background-color上面，而不是覆盖
      - 如果设置多张图片，会默认显示第一张，其他图片按顺序叠在下面
      - 元素本身没有具体宽高，背景图片不会显示

    - background-repeat
      - 平铺效果
      - 有四种属性：
        - repeat：平铺
        - repeat-x：横向平铺
        - repeat-y：垂直平铺
        - norepeat：不平铺
    - background-size
      - 用来设置背景图的大小
      - 有五个取值：
        - auto：以背景图本身大小显示
        - cover：缩放背景图，以完全覆盖铺满元素
        - contain：缩放背景图，宽度或高度铺满元素，但是图片保持宽高比
        - <percentage>：百分比，相对于背景区，分水平和垂直方向有两个值
        - length：具体的大小
    - backgroud-position
      - 用于设置图片在水平、垂直方向上的具体位置
      - 分水平和垂直方向有两个值
      - 可设置具体的值，正负都可以
      - 水平方向可以设置left、right、center
      - 垂直方向可以设置top、bottom、center
      - 如果只设置了一个方向，另一个方向默认是center
    - CSS Sprite
      - 是一种CSS图像合成技术，将各种小图片合并到一张图片上，然后利用CSS的背景定位来显示对应的图片部分
      - 使用的好处是：1.减少网页的http请求数量，加快网页响应速度，减轻服务器的压力；2.减少图片总大小；3.解决图片命名困扰；
      - 使用background-position取图片
    - background-attachment
      - 可以设置以下3个值
        - scroll：背景图片随着元素一起滚动（默认值）
        - local：背景图片随着**元素以及元素内容**一起滚动
        - fixed：背景图片相对于浏览器窗口固定
    - background
      - 是以上几种属性的缩写形式，background-size必须跟在background-position后面，其他顺序任意

29. background-image和img的选择

    ![截屏2020-11-04 下午7.54.50](https://gitee.com/baolk/typora_images/raw/master/img/css_img%E7%9A%84%E9%80%89%E6%8B%A9.png)

30. 光标的展示样式（cursor）

    - cursor可以设置鼠标在元素上面的显示样式
    - 常见的设值有：
      - auto：自动
      - default：箭头
      - pointer：小手
      - text：竖线
      - none：不显示

31. 标准流（normal flow）

    - 默认情况下，元素都是按照normal flow进行排布的，从左到右，从上到下；
    - 在标准流中，使用margin和padding对元素定位时会影响到其他元素的定位效果，不便于实现元素的层叠效果

32. CSS的position属性

    - 利用position可以对元素进行定位，常用取值如下：
      - static：静态定位（默认）
      - relative：相对定位
      - absolute：绝对定位
      - fixed：固定定位

33. 相对定位

    - 元素按照标准流布局，可以通过left、right、top、bottom进行定位

    - 定位参照对象是元素自己原来的位置

    - 相对定位的应用场景：

      - 在不影响其他元素位置的前提下，对当前元素进行微调

      - 当浏览器屏幕变小的时候，希望一张长图的中间始终在屏幕中间，可以使用相对定位进行图片的动态移动：

        - 移动距离=图片长度 * 0.5—div长度 * 0.5

          ```css
          /*向左移动img的一半*/
          img{
              position：relative;
              left:-960px;
              transform:translate(-50%);/*不写死，相对于自己图片的百分之50*/
              /*向右移动父元素（div）的一半*/
              margin-left:50%;
           }
          ```

34. 固定定位

    - 元素脱离标准流、脱标
    - 可以通过left、right、top、bottom进行定位
    - 定位参照对象是视口，当画布滚动时，固定不动

35. 脱离标准流的元素特点：fixed、absolute、float

    - 可以随意设置宽高
    - 宽高默认由内容决定
    - 不再受标准流的约束
    - 不再给父元素汇报宽高度
    - display变成了block，由于脱标没有父元素，所以现象为包裹内容

36. 绝对定位

    - 元素脱离标准流、脱标
    - 可以通过left、right、top、bottom进行定位
    - 定位参照对象是最邻近的定位祖先元素（position:relative|fixed|absolute）
    - 子绝父相：
      - 大多数情况下，子元素的绝对定位是相对于父元素进行定位的，通常将父元素设置为relative，将子元素设置为absolute

37. 绝对定位技巧

    - 绝对定位元素是指position为absolute或fixed的元素

    - 对于绝对定位元素来说

      - 定位参照对象的宽度=left + right + margin-left + margin-right + 绝对定位元素的实际占用宽度 
      - 定位参照对象的高度=top + bottom + margin-top + margin-bottom + 绝对定位元素的实际占用高度 

    - 具体应用：

      - 让子元素完全占据父元素

        ```css
        left:0;
        right:0;
        top:0;
        bottom:0;
        margin:0;
        ```

      - 让子元素在父元素居中显示

        ```css
        left:0;
        right:0;
        top:0;
        bottom:0;
        margin:auto;
        ```

38. 元素的层叠

    ![截屏2020-11-05 上午10.03.18](https://gitee.com/baolk/typora_images/raw/master/img/css_%E5%85%83%E7%B4%A0%E7%9A%84%E5%B1%82%E5%8F%A0.png)

    - z-index用于设置定位元素的层叠顺序（仅对定位元素有效）
    - 取值可以是正整数、负整数、0
    - z-index越大，层叠在上面

39. CSS的浮动属性

    - 可以通过float让元素产生浮动效果，float的常见取值：

      - none：不浮动，默认值
      - left：向左浮动
      - right：向右浮动

    - 规则一：元素一旦浮动，会脱离标准流向左或向右移动，直到边界紧贴包含块（父元素）或其他浮动元素的边界为止；定位元素会层叠在浮动元素上面；

    - 规则二：浮动元素不能与行内级内容层叠，行内级内容将被浮动元素推出；利用该特性可以实现文字浮动效果；

    - 规则三：行内级元素、inline-block元素浮动之后，其顶部将与其所在行的顶部对齐；只会在当前行浮动；

    - 规则四：浮动元素之间不能层叠；后浮动的元素将会紧贴着前一个浮动的元素；如果水平方向剩余空间不够显示浮动元素时，浮动元素将向下移动，直到有充足的空间；

    - 规则五：浮动元素的顶端不能超过包含块的顶端，也不能超过之前所有浮动元素的顶端（要和最低位置的浮动元素一样高）；

    - 浮动的应用：

      - 解决行内级元素、inline-block元素的水平间隙问题
      - 布局

    - 浮动时最后一个元素的margin多余的处理办法：

      - 通过伪类选择器去除每行最后一个元素的margin

      - 通过之间包裹一个元素，设置负的margin，增加最后一个元素的宽度

        ```css
        .container固定宽度 > .wrap + 负的margin >多个item
        ```

    - 浮动布局时，每个元素都会边框，会存在边框重叠的问题
      - 将某个元素向左或向右移动边框的粗细长度，使得两个边框变成一个边框

40. BFC(block format context)

- 如何触发BFC
  - 浮动
  - 设置一个元素的overflow为非visible的某个属性



