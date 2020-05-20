# 基础知识
## 数据类型及其对象原型提供的方法
[typeof判断类型](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

        undefined : typeof instance === "undefined"
        Boolean   : typeof instance === "boolean"
        Number    : typeof instance === "number"
        String    : typeof instance === "string"
        BigInt    : typeof instance === "bigint"
        Symbol    : typeof instance === "symbol"
        null      : typeof instance === "object"
        Object    : typeof instance === "object"
        Function  : typeof instance === "function"
[instanceof判断Object的类名](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof)
                
        function Car(make, model, year) {
                this.make = make;
                this.model = model;
                this.year = year;
        }
        var mycar = new Car("Honda", "Accord", 1998);
        var a = mycar instanceof Car;    // 返回 true
        var b = mycar instanceof Object; // 返回 true，根据原型链顺着找

        var simpleStr = "This is a simple string"; 
        simpleStr instanceof String; // 返回 false, primitive type检查原型链会找到 undefined

        var myObj     = {};
        var myNonObj  = Object.create(null);
        myObj instanceof Object;    // 返回 true, 尽管原型没有定义
        myNonObj instanceof Object; // 返回 false, 一种创建非 Object 实例的对象的方法

[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)<br/>
- [CR: Carriage Return](https://blog.csdn.net/xiaoxian8023/article/details/8448160)
```
//回车"（carriage return）和"换行"（line feed）的区别和来历

关于“回车”（carriage return）和“换行”（line feed）这两个概念的来历和区别。
在计算机还没有出现之前，有一种叫做电传打字机（Teletype Model 33）的玩意，每秒钟可以打10个字符。但是它有一个问题，就是打完一行换行的时候，要用去0.2秒，正好可以打两个字符。要是在这0.2秒里面，又有新的字符传过来，那么这个字符将丢失。

于是，研制人员想了个办法解决这个问题，就是在每行后面加两个表示结束的字符。一个叫做“回车”，告诉打字机把打印头定位在左边界；另一个叫做“换行”，告诉打字机把纸向下移一行。

这就是“换行”和“回车”的来历，从它们的英语名字上也可以看出一二。

后来，计算机发明了，这两个概念也就被般到了计算机上。那时，存储器很贵，一些科学家认为在每行结尾加两个字符太浪费了，加一个就可以。于是，就出现了分歧。

Unix系统里，每行结尾只有“<换行>”，即“\n”；Windows系统里面，每行结尾是“<换行><回车>”，即“\n\r”；Mac系统里，每行结尾是“<回车>”。一个直接后果是，Unix/Mac系统下的文件在Windows里打开的话，所有文字会变成一行；而Windows里的文件在Unix/Mac下打开的话，在每行的结尾可能会多出一个^M符号。
```
- [UTF8编码](https://www.cnblogs.com/doublenet/p/5616451.html)
  
        // 将字符串格式化为UTF8编码的字节
        var writeUTF = function (str, isGetBytes) {
        var back = [];
        var byteSize = 0;
        for (var i = 0; i < str.length; i++) {
                var code = str.charCodeAt(i);
                if (0x00 <= code && code <= 0x7f) {
                        byteSize += 1;
                        back.push(code);
                } else if (0x80 <= code && code <= 0x7ff) {
                        byteSize += 2;
                        back.push((192 | (31 & (code >> 6))));
                        back.push((128 | (63 & code)))
                } else if ((0x800 <= code && code <= 0xd7ff) 
                        || (0xe000 <= code && code <= 0xffff)) {
                        byteSize += 3;
                        back.push((224 | (15 & (code >> 12))));
                        back.push((128 | (63 & (code >> 6))));
                        back.push((128 | (63 & code)))
                }
        }
        for (i = 0; i < back.length; i++) {
                back[i] &= 0xff;
        }
        if (isGetBytes) {
                return back
        }
        if (byteSize <= 0xff) {
                return [0, byteSize].concat(back);
        } else {
                return [byteSize >> 8, byteSize & 0xff].concat(back);
                }
        }

writeUTF('中'); // =>  [0, 3, 228, 184, 173] 
- 返回字符串中某个位置上的字符
  
        return 'cat'.charAt(1) // returns "a"
        return 'cat'[1] // returns "a"
- 返回字符串长度

        const str = 'Life, the universe and everything. Answer:';
        console.log(str + ' ' + str.length);
        // expected output: "Life, the universe and everything. Answer: 42"
- 字符串拼接
  
        let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable."
- 长字符串断行
  
        let longString = "This is a very long string which needs \
        to wrap across multiple lines because \
        otherwise my code is unreadable."

- 字符的ASCII码

                str="0";
                code = str.charCodeAt(0); //48
- [字串样版匹配](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
  
        let str = 'hello world!';
        let result = /^hello/.test(str);
        console.log(result); 
        // true
- [字串样版使用"组"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Groups_and_Ranges)
  
        const imageDescription = "This image has a resolution of 1440×900 pixels.";
        const regexpSize = /([0-9]+)×([0-9]+)/;
        const match = imageDescription.match(regexpSize);
        console.log(`Width: ${match[1]} / Height: ${match[2]}.`);
        // expected output: "Width: 1440 / Height: 900."
- [字串样版-非捕获型括号](https://blog.csdn.net/yangnianbing110/java/article/details/40321155)
  
        //non-capturing parentheses
        var regular = /^Subject:(?:\d)/
        var str = "Subject:1 as something";
        var result = regular.exec(str);
        alert(reslt[0])  //Subject:1
        alert(result[1]) //null
        //有些时候我们只需要测试表达是否可以匹配，而并不需要进行存储，可以通过非捕获型括号"(?:)"
        //https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions#Using_parentheses

- 判断字符串是否为非数字: 
        function milliseconds(x) {
                if (isNaN(x)) {
                        return 'Not a Number!';
                }
                return x * 1000;
        }

        console.log(milliseconds('100F'));
        // expected output: "Not a Number!"

        console.log(milliseconds('0.0314E+2'));
        // expected output: 3140
**注意：[isNaN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/isNaN)
**
1. Boolean的true会判断为数字1，false会判断为数字0
2. null '' "" 这些空值会判断为数字0
3. Date类型的值会判断为数字

Number
- n次方计算

        Math.pow(base, exponent) 
        **参数**
        base: 底的值
        exponent: 表达式的指数值
- 非整数的 Number 类型无法用 ==（=== 也不行） 来比较
        
        console.log( Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON);
- 指数(power)
  
                0.0314e2 //3.14
                .0618e1  //0.618
                .1e2     //10
                3.e-2    //0.03
- 小数(decimal)

                4.       //4.0
                .5       //0.5
                
[Boolean](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- 非
  
                let x = !(expression);
- 或
  
                let x = expression1 || expression2;
- 且
  
                let x = expression1 && expression2;

[null](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/null)
- 是否为null

                const m = 'sky'.match(/[aeiou]/gi);
                if (m === null) {
                        console.log(0); //0
                }
  
[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- 添加元素到数组末尾：push() ：返回值是新数组的长度
  
        let fruits = ['Apple', 'Banana']
        let newLength = fruits.push('Orange')
        // ["Apple", "Banana", "Orange"]
- 移除数组末尾元素：pop() : 返回值是最后一个元素
  
        let last = fruits.pop() // remove Orange (from the end)
        // ["Apple", "Banana"]
- 移除数组开头元素：shift()

        let first = fruits.shift() // remove Apple from the front
        // ["Banana"]
- 移除指定下标元素：splice(index, count)
  
        let myAry = [2, 5, 9]
        myAry.splice(-2, 1) // 删除倒数第二个开始的一个元素
        //[2, 9]
- 添加元素在数组开头：unshift()
  
        let newLength = fruits.unshift('Strawberry') // add to the front
        // ["Strawberry", "Banana"]
- 返回数组长度：length
  
        const fruits = []
        fruits.push('banana', 'apple', 'peach')
        console.log(fruits.length) // 3
- 遍历元素：forEach()
  
        let fruits = ['Apple', 'Banana']
        fruits.forEach(function(item, index, array) {
            console.log(item, index)
        })
        // Apple 0
        // Banana 1
- 切片: slice([begin[, end]]) ：返回begin到end-1 这一段Array

        const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
        
        console.log(animals.slice(2));
        // expected output: Array ["camel", "duck", "elephant"]
        console.log(animals.slice(2, 4));
        // expected output: Array ["camel", "duck"]
        console.log(animals.slice(-3, -1));
        // expected output: Array ['camel', 'duck']
- 返回值的下标
  
        const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];
        console.log(beasts.indexOf('bison'));
        // expected output: 1

        // start from index 2
        console.log(beasts.indexOf('bison', 2));
        // expected output: 4

        console.log(beasts.indexOf('giraffe'));
        // expected output: -1

- 拼接多个数组为一个：concat()
        
        const array1 = ['a', 'b', 'c'];
        const array2 = ['d', 'e', 'f'];
        const array3 = array1.concat(array2);
        
        console.log(array3);
        // expected output: Array ["a", "b", "c", "d", "e", "f"]
- 排序：sort()
  1. 默认排序（数字按小到大，字母按字母表顺序）
   
                const months = ['March', 'Jan', 'Feb', 'Dec'];
                months.sort();
                console.log(months);
                // expected output: Array ["Dec", "Feb", "Jan", "March"]
        
                const array1 = [1, 30, 4, 21, 100000];
                array1.sort();
                console.log(array1);
                // expected output: Array [1, 100000, 21, 30, 4]
  2. 汉字排序（非ASCII码）：汉字是拼音首字母

                var items = ['réservé', 'premier', 'communiqué', 'café', 'adieu', 'éclair'];
                items.sort(function (a, b) {
                        return a.localeCompare(b);
                });
                // items is ['adieu', 'café', 'communiqué', 'éclair', 'premier', 'réservé']

  3. 修改排序方法
   
                var arr = [[1, 2, 3], [7, 2, 3], [3, 2, 3]];
                arr.sort(function(x, y){
                          return x[0] – y[0];
                        }); // [[1, 2, 3], [3, 2, 3], [7, 2, 3]]
                // > 0 : x放到y的后面
                // = 0 : 不变
                // < 0 : x放y的前面
- 判断数组是几维数组
        
        var arr = [1,2,3,[1,2,3,1,3,[1,2,3,6,4,[1,2,3,1]]],2],a=1;
        function multiarr(arr){
		for (i=0;i<arr.length;i++){
			if(arr[i] instanceof Array){ //重点: instanceof Array
				a++;
				arr = arr[i];
				multiarr(arr);
			}
		}
		return a;
        }
        console.log(multiarr(arr)); // 4
- 计算数组中空格元素的个数: [map & reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
  
        ['', 'abc', '', '', 'efg'].map(
        function (x) {
            if (x === "") {
                return 1
            } else {
                return 0
            }
        }
    ).reduce(function (a, b) {
        return a + b
    })
    // 3
- 数组深拷贝
  
  1. 方式1：[slice()：返回一个新的数组，包含从 start 到 end](https://www.cnblogs.com/jiangzilong/p/6513552.html)
        
                arrCopy = arr.slice(0);
  
  2. 方式2:concat():返回被连接数组的一个副本

                arrCopy = arr.concat();
- [对象Object深拷贝](https://www.cnblogs.com/rusr/p/8984604.html)

        function copy(obj1,obj2){
                var obj2=obj2||{}; //最初的时候给它一个初始值=它自己或者是一个json
                for(var name in obj1){
                        if(typeof obj1[name] === "object"){ //先判断一下obj[name]是不是一个对象
                                obj2[name]= (obj1[name].constructor===Array)?[]:{}; //我们让要复制的对象的name项=数组或者是json
                                copy(obj1[name],obj2[name]); //然后来无限调用函数自己 递归思想
                        }else{
                                obj2[name]=obj1[name];  //如果不是对象，直接等于即可，不会发生引用。
                        }
                }
                return obj2; //然后在把复制好的对象给return出去
        }
        var json1={"name":"鹏哥","age":18,"arr1":[1,2,3,4,5],"string":'afasfsafa',"arr2":[1,2,3,4,5],"arr3":[{"name1":"李鹏"},{"job":"前端开发"}]};
        var json2={};

        json2=copy(json1,json2)
        json1.arr1.push(6);
        alert(json1.arr1);  //123456
        alert(json2.arr1);  //12345

- [判断对象Object是否为空](https://cloud.tencent.com/developer/article/1436302)
  
        var checkIsNull=function(obj){
                if(!obj){ //obj===null时，会转换为false，!obj即返回true
                        return true
                }else{ //obj==={}时，用如下判断是否为空
                        return Object.keys(obj).length === 0
                }
        }
---
## 流程控制语句b
for循环
- 退出当前循环或switch： break
  
        for(let i=1;i<=10;i++) { 
            if(i==8) { 
                break; 
            } 
            document.write(i); 
        } 
- 跳至循环的下一次：continue
  
        for(var i=1;i<=10;i++) { 
            if(i==8) { 
                continue; 
            } 
            document.write(i); 
        } 
- 退出当前函数：return
  
        for(var i=1;i<=10;i++) { 
            if(i==8) { 
                return; 
            } 
        document.write(i); 
        } 


