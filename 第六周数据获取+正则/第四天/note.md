1. exec：每次只能返回一个值；默认情况下，这个值是个数组，这个数组只有三项
    + 大正则匹配的内容
    + 索引
    + 原始字符串
 当我们有小分组的时候，小分组从数组的第二项开始，索引和原始字符串永远都在最后两位；
2. replace:
    + replace中的回调函数，默认接收三个参数，如果有小分组，arguments的长度会扩充；
    回调函数中参数的实现原理，跟exec一样；
3. replace回调函数中第一个参数的运用：敏感词过滤
4. replace回调函数中第2个参数的运用:把数字作为数组的索引，找到对应的值；
5. 重复子项 /\w(\w)(\w)\1\2/
   \1:跟第一个小分组内容一模一样；
   \2:跟第2个小分组内容一模一样；
6. 统计出现次数最多的单词：
   思路1：
        1） 利用对象不重名的特性
        2） 假设法
        3） 字符串拼接
   思路2：
        1）字符串排序：字符串转数组-数组排序-数组转字符串
        2）假设法+重复子项 /(\w)\1+/gi;
7.解析URL地址： /([^&?=]+)=([^&?=]+)/g;
8.日期格式化：
  重点，字符串转成数组，三种思路：
  1）严格匹配；
 ```
 var reg=/^(\d{4})[/-](\d{2})[/-](\d{2}) (\d{2}):(\d{2}):(\d{2})$/;
     var ary=null;
     str.replace(reg,function(){
         ary=Array.prototype.slice.call(arguments,1,arguments.length-2)
     });
 ```
   2) split 切
   var ary=str.split(/[^\d]+/g);
   3) match 捕获
   var ary=str.match(/\d+/g);
9 ?的用法
    1） 0或1
    2） 解决正则捕获的贪婪性 +?
    3） 只匹配不捕获 (?:\d+)
10 小括号的用法：
    1）分组
    2）提高优先级
    3）只匹配不捕获 (?:\d+)
11 var reg=new RegExp();
12 在有全局g的情况下，能影响lastIndex的值的属性有两个：
    1）reg.test()
    2) reg.exec()
13 回调函数需要注意的几点：
1）回调函数被调用的次数；比如，map中回调函数被调用的次数，取决于数组的长度
2）回调函数是否需要传参；比如，map中回调函数接收三个参数 1.item 2.index 3.input
3）回调函数中this默认指向window，可以通过call来改变this指向；
4）回调函数是否有返回值；比如 forEach()没有返回值； map()有返回值，他是把每个回调函数的返回值保存在一个数组中，最后返回出map;

14 考试的内容：
1）表格排序
2）日期格式化   urlParse
3）map()




