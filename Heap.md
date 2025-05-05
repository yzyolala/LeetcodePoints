# Java PriorityQueue (堆) 使用指南

## 1. 为 `Map.Entry` 创建最小堆

* **知识点：** 创建一个基于 `PriorityQueue` 的最小堆。
* **说明：** `PriorityQueue` 是 Java 提供的一个基于堆的数据结构，默认是最小堆（按自然排序）。在这里，我们使用 `Comparator.comparingInt(Map.Entry::getValue)` 来自定义排序，使得堆按照 `Map.Entry` 的 `value` 值进行排序，始终保持最小值（`value` 最小的 Entry）在堆顶。
* **示例：**

    ```java
    import java.util.*;

    public class MinHeapExample {
        public static void main(String[] args) {
            // 创建一个按 Map.Entry 的 value 排序的最小堆
            PriorityQueue<Map.Entry<Integer, Integer>> minHeap =
                new PriorityQueue<>(Comparator.comparingInt(Map.Entry::getValue));

            // 创建一些映射项并加入最小堆
            Map<Integer, Integer> map = new HashMap<>();
            map.put(1, 10);
            map.put(2, 5); // 最小值
            map.put(3, 20);

            for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
                minHeap.add(entry);
            }

            // 获取堆顶元素 (值最小的 Entry)
            System.out.println("堆顶元素 Key: " + minHeap.peek().getKey() +
                               ", Value: " + minHeap.peek().getValue()); // 输出: Key: 2, Value: 5
        }
    }
    ```

## 2. `minHeap.size()`

* **知识点：** 获取堆中元素数量。
* **说明：** `size()` 方法返回 `PriorityQueue` 当前包含的元素数量。
* **示例：**

    ```java
    // 假设 minHeap 来自上一个示例
    System.out.println("当前堆大小: " + minHeap.size()); // 输出: 3
    ```

## 3. `minHeap.poll()` (不能用 `pop()`)

* **知识点：** 移除并返回堆顶元素（最小值）。
* **说明：** `poll()` 方法用于获取并移除堆顶元素（对于最小堆即最小值）。如果堆为空，则返回 `null`。（注意：`pop()` 是 `Stack` 的方法，`PriorityQueue` 实现的是 `Queue` 接口，标准移除方法是 `poll()`）。
* **示例：**

    ```java
    // 假设 minHeap 来自上一个示例
    Map.Entry<Integer, Integer> minEntry = minHeap.poll();
    System.out.println("移除的最小元素 Key: " + minEntry.getKey() +
                       ", Value: " + minEntry.getValue()); // 输出: Key: 2, Value: 5
    System.out.println("移除后堆大小: " + minHeap.size()); // 输出: 2
    ```

## 4. `minHeap.peek().getKey()`

* **知识点：** 访问 `Map.Entry` 最小堆堆顶元素的 Key。
* **说明：** `peek()` 方法返回当前堆顶元素但**不会**将其从堆中移除。接着，调用 `getKey()` 获取该 `Map.Entry` 对象的键（Key）。
* **示例：**

    ```java
    // 假设 minHeap 在移除了值为 5 的元素之后
    System.out.println("当前堆顶 Key: " + minHeap.peek().getKey()); // 输出: 1 (因为 {1, 10} 现在是堆顶)
    ```

## 堆创建模板

### 1. 最小堆创建模板

```java
// 默认就是最小堆（适用于自然排序类型，如 Integer）
PriorityQueue<Integer> minHeapDefault = new PriorityQueue<>();

// 使用 lambda 表达式显式声明（更清晰）
PriorityQueue<Integer> minHeapLambda = new PriorityQueue<>((a, b) -> a - b);

// 针对自定义对象（例如，按 Map.Entry 的 value 排序）
PriorityQueue<Map.Entry<Integer, Integer>> minHeapCustom =
    new PriorityQueue<>(Comparator.comparingInt(Map.Entry::getValue));
```

### 2. 最大堆创建模板

```java
// 使用 Comparator.reverseOrder() (推荐用于自然排序类型)
PriorityQueue<Integer> maxHeapReverse = new PriorityQueue<>(Comparator.reverseOrder());

// 或者使用 lambda 表达式
PriorityQueue<Integer> maxHeapLambda = new PriorityQueue<>((a, b) -> b - a);

// 针对自定义对象（例如，按 Map.Entry 的 value 降序排序）
PriorityQueue<Map.Entry<Integer, Integer>> maxHeapCustom =
    new PriorityQueue<>((a, b) -> b.getValue() - a.getValue()); // 也可使用 Comparator reversed()
```

### 3. **万能记忆口诀**

* **最小堆 (Min-Heap):** 默认就是 / `(a,b) -> a - b`
* **最大堆 (Max-Heap):** `reverseOrder()` / `(a,b) -> b - a`

## 特殊场景示例

### 按字符串长度排序

```java
// 最短字符串优先（按长度构建最小堆）
PriorityQueue<String> minStrHeap =
    new PriorityQueue<>(Comparator.comparingInt(String::length));

// 最长字符串优先（按长度构建最大堆）
PriorityQueue<String> maxStrHeap =
    new PriorityQueue<>((a, b) -> b.length() - a.length());
```

### 按自定义对象排序

```java
class Person {
    String name;
    int age;
    // 为简洁省略构造函数、getter/setter
    public Person(String name, int age) { this.name = name; this.age = age; }
    public int getAge() { return age; }
}

// 按年龄构建最小堆
PriorityQueue<Person> minAgeHeap =
    new PriorityQueue<>(Comparator.comparingInt(Person::getAge)); // 或 Comparator.comparingInt(p -> p.age)

// 按年龄构建最大堆
PriorityQueue<Person> maxAgeHeap =
    new PriorityQueue<>((a, b) -> b.age - a.age);
```
