---
output:
  html_document: default
  pdf_document: default
---

# 名字和取值 {#sec:name-value}



## 本章概览

R中最重要的是了解对象和名字之间的区别：

   - 更准确的预测代码的性能和内存使用情况。
   - 通过避免意外复制（这是程序运行慢的主要原因）来编写更快的代码。
   - 更好的了解R的函数式编程工具。
   
## 绑定基础


```r
x <- c(1, 2, 3)
```

对于以上代码，我们通常的理解为，“建立一个名为‘x’的变量，包含值1、2和3。”但这其实是一种简化，并不能准确的预测R语言背后的实际操作。

准确的说，以上代码做了如下两个工作：

1. 创建一个对象，值向量`c(1, 2, 3)`，

2. 并将该对象绑定到名字x。

::: {.rmdtip data-latex="{提示}"}
- 通俗的讲，上例中的对象（或取值）并没有名字，代码实际上是生成了一个具有具体取值的名字。

- 名字x可以理解为，是对值`c(1, 2, 3)`的引用。

- lobstr::obj_addr()函数可以访问对象的标识符。
:::


```r
# 通过多种方式访问函数，实际上均指向同一个的函数。
obj_addr(mean)
```

```
## [1] "0x147179f0"
```

```r
obj_addr(base::mean)
```

```
## [1] "0x147179f0"
```

```r
obj_addr(get("mean"))
```

```
## [1] "0x147179f0"
```

## 复制后修改


```r
x <- c(1, 2, 3)
y <- x
y[[3]] <- 4
x
```

```
## [1] 1 2 3
```

```r
obj_addr(x)
```

```
## [1] "0x224cc608"
```

```r
obj_addr(y)
```

```
## [1] "0x2257f1a8"
```

上述代码首先将名字x、y绑定至同一取值，然后对y的第三个值进行变更。上述代码的结果表明：

   - 对y的修改并不会对x产生影响，即原始的对象（值）并没有改变，取而代之的操作是，R创建了一个新的对象，并对其中的值进行修改。
   - 这个行为在R中叫做**复制后修改（copy-on-modify）。**
   - 这个行为表明了R中的对象是不可更改或不可变的。

### 查看何时复制

使用`base::tracemem()`查看何时复制对象。


```r
x <- c(1, 2, 3)
cat(tracemem(x), "\n")
```

```
## <00000000228DED28>
```

```r
y <- x
y[[3]] <- 4L # 运行此代码可以看到复制的过程。
```

```
## tracemem[0x00000000228ded28 -> 0x00000000229de1e8]: eval eval eval_with_user_handlers withVisible withCallingHandlers handle timing_fn evaluate_call <Anonymous> evaluate in_dir in_input_dir eng_r block_exec call_block process_group.block process_group withCallingHandlers process_file <Anonymous> <Anonymous> do.call eval eval eval eval eval.parent local
```
