## 1. `s.length()`

*   **知识点：** 获取字符串的长度。
*   **说明：** `length()` 是 Java 中 `String` 类的一个方法，用于返回字符串的字符数（长度）。
*   **示例：**

    ```java
    String s = "Hello";
    int len = s.length(); // len 的值为 5
    ```

## 2. `StringBuilder st = new StringBuilder();`

*   **知识点：** 创建一个 `StringBuilder` 对象。
*   **说明：** `StringBuilder` 是 Java 中一个可变的字符串类，用于高效地拼接字符串。与 `String` 类不同，`StringBuilder` 对象的内容可以被修改，而不会创建新的对象。
*   **示例：**

    ```java
    StringBuilder st = new StringBuilder();
    st.append("Hello");
    st.append(" World");
    String result = st.toString(); // result 的值为 "Hello World"
    ```

## 3. `word1.charAt(s)`

*   **知识点：** 获取字符串中指定位置的字符。
*   **说明：** `charAt()` 是 `String` 类的一个方法，用于返回字符串中指定索引位置的字符。索引从 0 开始。
*   **示例：**

    ```java
    String word1 = "Hello";
    char c = word1.charAt(1); // c 的值为 'e'
    ```

## 4. `st.append(word2.charAt(s));`

*   **知识点：** 将字符追加到 `StringBuilder` 对象中。
*   **说明：** `append()` 是 `StringBuilder` 类的一个方法，用于将指定的字符或字符串追加到 `StringBuilder` 对象的末尾。
*   **示例：**

    ```java
    StringBuilder st = new StringBuilder();
    st.append('H');
    st.append('e');
    st.append('l');
    st.append('l');
    st.append('o');
    String result = st.toString(); // result 的值为 "Hello"
    ```

## 5. `word1.substring(s)`

*   **知识点：** 获取字符串的子串。
*   **说明：** `substring()` 是 `String` 类的一个方法，用于返回字符串的一个子串。它可以接受一个或两个参数：
    *   一个参数：表示子串的起始索引（包含）。
    *   两个参数：表示子串的起始索引（包含）和结束索引（不包含）。
*   **示例：**

    ```java
    String word1 = "Hello World";
    String sub1 = word1.substring(6); // sub1 的值为 "World"
    String sub2 = word1.substring(0, 5); // sub2 的值为 "Hello"
    ```

## 6. `word1.toCharArray()`

*   **知识点：** 将字符串转换为字符数组。
*   **说明：** `toCharArray()` 是 `String` 类的一个方法，用于将字符串的每个字符转换为一个 `char` 数组，便于遍历和修改。
*   **示例：**

    ```java
    String word1 = "Hello";
    char[] charArray = word1.toCharArray(); 
    // charArray 的值为 ['H', 'e', 'l', 'l', 'o']
    
    for (char c : charArray) {
        System.out.print(c + " "); // 输出: H e l l o
    }
    ```
## 7. `附加方法`

Character.isLetterOrDigit(): 判断指定字符是否为字母或数字。

Character.toLowerCase(): 将指定字符转换为小写。

Character.toUpperCase(): 将指定字符转换为大写。



