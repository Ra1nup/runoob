## 第一个 C 程序 - C 书写 HelloWorld

- **概述**：编写一个简单的 C++ 程序，输出 "Hello, World!"，这是学习 C++ 的入门示例。
- **代码实现**：

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```

- **解释**：
    - `#include <iostream>`：引入输入输出流库。
    - `using namespace std;`：使用标准命名空间，简化 `cout` 的调用。
    - `int main()`：程序入口，`return 0` 表示成功结束。
    - `cout << ... << endl;`：输出字符串并换行。

## 程序的注释 - 程序注释和多行注释

- **概述**：注释用于解释代码，提高可读性，不会被编译器执行。
- **类型**：
    - **单行注释**：`// 注释内容`，适用于短注释。
        - 示例：
            
            ```cpp
            int x = 10; // 初始化变量 x
            ```
            
    - **多行注释**：`/* 注释内容 */`，适用于长段说明。
        - 示例：
            
            ```cpp
            /* 这是一个
               多行注释示例 */
            int y = 20;
            ```
            
- **最佳实践**：
    - 在函数、复杂逻辑前添加注释。
    - 避免过度注释显而易见的内容。

## 变量 - 变量的使用 - 变量的定义

- **概述**：变量是程序中用于存储数据的命名空间，需先定义。
- **定义方式**：
    - 基本语法：`类型 变量名 = 值;`
    - 示例：
        
        ```cpp
        int age = 25;        // 整数
        float height = 1.75; // 浮点数
        char grade = 'A';    // 字符
        ```
        
- **规则**：
    - 变量名由字母、数字、下划线组成，不能以数字开头。
    - 区分大小写，如 `age` 和 `Age` 不同。
- **作用域**：
    - 局部变量：在函数内有效。
    - 全局变量：在文件级别有效。
- **相关笔记**：[[C++ 数据类型]]

## 常量 - 常量的使用 - 常量的定义

- **概述**：常量是固定不变的值，C++ 提供两种定义方式：const 和 #define。
    
- **使用** const **定义**：
    
    - 语法：const 类型 常量名 = 值;
        
    - 示例：
        
        ```cpp
        const int MAX_SIZE = 100;    // 整数常量
        const double PI = 3.14159;   // 浮点常量
        const char NEWLINE = '\n';   // 字符常量
        ```
        
    - **特点**：
        
        - 编译时类型检查，赋值后不可修改。
            
        - 具有作用域，遵循变量作用域规则。
            
        - 可调试（编译器可追踪）。
            
- **使用** #define **定义**：
    
    - 语法：#define 常量名 值
        
    - 示例：
        
        ```cpp
        #define MAX_SIZE 100
        #define PI 3.14159
        ```
        
    - **特点**：
        
        - 预处理器指令，在编译前替换所有 MAX_SIZE 为 100。
            
        - 无类型检查，纯粹文本替换。
            
        - 无作用域限制，定义后全局有效。
            
        - 不可调试（无符号信息）。
            

- **综合示例**：
    
    ```cpp
    #include <iostream>
    using namespace std;
    
    #define MAX 100
    const int MIN = 0;
    
    int main() {
        cout << "MAX: " << MAX << endl;  // 输出：MAX: 100
        cout << "MIN: " << MIN << endl;  // 输出：MIN: 0
        // MIN = 10; // 错误：const 不可修改
        return 0;
    }
    ```

- **相关笔记**：[[字符转义]]

## 关键字 - C++ 常用的关键字

- **概述**：关键字是 C++ 预定义的保留字，用于特定功能，不能作为变量名。
- **常见关键字**：
    - **数据类型**：`int`, `float`, `double`, `char`, `bool`
    - **控制结构**：`if`, `else`, `for`, `while`, `switch`
    - **函数相关**：`return`, `void`
    - **内存管理**：`new`, `delete`
    - **修饰符**：`const`, `static`, `auto`
- **示例使用**：
    
    ```cpp
    if (true) { // 使用关键字 if
        int x = 5; // 使用关键字 int
        cout << x << endl;
    }
    ```

下表列出了 C++ 中的保留字。这些保留字不能作为常量名、变量名或其他标识符名称。

| **asm**          | **else**      | **new**              | **this**     |
| ---------------- | ------------- | -------------------- | ------------ |
| **auto**         | **enum**      | **operator**         | **throw**    |
| **bool**         | **explicit**  | **private**          | **true**     |
| **break**        | **export**    | **protected**        | **try**      |
| **case**         | **extern**    | **public**           | **typedef**  |
| **catch**        | **false**     | **register**         | **typeid**   |
| **char**         | **float**     | **reinterpret_cast** | **typename** |
| **class**        | **for**       | **return**           | **union**    |
| **const**        | **friend**    | **short**            | **unsigned** |
| **const_cast**   | **goto**      | **signed**           | **using**    |
| **continue**     | **if**        | **sizeof**           | **virtual**  |
| **default**      | **inline**    | **static**           | **void**     |
| **delete**       | **int**       | **static_cast**      | **volatile** |
| **do**           | **long**      | **struct**           | **wchar_t**  |
| **double**       | **mutable**   | **switch**           | **while**    |
| **dynamic_cast** | **namespace** | **template**         |              |

## 标识符命名规则

**作用：** C++规定给标识符（变量、常量）命名时，有一套自己的规则。

- 标识符不能是关键字
	  
- 标识符只能由字母、数字、下划线组成
	  
- 第一个字符必须为字母或下划线
	  
- 标识符中字母区分大小写