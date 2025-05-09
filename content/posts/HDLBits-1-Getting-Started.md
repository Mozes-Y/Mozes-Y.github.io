+++
date = '2022-07-11T22:24:23+08:00'
draft = false
title = 'HDLBits 1 --Getting Started'
+++

---
title: HDLBits 1 --Getting Started
category:
  - HDLBits
tags:
  - Verilog
  - Digital Design
date: 2022-07-11 22:24:23
---
暑假闲来无事，作为一个微电子人，当然是要学习数字电子设计相关的东西啦，所以先来学习一波Verilog，作为学习Verilog最好的网站之一（个人觉得其实是最好的( •̀ ω •́ )✧），刷[HDLBits](https://hdlbits.01xz.net/wiki/Main_Page)当然是不二之选啦。

HDLBits基本分为几个大的模块，这篇是第一个大模块，也是开篇，其它的模块也会陆续更新的，希望能够完成吧，这里先开个新坑=￣ω￣=。

## Getting Started

### Getting started

这里这个小标题和大标题是一样的，作为强迫症患者有点不能忍受哈哈哈

这一小小篇章呢，基本上就是介绍了一下网站的大体内容和使用方法，并且有一道体验性质的Verilog题目来做一做。

题目呢是让输出一个恒为高的电平，也是非常的简单，并且大体框架都给了，所以呢直接填就行。

```verilog
module top_module( output one );

// Insert your code here
    assign one = [fixme];

endmodule
```

就是上面这道题了，我的答案如下

```verilog
assign one = 1'b1;
```

然后这一小节就完成了，进入下一个小节。

---

### Output Zero

这一小节呢，基本上还是体验性质的，说明了一下写代码时注意的事项以及支持的标准等等。

题目呢和标题一致，就是和前一节一样，输出一个低电平而已，所以呢也算是非常简单了

```verilog
module top_module(
    output zero
);// Module body starts after semicolon

endmodule
```

把答案填写在中间即可，预期是一行完成

```verilog
assign zero = 1'b0;
```

也是比较简单，那么这一个部分的内容就算结束了。

---

这一整个章节呢算是一个对整体的介绍吧，简单让我们体验一下做题的流程，以及告知一些注意事项吧。那么就进入下一个大的部分，正式开始Verilog语言的练习。
