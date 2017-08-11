### JavaScript编程入门第一节课总结：学习JavaScript的最少必要知识

老师先后通过两个类比向我们展示了学习JavaScript的最少必要知识。

##### 第一个类比

用银行开户流程的优化过程类比出代码的执行流程，同时具体而形象的展示了编译型语言和解释性语言的区别。在这两种流程（银行开户和代码执行）中，真正重要的是（运行）环境。

JS的运行环境包含了内置库和V8引擎。当然，在这个运行环境之外，我们还需要第三方库（第三方服务）的支持。

而**在这个运行环境中更重要的**（对于新手，初级乃至中级学习者而言）**是其中的内置库**，而不是V8引擎（负责代码最终的执行）。

但是V8引擎恰好体现出了编译型语言和解释性语言的区别，编译型语言需要一个专门的编译器，经过编译器编译之后再送去执行，而解释性语言（JavaScript）的执行过程是边解释边执行，靠的就是V8引擎这个解释（执行）器。



##### 第二个类比

用婴儿和小学生的生活环境的区别类比出浏览器和Nodejs的运行环境的区别。它们之间最大的区别也是使用的内置库不相同，还有一部分是用到的第三方库不同。



##### 总结

通过这两个类比，可以总结出学习JavaScript的**最少必要知识**就是：

> - **运行环境中的内置库**
> - **第三方库**

而这两者（S的内置服务和第三方服务）也决定了我们学习JavaScript的正确方向：

> 1. 初学：**掌握编程语言**，用编程方式调用服务来完成你的需求。
> 2. 提高：**了解和掌握重要的服务能力**，使其能服务你的业务。
> 3. 进阶：善于比较服务/技术之间的差异性，**用最好的方式实现你的业务**。