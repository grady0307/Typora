# JavaScript

### 输入限制

- ~~~js
  //限制只能输入数字
  <input type="text" id="phonenumber" oninput="value=value.replace(/[^\d]/g,'')">
  ~~~

  

- parseInt(string, radix)

- parseInt() 函数可解析一个字符串，并返回一个整数。

  当参数 radix 的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。

  当忽略参数 radix , JavaScript 默认数字的基数如下:

  - 如果 string 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数。
  - 如果 string 以 0 开头，那么 ECMAScript v3 允许 parseInt() 的一个实现把其后的字符解析为八进制或十六进制的数字。
  - 如果 string 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数。

| string | 必需。要被解析的字符串。                             |
| ------ | ---------------------------------------------------- |
| radix  | 可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。 |

- Math.floor()下取整

- 返回介于 0（包含） ~ 1（不包含） 之间的一个随机数：

  Math.random();

- 修改文本域的值：

  `document.getElementById("myText").value = "Johnny Bravo";`

- ~~~
  setTimeout("changeState()",3000 );  
  function changeState(){  
  	let content=document.getElementById('content');  
  	content.innerHTML="<div style='color:red'>我是三秒后显示的内容！</div>";  
  }//延迟时间运行函数
  ~~~

- let声明的变量只在局部代码块有效

- 调试

  - 在控制台查看错误代码的位置
  - 可以通过console.log()输出查看变量的值
  - 设置断点F10逐句F8继续
  - debugger;也可以设置断点
  - 当然也可以在vscode中直接设置

- alert() 方法用于显示带有一条指定消息和一个 **确认** 按钮的警告框。

- window.history.back()

  - back() 方法可加载历史列表中的前一个 URL（如果存在）。

    调用该方法的效果等价于点击后退按钮或调用 history.go(-1)。
