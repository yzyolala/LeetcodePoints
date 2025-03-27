## 1. `Map<String, Integer> map = new HashMap<>();`

*   **知识点：** 创建一个 `HashMap` 映射表。
*   **说明：** `Map` 是 Java 中的键值对集合，其中 `HashMap` 是最常用的实现之一。`HashMap` 允许存储 `null` 作为键或值，并且无序存储数据。
*   **示例：**

    ```java
    import java.util.HashMap;
    import java.util.Map;

    Map<String, Integer> map = new HashMap<>();
    map.put("Apple", 3);
    map.put("Banana", 5);
    map.put("Cherry", 2);

    System.out.println(map.get("Apple")); // 输出: 3
    System.out.println(map.containsKey("Banana")); // 输出: true
    System.out.println(map.containsValue(2)); // 输出: true
    ```

## 2. `map.get(key)`

*   **知识点：** 根据键获取对应的值。
*   **说明：** `get()` 方法用于根据键检索 `Map` 中存储的值。如果键不存在，则返回 `null`（或返回默认值）。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("Dog", 1);
    map.put("Cat", 2);

    System.out.println(map.get("Dog")); // 输出: 1
    System.out.println(map.get("Fish")); // 输出: null
    ```

## 3. `map.put(key, value)`

*   **知识点：** 向 `Map` 中添加键值对。
*   **说明：** `put()` 方法用于插入或更新 `Map` 中的键值对。如果键已存在，则更新对应的值。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("A", 10);
    map.put("B", 20);

    System.out.println(map.get("A")); // 输出: 10

    map.put("A", 30); // 更新键 "A" 的值
    System.out.println(map.get("A")); // 输出: 30
    ```

## 4. `map.containsKey(key)`

*   **知识点：** 判断 `Map` 是否包含指定的键。
*   **说明：** `containsKey()` 方法用于检查 `Map` 是否存在指定的键，返回 `true` 或 `false`。
*   **示例：**

    ```java
    Map<String, String> map = new HashMap<>();
    map.put("name", "Alice");

    System.out.println(map.containsKey("name")); // 输出: true
    System.out.println(map.containsKey("age")); // 输出: false
    ```

## 5. `map.containsValue(value)`

*   **知识点：** 判断 `Map` 是否包含指定的值。
*   **说明：** `containsValue()` 方法用于检查 `Map` 是否包含指定的值，返回 `true` 或 `false`。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("One", 1);
    map.put("Two", 2);

    System.out.println(map.containsValue(1)); // 输出: true
    System.out.println(map.containsValue(3)); // 输出: false
    ```

## 6. `map.remove(key)`

*   **知识点：** 删除 `Map` 中的键值对。
*   **说明：** `remove()` 方法用于删除 `Map` 中指定键的键值对。如果键存在，则返回删除的值；如果键不存在，则返回 `null`。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("X", 100);
    map.put("Y", 200);

    System.out.println(map.remove("X")); // 输出: 100
    System.out.println(map.containsKey("X")); // 输出: false
    ```

## 7. `map.keySet()`

*   **知识点：** 获取 `Map` 中所有的键。
*   **说明：** `keySet()` 方法返回 `Map` 中所有键的 `Set` 视图，可用于遍历 `Map` 的所有键。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("A", 1);
    map.put("B", 2);

    for (String key : map.keySet()) {
        System.out.println(key);
    }
    // 输出:
    // A
    // B
    ```

## 8. `map.values()`

*   **知识点：** 获取 `Map` 中所有的值。
*   **说明：** `values()` 方法返回 `Map` 中所有值的 `Collection` 视图，可用于遍历 `Map` 的所有值。
*   **示例：**

    ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("A", 10);
    map.put("B", 20);

    for (int value : map.values()) {
        System.out.println(value);
    }
    // 输出:
    // 10
    // 20
    ```

## 9. `map.entrySet()`

*   **知识点：** 获取 `Map` 中所有的键值对，并结合 `for` 循环进行遍历。
*   **说明：** `entrySet()` 方法返回 `Map` 中所有键值对的 `Set` 视图，可用于遍历 `Map` 的所有键值对。

*   **示例：**

    ```java
    Map<Integer, Integer> map = new HashMap<>();
    map.put(1, 10);
    map.put(2, 5);
    map.put(3, 20);

    for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
        System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
    }
    // 输出:
    // Key: 1, Value: 10
    // Key: 2, Value: 5
    // Key: 3, Value: 20
    ```

*   **进阶用法：** 在 `for` 循环中结合 `PriorityQueue` 进行操作，例如维护一个大小为 `k` 的最小堆。

    ```java
    for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
        minHeap.offer(entry); // 插入堆
        if (minHeap.size() > k) {
            minHeap.poll(); // 当堆大小超过 k 时，移除最小元素
        }
    }
    ```

*   **说明：**  
    - `for (Map.Entry<Integer, Integer> entry : map.entrySet())` 遍历 `Map` 的所有键值对。  
    - `minHeap.offer(entry)` 将元素插入 `PriorityQueue`（最小堆）。  
    - `if (minHeap.size() > k) minHeap.poll();` 确保 `PriorityQueue` 的大小始终保持在 `k`，即仅保留 `Map` 中 `value` 最大的 `k` 个元素。

