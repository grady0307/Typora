# Jqurey

- **DOM = Document Object Model（文档对象模型）**
- 引入
- 也可本地下载文件

<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
</script>

- 文件就绪代码

~~~js
$(document).ready(function(){
 
   // 开始写 jQuery 代码...
 
});
~~~

- 基础语法：$(selector).action()

- 选择器基于css  $("p")

  ```
  for(var i=0;i<4;i++)
  
    for(var j=0;j<4;j++){
  
     var gridCell = $("grid-cell-"+i+"-"+j);
  }
  //因为javascript只支持一维数组，要声明二维数组只能这么写个二重循环
  
  ```

  

- 添加新元素

  - append() - 在被选元素的结尾插入内容

    - $("p").append("追加文本");

  - prepend() - 在被选元素的开头插入内容

  - after() - 在被选元素之后插入内容

  - before() - 在被选元素之前插入内容

  - append/prepend 是在选择元素内部嵌入。

    after/before 是在元素外面追加。

- 对css的控制
  - 返回css属性`$("p").css("background-color");`
  - 设置css（多个）属性`$("p").css({"background-color":"yellow","font-size":"200%"});`

- DOM操作
  - **text()** - 设置或返回所选元素的文本内容`alert("Text: " + $("#test").text());`
  - **html()** - 设置或返回所选元素的内容（包括 HTML 标签）`alert("HTML: " + $("#test").html());`
  - **val()** - 设置或返回表单字段的值

- 动画效果

  - `$(*selector*).animate({*params*}*,speed,callback*);`必需的 params 参数定义形成动画的 CSS 属性。

    可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

    可选的 callback 参数是动画完成后所执行的函数名称。

  - 默认情况下，所有 HTML 元素都有一个静态位置，且无法移动。
    如需对位置进行操作，要记得首先把元素的 CSS position 属性设置为 relative、fixed 或 absolute！

    ~~~ js
    $("button").click(function(){
      $("div").animate({
        left:'250px',
        opacity:'0.5',
        height:'150px',
        width:'150px'
      });
    });

  - 使用相对值`height:'+=150px'`

- 按下键盘的响应 

  - 与 keydown 事件相关的事件顺序：
    1. keydown - 键按下的过程
    2. [keypress](https://www.runoob.com/jquery/event-keypress.html) - 键被按下
    3. [keyup](https://www.runoob.com/jquery/event-keyup.html) - 键被松开

  - **提示：**请使用 [event.which](https://www.runoob.com/jquery/event-which.html) 属性来返回哪个键盘键被按下。

  - `$("input").keydown(function(){    $("input").css("background-color","yellow"); });`

  - 或用enent.keyCode

  - ```js
    switch( event.keyCode ) {
        case $.ui.keyCode.LEFT:
          console.log( "left" );
          break;}
    ```

- event.preventDefault() 方法阻止元素发生默认的行为。

  例如：

  - 当点击提交按钮时阻止对表单的提交
  - 阻止以下 URL 的链接
  - `$("a").click(function(event){
      event.preventDefault();
    });`

- 显示和隐藏元素

  - $(*selector*).hide(*speed,callback*);

    $(*selector*).show(*speed,callback*);

  `$("#game-message").hide();`

  `$(":hidden").show(3000);`

- 点击方法`$(*selector*).click(*function*)`