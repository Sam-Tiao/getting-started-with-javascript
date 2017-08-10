#1. 类比代码执行流程
高级语言写的代码 > 编译后的中间代码  > 不同平台的机器码 > 机器指令
中央文件 > 官僚系统传递 > 各地根据当地情况做解读 > 群众去执行
#2. 运行环境
运行时需要的支撑环境，运行依赖的库。
#3. V8引擎
wiki解释
> V8在运行之前将JavaScript编译成了机器码，而非字节码或是解释执行它，以此提升性能。更进一步，使用了如内联缓存（inline caching）等方法来提高性能。有了这些功能，JavaScript程序与V8引擎的速度媲美二进制编译。
我的理解：v8引擎厉害的地方，方便代码书写的同时，没有降低代码执行的效率。
#4. 编译器/解释（执行）器 
编译器把高级语言编译为二进制文件，二进制文件加载到内存执行
解释器在运行时才进行代码的解析。
#5. 内置库
只有安装相应环境就包含的支持程序运行的最小代码库
#6. 第三方库
遵守相应规范开发的非官方代码库，实现官方库未实现的功能。库的质量由开发者能力决定。
#7. 学习JS的方向
基础语法+常用库+编程思想
