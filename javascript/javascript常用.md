# 基础知识
## 数据类型及其对象原型提供的方法
[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)<br/>
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
---
## 流程控制语句
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


