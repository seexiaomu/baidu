## JS前端实现模糊查询
#### 字符串方法indexOf
```
var len = list.length;
var arr = [];
for(var i=0;i<len;i++){
    //如果字符串中不包含目标字符会返回-1
    if(list[i].indexOf(keyWord)>=0){
        arr.push(list[i]);
    }
}
return arr;
```
#### 正则表达式
```
var len = list.length;
var arr = [];
var reg = new RegExp(keyWord);
for(var i=0;i<len;i++){
    //如果字符串中不包含目标字符会返回-1
    if(list[i].match(reg)){
        arr.push(list[i]);
    }
}
return arr;
```
###### 模糊查询:就是根据关键字把列表中符合关键字的罗列出来（当然这里只做了最简单的），也就是要检查列表的每一项中是否含有关键字，因此抽象一下就是一个字符串中是否含有某个字符或者字符串。
