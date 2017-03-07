##获取元素
 *  `document.getElementById`:
    语法：oElement = document .getElementById ( sID );
    参数：sID――必选项。字符串 (String) 。
    返回值：oElemen――对象 (Element) 。

说明：根据指定的 id 属性值得到对象。返回 id 属性值等于 sID 的第一个对象的引用。假如对应的为一组对象，则返回该组对象中的第一个。 如果无符合条件的对象，则返回 null 。
注意： document.getElementById(" ") 得到的是一个对象，用 alert 显示得到的是“ object ”，而不是具体的值，它有 value 和 length 等属性，加上 .value 得到的才是具体的值！
