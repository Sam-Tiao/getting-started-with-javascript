
###### 题外话
迟来了两周的作业。   
上周旅游，周末和周一二都去了外地。   
本想着，背电脑去，晚上有时间敲敲代码。   
但又想：出去玩，还背电脑，夜里又"啪啪啪"键盘，貌似也不对劲。   
结果没带，好后悔。   
晚上，看群里讨论得热闹，只能干看，(⊙﹏⊙)   b，想敲敲代码，拿着手机很不舒服，于是放弃，觉得自己做错了选择。   
教训：电脑外出要背着，不能嫌沉，不能在意别人的眼光，不论走到哪里，都要时刻准备着——敲代码。   

Ps:因为作业是听了老师后来讲的，还有周五补的课程，加持了这三节课的威力，我对代码的执行的理解有了质的提升，^^(我感觉)。   

---
## 一、lesson5 sample代码的解析
这2周老师，带领我们这群小白，理解函数。   
虽然老师讲了那么多，但对异步、直接返回，我依然有些懵，不过也稍微理解了一些。   


### 从函数的定义开始
函数是啥，就是你给它一个参数，它经过特殊处理，返回结果的算式。   
所以一个函数里面有3个很重要的元素（函数名也很重要）：
1. 参数
2. 表达式（算式）
3. 返回的结果

这三个元素，针对不同情况，就分出来很多不同类型的函数。

**回调函数**
假如，一个函数A的参数B，不是一个值，而是其他的一个函数，即函数A的参数B **是一个函数**。   
那么，B是回调函数。   
当运行A的时候，运行到了需要用到B时，会跳到B里面，运行B，得出一个结果，再返回到A里面继续运行。   

**异步函数和直接返回**   
这是针对返回情况，而产生出的两种不同函数。   
直接返回的函数是，当你运行到了这个函数时，必须要等待这个函数给出一个结果，它才运行下一行，否则它就会一直卡在那里。   
异步函数呢，当电脑运行到了异步函数这一行时，会先跳过它，运行它之后的代码，当异步函数运行完了之后，返回一个结果。电脑不会卡在那一行。   


### 作业2 name变量有什么差异？
```
1. function output(name) {
2.     console.log(name);
3. }

4. var name = 'Hello,JS';
5. output(name);
```
第一行的name,是函数output()   的参数，name作为参数变量，并无实际意义，name也可以是a，b，c……   
然后，第二行的命令是把参数变量name打印到屏幕上。   
此时，都是在定义函数output()。   
然后第4行，是声明了一个变量，定义变量名为name,并赋值它name = 'Hello,Js'，是个字符串,此时name是变量，是有意义的;   
然后，把name这个变量传给了函数output(),运行output(name);   


### 做菜函数解析
粗看之下，老师一直使用callback回调函数，但找了半天也没有找到定义callback函数的语句，试运行了下老师的代码，居然是还没有准备好……后来我又运行了一次，发现又多了一行,后来过了很久，又看时，居然成功了，(⊙﹏⊙)b。   
![](http://othyo5zr8.bkt.clouddn.com/17-9-2/99985079.jpg)
![](http://othyo5zr8.bkt.clouddn.com/17-9-2/66115860.jpg)

好吧，如果是上周，我傻了，而且束手无策，现在是有些懵，不过幸好是听过了周五的补课，有解决方法。   

##### 查找原因
代码的上半截都是定义函数，执行是从调用开始。   
```
startWork(); // 是最开始执行的函数,找到它。

// 然后startWrok()执行，

function startWork() {
  var success = prepare();

  if (!success) { 
    console.log('还没准备好');
    return;
  }   // 不懂!success是什么意思。
```

![](http://othyo5zr8.bkt.clouddn.com/17-9-2/21540839.jpg)

只执行到了if语音，因为if函数里面有一个return，也就是直接结束了startWork()函数，所以第一次运行是，运行了if里面的语句，(!success)成立了；  
但是第2次运行之后，发现if语句不成立了，(⊙﹏⊙)b，就几秒的时间。
![](http://othyo5zr8.bkt.clouddn.com/17-9-2/85398330.jpg)
好吧，究其原因，是因为不懂!succsss是什么意思。
一开始不成立，后来又成立了，翻了同学的作业，又百度了一下。
发现，!success 是指 success !== true，即success是false时，就执行if语句。
回看，prepare()函数，里面有一个随机函数。好吧，故而success时而成立，时而不成立。
这个解决后，继续看下去。

##### 第二个难点。
当preapre()函数是ture时，执行了buyFoods()函数。
```
  buyFoods(function(foodsList) {
    cooking(foodsList, function(feast) {
      console.log('----酒席准备好了----');
      for (var i = 0; i < feast.length; i++) {
        console.log(feast[i]);
      }
    });
  });
```
找到buyFoods()函数，它的变量是一个回调函数:callback();
先执行第一行：
```
function buyFoods(callback) {
  console.log('我要开始采购食物啦。。。。');

  // 模拟5秒后通过callback返回结果
  setTimeout(function() {
    console.log('采购完毕');
    var foodsList = ['fish', 'egg', 'meat'];
    callback(foodsList);
  }, 5000);
}
```

接下来是一个setTimeout()函数，是异步函数，跳过它，bufFoods()函数先放一边，先执行其他代码。
执行了53行的代码：
```console.log('事情安排好了，我去洗个澡')```
等待setTimeout生效,执行setTimeout()里面的语句。
* 第7行代码；
* 第8行代码，赋值foodsList;
* 第9行代码，同时执行有参数的回调函数callback(foodsList),找callback()函数的表达式；
* 第44行代码是callback()函数的表达式，是直接写在了buyFoods()函数的括号里面的； 
> 一开始我找了好久没有找到callback()的表达式，后来又看了一眼命令行，发现就在buyFoods()函数括号里面，只是没有命名成callback()而已。
* 执行45行，执行cooking()函数，找到定义cooking()的代码，第20行。
* 执行21行。
* 执行24行，又是异步函数setTimeout()，跳过它，但之后没有语句了，等它生效;
* 执行25行。
* 执行26行。
* 执行28行，赋值feast = ['鸡蛋西红柿'，'红烧肉'，'红烧鱼']；
* 执行有了feast参数的29行callback(feast)函数，找到callback()的表达式，又是直接被写在了cooking()函数里面。
* 执行46行。
```console.log('---酒席准备好了----')；```

* 执行47,48行代码，是一个for循环语句，批量打印出feast里面的内容，就是feast = ['鸡蛋西红柿'，'红烧肉'，'红烧鱼']。

然后就结束了。

^^蛮辛苦，好难。
但是很兴奋，执行得蛮顺利，克服了2个困难……给老师比心~
^^