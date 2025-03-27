##  `HashSet<Integer> set = new HashSet<>();`

*   **知识点：** 创建一个 `HashSet` 进行去重和快速查找。
*   **说明：** `HashSet` 是 Java 中的哈希集合，不允许存储重复元素，存取速度快，适用于 **去重** 和 **集合运算**。但它 **不保证元素顺序**，且 **不支持索引访问**。
*   **示例：**

    ```java
    import java.util.HashSet;

    HashSet<Integer> set = new HashSet<>();
    set.add(1);
    set.add(2);
    set.add(2); // 重复元素不会被加入
    set.add(3);

    System.out.println(set.contains(2)); // 输出: true
    System.out.println(set.size()); // 输出: 3
    ```

### **常用方法**
| 方法 | 说明 |
|------|------|
| `add(E e)` | 添加元素（自动去重） |
| `remove(E e)` | 删除元素 |
| `contains(E e)` | 判断元素是否存在 |
| `size()` | 获取集合大小 |
| `clear()` | 清空集合 |
| `addAll(Collection<? extends E> c)` | 合并集合（求并集） |
| `retainAll(Collection<?> c)` | 计算交集 |
| `removeAll(Collection<?> c)` | 计算差集 |

### **时间复杂度**
- **平均时间复杂度：** `O(1)`
- **最坏情况（哈希冲突严重时）：** `O(n)`


### **遍历 HashSet**
```java
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<Integer> set = new HashSet<>();
        set.add(1);
        set.add(2);
        set.add(3);

        // ✅ for-each 遍历
        for (int num : set) {
            System.out.println(num);
        }

        // ✅ 迭代器遍历
        System.out.println("使用迭代器：");
        var iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

        // ❌ 不能用索引访问
        // System.out.println(set.get(0)); // 报错：HashSet 没有 get(index) 方法
    }
}
