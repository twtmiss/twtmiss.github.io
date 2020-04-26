# Java Collection 集合

[TOC]

## Collection

Java标准库自带的java.util包提供了集合类：Collection，它是除Map外所有其他集合类的根接口。Java的java.util包主要提供了以下三种类型的集合：

**List**：一种有序列表的集合

**Set**：一种保证没有重复元素的集合

**Map**：一种通过键值（key-value）查找的映射表集合

## List

### 简介

List集合代表一个元素有序、可重复的集合，集合中每个元素都有其对应的顺序索引。List集合允许使用重复元素，可以通过索引来访问指定位置的集合元素 。List集合默认按元素的添加顺序设置元素的索引，例如第一个添加的元素索引为0，第二个添加的元素索引为1......
List作为Collection接口的子接口，可以使用Collection接口里的全部方法。而且由于List是有序集合，因此List集合里增加了一些根据索引来操作集合元素的方法。

查看List\<E>接口，可以看到几个主要的接口方法：

- 在末尾添加一个元素：void add(E e)
- 在指定索引添加一个元素：void add(int index, E e)
- 删除指定索引的元素：int remove(int index)
- 删除某个元素：int remove(Object e)
- 获取指定索引的元素：E get(int index)
- 获取链表大小（包含元素的个数）：int size()

### ArrayList

#### ArrayList简介

ArrayList和Vector作为List类的两个典型实现，完全支持之前介绍的List接口的全部功能。
ArrayList和Vector类都是基于数组实现的List类，所以ArrayList和Vector类封装了一个动态的、允许再分配的Object[]数组。ArrayList或Vector对象使用initalCapacity参数来设置该数组的长度，当向ArrayList或Vector中添加元素超过了该数组的长度时，它们的initalCapacity会自动增加。

#### ArrayList的遍历方式

1. 通过迭代器遍历

```java
Integer value = null;
Iterator iter = list.iterator();
while (iter.hashNext()) {
    value = (Integer)iter.next();
}
```

2. 随机访问，通过索引值去遍历

由于ArrayList实现了RandomAccess接口，它支持通过索引值去随机访问元素。

```java
Integer value = null;
int size = list.size();
for (int i=0; i<size; i++) {
    value = (Integer)list.get(i);
}
```

3. for循环遍历

```java
Integer value = null;
for (Integer integ:list) {
    value = integ;
}
```

遍历ArrayList时，使用随机访问(即，通过索引序号访问)效率最高，而使用迭代器的效率最低。

### LinkedList

#### LinkedList简介

LinkedList类是List接口的实现类——这意味着它是一个List集合，可以根据索引来随机访问集合中的元素。除此之外，LinkedList还实现了Deque接口，可以被当作成双端队列来使用，因此既可以被当成“栈"来使用，也可以当成队列来使用。
LinkedList的实现机制与ArrayList完全不同。ArrayList内部是以数组的形式来保存集合中的元素的，因此随机访问集合元素时有较好的性能；而LinkedList内部以链表的形式来保存集合中的元素，因此随机访问集合元素时性能较差，但在插入、删除元素时性能比较出色。
由于LinkedList双端队列的特性，所以新增了一些方法。

LinkedList通过“链表”也实现了List接口。在LinkedList中，它的内部每个元素都指向下一个元素：

            ┌───┬───┐   ┌───┬───┐   ┌───┬───┐   ┌───┬───┐
    HEAD ──>│ A │ ●─┼──>│ B │ ●─┼──>│ C │ ●─┼──>│ D │   │
            └───┴───┘   └───┴───┘   └───┴───┘   └───┴───┘

#### LinkedList方法

```java
void addFirst(E e):将指定元素插入此列表的开头。
void addLast(E e): 将指定元素添加到此列表的结尾。
E getFirst(E e): 返回此列表的第一个元素。
E getLast(E e): 返回此列表的最后一个元素。
boolean offerFirst(E e): 在此列表的开头插入指定的元素。
boolean offerLast(E e): 在此列表末尾插入指定的元素。
E peekFirst(E e): 获取但不移除此列表的第一个元素；如果此列表为空，则返回 null。
E peekLast(E e): 获取但不移除此列表的最后一个元素；如果此列表为空，则返回 null。
E pollFirst(E e): 获取并移除此列表的第一个元素；如果此列表为空，则返回 null。
E pollLast(E e): 获取并移除此列表的最后一个元素；如果此列表为空，则返回 null。
E removeFirst(E e): 移除并返回此列表的第一个元素。
boolean removeFirstOccurrence(Objcet o): 从此列表中移除第一次出现的指定元素（从头部到尾部遍历列表时）。
E removeLast(E e): 移除并返回此列表的最后一个元素。
boolean removeLastOccurrence(Objcet o): 从此列表中移除最后一次出现的指定元素（从头部到尾部遍历列表时）。
```

#### LinkedList遍历方式

1.通过迭代器遍历LinkedList
2通过快速随机访问遍历LinkedList
3.通过for循环遍历LinkedList
4.通过pollFirst()遍历LinkedList
5.通过pollLast()遍历LinkedList
6通过removeFirst()遍历LinkedList
7.通过removeLast()遍历LinkedList
实现都比较简单，就不贴代码了。
其中采用逐个遍历的方式，效率比较高。采用随机访问的方式去遍历LinkedList的方式效率最低。

**LinkedList也是非线程安全的。**

### vector

#### Stack

Stack是Vector的子类，用户模拟“栈”这种数据结构，“栈”通常是指“后进先出”(LIFO)的容器。最后“push”进栈的元素，将被最先“pop”出栈

Stack与Vector一样，是线程安全的，但是性能较差，尽量少用Stack类。如果要实现栈”这种数据结构，可以考虑使用LinkedList。

---

## Set

**简介**

Set集合与Collection集合基本相同，没有提供任何额外的方法。实际上Set就是Collection，只是行为略有不同（Set不允许包含重复元素）。
Set集合不允许包含相同的元素，如果试图把两个相同的元素加入同一个Set集合中，则添加操作失败，add()方法返回false，且新元素不会被加入。

### HashSet

#### HashSet简介

HashSet是Set接口的典型实现，实现了Set接口中的所有方法，并没有添加额外的方法，大多数时候使用Set集合时就是使用这个实现类。HashSet按Hash算法来存储集合中的元素。因此具有很好的存取和查找性能。

#### HashSet特点

- 不能保证元素的排列顺序，顺序可能与添加顺序不同，顺序也有可能发生变化。
- HashSet不是同步的，如果多个线程同时访问一个HashSet，则必须通过代码来保证其同步。
- 集合元素值可以是null。
- 除此之外，HashSet判断两个元素是否相等的标准也是其一大特点。HashSet集合判断两个元素相等的标准是两个对象通过equals()方法比较相等，并且两个对象的hashCode()方法返回值也相等。

#### HashSet中判断集合元素相等

两个对象比较 具体分为如下四个情况：

1. 如果有两个元素通过equal()方法比较返回false，但它们的hashCode()方法返回不相等，HashSet将会把它们存储在不同的位置。

2. 如果有两个元素通过equal()方法比较返回true，但它们的hashCode()方法返回不相等，HashSet将会把它们存储在不同的位置。

3. 如果两个对象通过equals()方法比较不相等，hashCode()方法比较相等，HashSet将会把它们存储在相同的位置，在这个位置以链表式结构来保存多个对象。这是因为当向HashSet集合中存入一个元素时，HashSet会调用对象的hashCode()方法来得到对象的hashCode值，然后根据该hashCode值来决定该对象存储在HashSet中存储位置。

4. 如果有两个元素通过equal()方法比较返回true，但它们的hashCode()方法返回true，HashSet将不予添加。

HashSet判断两个元素相等的标准：**两个对象通过equals()方法比较相等，并且两个对象的hashCode()方法返回值也相等。**

**注意**：HashSet是根据元素的hashCode值来快速定位的，如果HashSet中两个以上的元素具有相同的hashCode值，将会导致性能下降。所以如果重写类的equals()方法和hashCode()方法时，应尽量保证两个对象通过hashCode()方法返回值相等时，通过equals()方法比较返回true。

#### LinkedHashSet类

LinkedHashSet是HashSet的子类，也是根据元素的hashCode值来决定元素的存储位置，同时使用链表维护元素的次序，使得元素是以插入的顺序来保存的。当遍历LinkedHashSet集合里的元素时，LinkedHashSet将会按元素的添加顺序来访问集合里的元素。但是由于要维护元素的插入顺序，在性能上略低与HashSet，但在迭代访问Set里的全部元素时有很好的性能。

**注意**：LinkedHashSet依然不允许元素重复，判断重复标准与HashSet一致。

补充：HashSet的实质是一个HashMap。HashSet的所有集合元素，构成了HashMap的key，其value为一个静态Object对象。因此HashSet的所有性质，HashMap的key所构成的集合都具备。可以参考后续文章中HashMap的相关内容进行比对。

### **TreeSet**

#### TreeSet简介

TreeSet是SortedSet接口的实现类，正如SortedSet名字所暗示的，TreeSet可以确保集合元素处于排序状态。此外，TreeSet还提供了几个额外的方法。

#### TreeSet的方法

- **comparator()**：返回对此 set 中的元素进行排序的比较器；如果此 set 使用其元素的自然顺序，则返回null。
- **first()**：返回此 set 中当前第一个（最低）元素。
- **last()**：返回此 set 中当前最后一个（最高）元素。
- **lower(E e)**：返回此 set 中严格小于给定元素的最大元素；如果不存在这样的元素，则返回 null。
- **higher(E e)**：返回此 set 中严格大于给定元素的最小元素；如果不存在这样的元素，则返回 null。
- **subSet(E fromElement, E toElement)**：返回此 set 的部分视图，其元素从 fromElement（包括）到 toElement（不包括）。
- **headSet(E toElement)**：返回此 set 的部分视图，其元素小于toElement。
- **tailSet(E fromElement)**：返回此 set 的部分视图，其元素大于等于 fromElement。

#### TreeSet的排序方式

TreeSet中所谓的有序，不同于之前所讲的插入顺序，而是通过集合中元素属性进行排序方式来实现的。
TreeSet支持两种排序方法：自然排序和定制排序。在默认情况下，TreeSet采用自然排序。

##### 自然排序

TreeSet会调用集合中元素所属类的compareTo(Object obj)方法来比较元素之间的大小关系，然后将集合元素按升序排列，即把通过compareTo(Object obj)方法比较后比较大的的往后排。这种方式就是自然排序。

Java的一些常用类已经实现了Comparable接口，并提供了比较大小的标准。例如，String按字符串的UNICODE值进行比较，Integer等所有数值类型对应的包装类按它们的数值大小进行比较。

除了这些已经实现Comparable接口类之外，如果试图把一个对象添加到TreeSet时，则该对象的类必须实现Comparable接口，否则就会出现异常。

注意：TreeSet中只能添加同一种类型的对象，否则无法比较，会出现异常。

**TreeSet中判断集合元素相等**
对于TreeSet集合而言，判断两个对象是否相等的唯一标准是：两个对象通过compareTo(Object obj)方法比较是否返回0——如果通过compareTo(Object obj)方法比较返回0，TreeSet则会认为它们相等，不予添加入集合内；否则就认为它们不相等，添加到集合内。
**TreeSet是根据红黑树结构找到集合元素的存储位置。**

2.定制排序
TreeSet的自然排序是根据集合元素中compareTo(Object obj)比较的大小，以升序排列。而定制排序是通过Comparator接口的帮助。该接口包含一个int compare(T o1,T o2)方法，该方法用于比较o1,o2的大小：如果该方法返回正整数，则表明o1大于o2；如果该方法返回0，则表明o1等于o2;如果该方法返回负整数，则表明o1小于o2。
如果要实现定制排序，则需要在创建TreeSet时，调用一个带参构造器，传入Comparator对象。并有该Comparator对象负责集合元素的排序逻辑，集合元素可以不必实现Comparable接口。下面具体演示一下这种用法：

```java
public static void main(String[] args){
        Person p1 = new Person();
        p1.age =20;
        Person p2 =new Person();
        p2.age = 30;
        Comparator<Person> comparator = new Comparator<Person>() {

            @Override
            public int compare(Person o1, Person o2) {
                //年龄越小的排在越后面
                if(o1.age<o2.age){
                    return 1;
                }else if(o1.age>o2.age){
                    return -1;
                }else{
                    return 0;
                }
                
            }
        };
        TreeSet<Person> set = new TreeSet<Person>(comparator);
        set.add(p1);
        set.add(p2);
        System.out.println(set);
    }
[Person[age=30], Person[age=20]]
```

总结：无论使用自然排序还是定制排序，都可以通过自定义比较逻辑实现各种各样的排序方式。

注意:如果向TreeSet中添加了一个可变对象后，并且后面程序修改了该可变对象的实例变量，这将导致它与其他对象的大小顺序发生了改变，但TreeSet不会再次调整它们。下面程序演示这一现象：

```
TreeSet<Person> set = new TreeSet<Person>();
        Person p1 = new Person();
        p1.setAge(10);
        Person p2 =new Person();
        p2.setAge(30);
        Person p3 =new Person();
        p3.setAge(40);
        set.add(p1);
        set.add(p2);
        set.add(p3);
        System.out.println("初始年龄排序");
        System.out.println(set);
        //p1的年龄修改成50 最大
        p1.age = 60;
        System.out.println("修改p1年龄后集合排序");
        System.out.println(set);
        p2.age = 40;
        System.out.println("修改p2年龄后集合排序");
        System.out.println(set);
        Person p4 = new Person();
```

其中Person实现Comparable接口，将Person对象按照年龄从小到大升序排列。
输出结果：

```
初始年龄排序
[Person[age=10], Person[age=30], Person[age=40]]
修改p1年龄后集合排序
[Person[age=60], Person[age=30], Person[age=40]]
修改p2年龄后集合排序
[Person[age=60], Person[age=40], Person[age=40]]
```

可以看到并没有发生变化，而且如果修改后进行元素删除操作可能会不成功，具体比较复杂。总之，推荐不要修改放入TreeSet集合中元素的关键实例变量。
补充：TreeSet也是非线程安全的。

### **EnumSet**

---

## **Map**

### **简介**

Map用户保存具有映射关系的数据，因此Map集合里保存着两组数，一组值用户保存Map里的key,另一组值用户保存Map里的value，key和value都可以是任何引用类型的数据。Map的key不允许重复，即同一个Map对象的任何两个key通过equals方法比较总是返回false。
如下图所描述，key和value之间存在单向一对一关系，即通过指定的key,总能找到唯一的、确定的value。从Map中取出数据时，只要给出指定的key，就可以取出对应的value。

### **HashMap**

### **HashTable**

### **TreeMap**

---

## **Queue**

### **简介**

Queue用户模拟队列这种数据结构，队列通常是指“先进先出”(FIFO，first-in-first-out)的容器。队列的头部是在队列中存放时间最长的元素，队列的尾部是保存在队列中存放时间最短的元素。新元素插入（offer）到队列的尾部，访问元素（poll）操作会返回队列头部的元素。通常，队列不允许随机访问队列中的元素。

---

## **集合常见面试题**

- ### Arraylist 与 LinkedList 异同

  - 是否保证线程安全： ArrayList 和 LinkedList 都是不同步的，也就是不保证线程安全；
  - 底层数据结构： Arraylist 底层使用的是Object数组；LinkedList 底层使用的是双向循环链表数据结构；
  - 插入和删除是否受元素位置的影响： ① ArrayList 采用数组存储，所以插入和删除元素的时间复杂度受元素位置的影响。 比如：执行add(E e)方法的时候， ArrayList 会默认在将指定的元素追加到此列表的末尾，这种情况时间复杂度就是O(1)。但是如果要在指定位置 i 插入和删除元素的话（add(int index, E element)）时间复杂度就为 O(n-i)。因为在进行上述操作的时候集合中第 i 和第 i 个元素之后的(n-i)个元素都要执行向后位/向前移一位的操作。 ② LinkedList 采用链表存储，所以插入，删除元素时间复杂度不受元素位置的影响，都是近似 O（1）而数组为近似 O（n）。
  - 是否支持快速随机访问： LinkedList 不支持高效的随机元素访问，而ArrayList 实现了RandmoAccess 接口，所以有随机访问功能。快速随机访问就是通过元素的序号快速获取元素对象(对应于get(int index)方法)。
  - 内存空间占用： ArrayList的空 间浪费主要体现在在list列表的结尾会预留一定的容量空间，而LinkedList的空间花费则体现在它的每一个元素都需要消耗比ArrayList更多的空间（因为要存放直接后继和直接前驱以及数据）。

- ### HashMap的底层实现

- ### ArrayList 与 Vector 区别

- ### HashMap 和 Hashtable 的区别

  - 线程是否安全： HashMap 是非线程安全的，HashTable 是线程安全的；HashTable 内部的方法基本都经过  synchronized  修饰。（如果你要保证线程安全的话就使用 ConcurrentHashMap 吧！）；
  
  - 效率： 因为线程安全的问题，HashMap 要比 HashTable 效率高一点。另外，HashTable 基本被淘汰，不要在代码中使用它；

  - 对Null key 和Null value的支持： HashMap 中，null 可以作为键，这样的键只有一个，可以有一个或多个键所对应的值为 null。。但是在 HashTable 中 put 进的键值只要有一个 null，直接抛出 NullPointerException。

  - 初始容量大小和每次扩充容量大小的不同 ：   ①创建时如果不指定容量初始值，Hashtable 默认的初始大小为11，之后每次扩充，容量变为原来的2n+1。HashMap 默认的初始化大小为16。之后每次扩充，容量变为原来的2倍。②创建时如果给定了容量初始值，那么 Hashtable 会直接使用你给定的大小，而 HashMap 会将其扩充为2的幂次方大小。也就是说 HashMap 总是使用2的幂作为哈希表的大小,后面会介绍到为什么是2的幂次方。

  - 底层数据结构： JDK1.8 以后的 HashMap 在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为8）时，将链表转化为红黑树，以减少搜索时间。Hashtable 没有这样的机制。
  
- ### HashSet 和 HashMap 区别

- ### ConcurrentHashMap 和 Hashtable 的区别

  - 底层数据结构： JDK1.7的 ConcurrentHashMap 底层采用 分段的数组+链表 实现，JDK1.8 采用的数据结构跟HashMap1.8的结构一样，数组+链表/红黑二叉树。Hashtable 和 JDK1.8 之前的 HashMap 的底层数据结构类似都是采用 数组+链表 的形式，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突而存在的；

  - 实现线程安全的方式（重要）： ① 在JDK1.7的时候，ConcurrentHashMap（分段锁） 对整个桶数组进行了分割分段(Segment)，每一把锁只锁容器其中一部分数据，多线程访问容器里不同数据段的数据，就不会存在锁竞争，提高并发访问率。（默认分配16个Segment，比Hashtable效率提高16倍。） 到了 JDK1.8 的时候已经摒弃了Segment的概念，而是直接用 Node 数组+链表+红黑树的数据结构来实现，并发控制使用 synchronized 和 CAS 来操作。（JDK1.6以后 对 synchronized锁做了很多优化）  整个看起来就像是优化过且线程安全的 HashMap，虽然在JDK1.8中还能看到 Segment 的数据结构，但是已经简化了属性，只是为了兼容旧版本；② Hashtable(同一把锁) :使用 synchronized 来保证线程安全，效率非常低下。当一个线程访问同步方法时，其他线程也访问同步方法，可能会进入阻塞或轮询状态，如使用 put 添加元素，另一个线程不能使用 put 添加元素，也不能使用 get，竞争会越来越激烈效率越低。
  
- ### ConcurrentHashMap线程安全的具体实现方式/底层具体实现