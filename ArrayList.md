# Java 数组与列表基础操作

## 1. `int[] arr = new int[]{a, b, c};`

* **知识点：** 创建并初始化一个整数数组。
* **说明：** 在 Java 中，数组是固定大小的数据结构，可以存储相同类型的元素。可以使用 `new` 关键字和 `{}` 显式初始化数组，也可以直接使用 `{}` 进行简写初始化。
* **示例：**

    ```java
    int[] arr = new int[]{1, 2, 3};
    // 等价于简写形式：
    int[] arr2 = {1, 2, 3};

    System.out.println(arr[0]); // 输出: 1
    System.out.println(arr2[1]); // 输出: 2
    ```

## 2. `ArrayList<Integer> arr = new ArrayList<>();`

* **知识点：** 创建一个 `ArrayList` 动态数组。
* **说明：** `ArrayList` 是 Java 中的动态数组（实现了 `List` 接口），与固定大小的数组不同，它可以动态增加或减少元素。`<>` 内指定存储的元素类型（泛型），如 `Integer`、`String` 等。
* **示例：**

    ```java
    import java.util.ArrayList;

    ArrayList<Integer> arr = new ArrayList<>();
    arr.add(1); // 添加元素
    arr.add(2);
    arr.add(3);

    System.out.println(arr.get(0)); // 获取元素，输出: 1
    System.out.println(arr.size()); // 获取大小，输出: 3
    ```

## 3. `Arrays.equals(arr1, arr2)`

* **知识点：** 比较两个数组的内容是否相等。
* **说明：** `Arrays.equals()` 方法用于比较两个**数组**的内容是否完全相同，它会检查数组的长度以及每个索引位置上的元素值是否都相等。该方法适用于基本数据类型数组和对象数组（对象会使用其 `equals` 方法进行比较）。
* **示例：**

    ```java
    import java.util.Arrays;

    int[] arr1 = {1, 2, 3};
    int[] arr2 = {1, 2, 3};
    int[] arr3 = {1, 2, 4};

    System.out.println(Arrays.equals(arr1, arr2)); // 输出: true
    System.out.println(Arrays.equals(arr1, arr3)); // 输出: false
    ```

## 4. `Arrays.asList()` 创建列表

* **知识点：** 使用 `Arrays.asList()` 快速创建列表。
* **说明：** `Arrays.asList()` 可以方便地将一组元素或一个数组转换为 `List`。**重要：** 直接通过 `Arrays.asList(元素...)` 创建的 `List` 是一个**固定大小**的列表（底层是 `Arrays` 的一个私有静态内部类），不能进行添加 (`add`) 或删除 (`remove`) 操作，否则会抛出 `UnsupportedOperationException`。如果需要一个可变大小的 `ArrayList`，需要将其作为构造函数的参数传入。
* **示例：**

    ```java
    import java.util.Arrays;
    import java.util.List;
    import java.util.ArrayList;

    // 示例 1: 返回固定大小的 List
    List<Integer> fixedList = Arrays.asList(1, 2, 3, 4);
    System.out.println(fixedList.getClass()); // 输出: class java.util.Arrays$ArrayList
    // fixedList.add(5); // 这行会抛出 UnsupportedOperationException

    // 示例 2: 返回可变大小的 ArrayList
    List<Integer> variableList = new ArrayList<>(Arrays.asList(1, 2, 3, 4));
    System.out.println(variableList.getClass()); // 输出: class java.util.ArrayList
    variableList.add(5); // 操作成功
    System.out.println(variableList); // 输出: [1, 2, 3, 4, 5]
    ```

## 5. `System.arraycopy(src, srcPos, dest, destPos, length)`

* **知识点：** 高效复制数组内容。
* **说明：** `System.arraycopy()` 是一个本地方法（native），通常比手动循环复制数组元素效率更高。它用于将源数组的一部分或全部元素复制到目标数组的指定位置。
* **方法签名：**
    `arraycopy(Object src, int srcPos, Object dest, int destPos, int length)`
* **参数详解：**
    * `src (Object)`: 源数组，即你要从中复制数据的数组。
    * `srcPos (int)`: 源数组中的起始位置（索引），从这个位置开始复制数据。
    * `dest (Object)`: 目标数组，即你要将数据复制到的数组。目标数组必须已分配内存空间。
    * `destPos (int)`: 目标数组中的起始位置（索引），从这个位置开始存放复制过来的数据。
    * `length (int)`: 要复制的元素个数。
* **示例：**

    ```java
    int[] nums = {10, 20, 30, 40, 50};
    int n = 3; // 要复制的元素个数
    int[] res = new int[n]; // 目标数组

    // 从 nums 数组的索引 0 开始，复制 n 个元素到 res 数组，从 res 的索引 0 开始存放
    System.arraycopy(nums, 0, res, 0, n);

    // 打印目标数组内容
    System.out.println(Arrays.toString(res)); // 输出: [10, 20, 30]
    ```
