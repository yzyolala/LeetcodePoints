HashSet 适用于 去重、快速查找、集合运算。

常用方法：

add()：添加元素（去重）

remove()：删除元素

contains()：判断元素是否存在

size()：获取元素个数

clear()：清空集合

addAll()：合并集合

retainAll()：求交集

removeAll()：求差集

时间复杂度：

平均 O(1)，但哈希冲突严重时最坏可达 O(n)。
