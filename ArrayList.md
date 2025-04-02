## 1. `int[] arr = new int[]{a, b, c};`

*   **知识点：** 创建并初始化一个整数数组。
*   **说明：** 在 Java 中，数组是固定大小的数据结构，可以存储相同类型的元素。可以使用 `new` 关键字显式初始化数组，也可以直接使用 `{}` 进行初始化。
*   **示例：**

    ```java
    int[] arr = new int[]{1, 2, 3}; 
    // 等价于
    int[] arr2 = {1, 2, 3};

    System.out.println(arr[0]); // 输出: 1
    ```

## 2. `ArrayList<Integer> arr = new ArrayList<>();`

*   **知识点：** 创建一个 `ArrayList` 动态数组。
*   **说明：** `ArrayList` 是 Java 中的动态数组，存储的数据可以自动扩展，与固定大小的数组不同，它可以动态增加或减少元素。`<>` 内指定泛型类型，如 `Integer`、`String` 等。
*   **示例：**

    ```java
    import java.util.ArrayList;

    ArrayList<Integer> arr = new ArrayList<>();
    arr.add(1);
    arr.add(2);
    arr.add(3);

    System.out.println(arr.get(0)); // 输出: 1
    System.out.println(arr.size()); // 输出: 3
    ```

## 3. `Arrays.equals(arr1, arr2)`

*   **知识点：** 比较两个数组是否相等。
*   **说明：** `Arrays.equals()` 方法用于比较两个数组的内容是否完全相同，包括长度和对应索引的值。该方法适用于基本数据类型和对象数组。
*   **示例：**

    ```java
    import java.util.Arrays;

    int[] arr1 = {1, 2, 3};
    int[] arr2 = {1, 2, 3};
    int[] arr3 = {1, 2, 4};

    System.out.println(Arrays.equals(arr1, arr2)); // 输出: true
    System.out.println(Arrays.equals(arr1, arr3)); // 输出: false
    ```
4.List<Integer> list = Arrays.asList(1, 2, 3, 4);  // 返回固定大小的 List
List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3, 4));// 返回可变大小的 List
