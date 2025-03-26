## 1. `PriorityQueue<Map.Entry<Integer, Integer>> minHeap = new PriorityQueue<>(Comparator.comparingInt(Map.Entry::getValue));`

*   **知识点：** 创建一个基于 `PriorityQueue` 的最小堆。
*   **说明：** `PriorityQueue` 是 Java 提供的一个基于堆的数据结构，默认是最小堆（按自然排序）。在这里，我们使用 `Comparator.comparingInt(Map.Entry::getValue)` 来自定义排序，使得堆按照 `Map.Entry` 的 `value` 进行排序，始终保持最小值在堆顶。
*   **示例：**

    ```java
    import java.util.*;

    public class MinHeapExample {
        public static void main(String[] args) {
            PriorityQueue<Map.Entry<Integer, Integer>> minHeap =
                new PriorityQueue<>(Comparator.comparingInt(Map.Entry::getValue));

            // 创建一些映射项并加入最小堆
            Map<Integer, Integer> map = new HashMap<>();
            map.put(1, 10);
            map.put(2, 5);
            map.put(3, 20);

            for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
                minHeap.add(entry);
            }

            // 获取堆顶元素
            System.out.println("堆顶元素 Key: " + minHeap.peek().getKey() + 
                               ", Value: " + minHeap.peek().getValue()); // 输出: 2, 5
        }
    }
    ```

## 2. `minHeap.size()`

*   **知识点：** 获取最小堆的元素个数。
*   **说明：** `size()` 方法返回 `PriorityQueue` 当前包含的元素数量。
*   **示例：**

    ```java
    System.out.println("当前堆大小: " + minHeap.size()); // 输出: 3
    ```

## 3. `minHeap.poll()`

*   **知识点：** 移除并返回最小堆中的堆顶元素。
*   **说明：** `poll()` 方法用于获取最小值并将其从堆中移除。如果堆为空，则返回 `null`。
*   **示例：**

    ```java
    Map.Entry<Integer, Integer> minEntry = minHeap.poll();
    System.out.println("移除的最小元素 Key: " + minEntry.getKey() + 
                       ", Value: " + minEntry.getValue()); // 输出: 2, 5
    ```

## 4. `minHeap.peek().getKey();`

*   **知识点：** 获取最小堆堆顶元素的 `key`。
*   **说明：** `peek()` 方法返回当前堆顶元素但不会移除，`getKey()` 获取该元素的键值。
*   **示例：**

    ```java
    System.out.println("当前堆顶 Key: " + minHeap.peek().getKey()); // 输出: 1
    ```
