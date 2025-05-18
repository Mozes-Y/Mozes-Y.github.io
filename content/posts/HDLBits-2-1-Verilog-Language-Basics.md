+++
date = '2022-07-29T10:16:40+08:00'
draft = false
title = 'HDLBits 2.1 --Verilog Language ---Basics'
categories = ['HDLBits']
tags = ['Verilog', 'Digital Design']
+++

---
title: HDLBits 2.1 --Verilog Language ---Basics
category:
  - HDLBits
tags:
  - Verilog
  - Digital Design
date: 2022-07-29 10:16:40
---

从这一章开始就进入了正式的Verilog语法的学习，从这一章开始，每篇文章将会更新一个模块的内容，希望能够坚持更新完吧。

# Simple wire

第一个题目就是简单的一个连接的一个电路，将输入连接到输出，也就是说输出被输入驱动（我比较喜欢这个表达，可能有人喜欢称之为赋值，这都不重要 ¯\_(ツ)_/¯），一条assign语句就可以完成这道题。

```verilog
module top_module(
    input in,
    output out
);

    assign out = in;
    
endmodule

```

好了，这道题目就算是完成啦§(*￣▽￣*)§

# Four wires

这道题算是前一道题的小小升级版本吧，题目要求使用三个输入来驱动四个输出，写起来还是很简单的，下面是我的答案。

```verilog
module top_module (
	input a,
	input b,
	input c,
	output w,
	output x,
	output y,
	output z
);
	
	assign w = a;
	assign x = b;
	assign y = b;
	assign z = c;
	
endmodule

```

需要注意的一点是，这里四个语句的顺序前后并没有什么关系，这是非常重要的一点，因为Verilog是一个**硬件描述**语言，一定要铭记于心，非常重要，**你只是在描述电路间的电气连接的关系，并不是在写一门编程语言**，这是非常重要的，刚接触HDL的同学可能会习惯性的带着编程语言的思想来看待硬件描述语言，这是错误的。

当然上面的这道题还可以用连接符`{}`来做，当然这里题目的意思是让我们练习assign语句，连接符会在后面的章节中介绍和练习，感兴趣的同学可以自行查阅相关语法并尝试。

