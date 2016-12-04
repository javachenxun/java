###java源码等级要求，(基于java version 1.8.0_60)
#1.精读源码（基本要求）
##1.1java.util
       这个包主要以集合为主，这是数据结构学习的最佳实践。
###1.1.1Map相关
- 这是集合中个人认为是最关键最复杂的类，搞清楚map的常用实现类是非常关键的对于认识集合总体的实现。
- 每个key，value键值对封装为Map.Entry<K, V> 实体bean。
####1.1.1.1HashMap
- 数据结构：Node实体数组（又叫Hash表或散列表，hash函数又叫散列函数）+ 单向链表+红黑树（又叫自平衡二叉查找树）。
- Node实体基本结构：hash,key,value,next(链表的下一个实体);Map.Entry<K, V> 实现类。
- TreeNode实体基本结构：parent,left,right,prev;TreeNode继承LinkedHashMap.Entry继承HashMap.Node<K,V>。
- 数组上的元素为链表（或红黑树）的头节点（或根节点）。
- 对于hash冲突解决办法使用链表（或红黑树），当链表长度大于等于8时转化为红黑树。之所以转化为红黑树是当数量大时红黑树的查询效率更高。
- 操作红黑树，增加删除后为了自平衡 进行的左右旋和重新着色。 
- 几种时间复杂度

|结构|  查询时间复杂度  |说明 |
|-- |  -------------- |---|
|hash表 |O（1）|       |
|链表 |  O（n）|遍历链表去查找 |
|红黑树 | O（log n）|  |
- 多线程下当共享变量使用时，扩容链表造成的问题

|jdk|  元素顺序 | 是否丢失|
|-- |  -------------- |  ------|
|1.7  | 倒置(易形成闭合回路) | 没验证|
|1.8  | 不倒置(99%的认为不会形成，1%再验证) |会丢失|
解决办法| 不当共享变量使用（在局部变量中 new创建 是没问题的，在栈中操作，属于私有的）或使用Collections.synchronizedMap(Map<K, V>)包装或使用ConcurrentHashMap |
#####1.1.1.2HashTable
#####1.1.1.3TreeMap
#####1.1.1.4LinkedHashMap
##1.2java.lang
##1.3java.io
#2.深刻理解（高级要求）
####java.lang.reflect
####java.net
####javax.net.*
####java.nio.*
####java.util.concurrent.*
#3.其他包会使用即可