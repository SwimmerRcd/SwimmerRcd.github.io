# 问题描述
- 《重学前端》专栏的<b>JavaScript类型：关于类型，有哪些你不知道的细节?</b>这一课，谈到了语言类型有7种，分别为：<br/>
Undefined；Null；Boolean；String；Number；Symbol；Object。<br/>
但是我在看下面评论时，发现有人说还有Bigint。老师又推荐过MDN，于是我就在里面搜索DataTypes发现的确有Bigint，到底是谁在撒谎？

# 先上结果
- 2019年7月份以前，winter老师是对的，然后看了一下课程发布日期，是2019-01-26，所以，在winter老师发布这个课程时，这种说法还是对的。
- 但是，时代滚滚向前，情况发生了变化，从2019年7月份开始，这种说法就不成立了，因为Emacscript标准变了，新标准纳入了新的原始数据类型bigint，用于处理超过Number数字范围的数字。所以放在今天，这个说法是有问题的

# 破案过程
>
- 既然MDN已经被纳入怀疑对象的，当然不能以它为准。依葫芦画瓢，先上wikipedia，里面找到了[JavaScript syntax](https://en.wikipedia.org/wiki/JavaScript_syntax)里面提到了dataTypes，一看的确跟老师说的一样没有bigint，但是老师又说了，内容随便看看，重点看历史，但是也没找到历史，但是里面有个Origins，跟历史有点类似，里面提到了一个大牛Brendan Eich
- 接下来就要用google scholar了，可是，居然打不开！WTF，是我不配吗？试了几次都不行，算了，世上无难事，只要肯放弃。此路不通，只能绕道走了
- 于是我又google“Brendan Eich dataTypes"，出来一堆低质量的链接，放弃+1。回想起看MDN学到的一个高级词汇 primitive types，google "Brendan Eich primitive types"，出来Brendan Eich大牛的一篇javascript[设计备注](https://brendaneich.com/tag/languages/)，里面关于Type提到了ECMA-262，跟emacscript开头有点像，猜测应该是个语言标准。google一搜，还真是。oh yeah，曙光乍现，[Standard ECMA-262 - Ecma International](https://www.ecma-international.org/publications/standards/Ecma-262.htm),这个标准有两个版本，一个是ECMA-262第10版2019，里面说的还是跟winter老师一样，没有bigint。但是另外一个版本是[最新版](https://tc39.github.io/ecma262/)，打开一看，里面是由bigint的。为了验证，我又写段代码验证：
  
        console.log(Number.MAX_SAFE_INTEGER) // 9007199254740991
        let myBigInt = 2n ** 53n + 99998n // bigint就是数字后带个n
        console.log(myBigInt)          // 9007199254840990n
        console.log(typeof myBigInt)   // bigint
- 看到结果很明显，bigint类型是已经被实现了的，结案！