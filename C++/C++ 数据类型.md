## 📦 基本数据类型

### 1. 整型
| 数据类型           | 占用空间  | 取值范围                    | 说明          |
| -------------- | ----- | ----------------------- | ----------- |
| `short`        | 2字节   | -32768 ~ 32767          | 短整型         |
| `int`          | 4字节   | -2^31 ~ 2^31-1 (约±21亿)  | 最常用的整型      |
| `long`         | 4/8字节 | -2^31 ~ 2^31-1 (或更大)    | 长整型（平台相关）   |
| `long long`    | 8字节   | -2^63 ~ 2^63-1 (约±9e18) | 超长整型(C++11) |
| `unsigned int` | 4字节   | 0 ~ 4294967295          | 无符号整型       |

```cpp
int age = 25;
unsigned int population = 8000000;
long long bigNum = 123456789012345LL;
```

### 2. 实型（浮点型）
| 数据类型  | 占用空间 | 取值范围             | 精度          | 说明       |
|-----------|----------|----------------------|---------------|------------|
| `float`   | 4字节    | ±3.4e-38 ~ ±3.4e38  | 7位有效数字  | 单精度浮点 |
| `double`  | 8字节    | ±1.7e-308 ~ ±1.7e308| 15位有效数字 | 双精度浮点 |
| `long double`| 8/16字节 | 更大范围             | 更高精度      | 扩展双精度 |

```cpp
float pi = 3.14159f;       // 注意加f后缀
double distance = 1.496e11; // 科学计数法
long double precise = 3.141592653589793238L;
```

### 3. 字符型
| 数据类型 | 占用空间 | 说明                          |
|----------|----------|-------------------------------|
| `char`   | 1字节    | 存储单个字符(-128~127)        |
| `wchar_t`| 2/4字节  | 宽字符（用于Unicode）         |
| `char16_t`| 2字节    | UTF-16字符(C++11)             |
| `char32_t`| 4字节    | UTF-32字符(C++11)             |

```cpp
char ch = 'A';         // 单引号表示字符
char newline = '\n';   // 转义字符
wchar_t wch = L'中';   // 宽字符前缀L
```

### 4. 字符串型
| 数据类型       | 说明                          | 头文件       |
|----------------|-------------------------------|--------------|
| C风格字符串    | `char str[]` 或 `char*`      | `<cstring>`  |
| `std::string`  | C++字符串类(推荐使用)         | `<string>`   |
| `std::wstring` | 宽字符串版本                  | `<string>`   |

```cpp
// C风格字符串
char name[] = "Alice"; 
const char* greeting = "Hello!";

// C++字符串
#include <string>
std::string message = "C++ is powerful!";
std::wstring wmessage = L"宽字符文本";
```

### 5. 布尔型
| 数据类型 | 占用空间 | 取值        | 说明                  |
|----------|----------|-------------|-----------------------|
| `bool`   | 1字节    | `true/false`| 布尔类型（真/假值）   |

```cpp
bool isReady = true;
bool isFinished = false;
```

## 🔍 sizeof 关键字
- 作用：获取数据类型或变量占用的内存大小（字节）
- 语法：`sizeof(数据类型)` 或 `sizeof(变量名)`

```cpp
cout << "int size: " << sizeof(int) << " bytes" << endl;     // 4
cout << "double size: " << sizeof(double) << " bytes" << endl; // 8

float num;
cout << "num size: " << sizeof num << " bytes" << endl; // 4
```

## 📥 数据输入（使用cin）
```cpp
#include <iostream>
using namespace std;

int main() {
    // 整型输入
    int age;
    cout << "Enter your age: ";
    cin >> age;

    // 浮点型输入
    double salary;
    cout << "Enter your salary: ";
    cin >> salary;

    // 字符输入
    char grade;
    cout << "Enter your grade: ";
    cin >> grade;

    // 字符串输入
    string name;
    cout << "Enter your name: ";
    cin >> name;  // 遇到空格会停止
    
    // 获取整行输入（包含空格）
    string fullName;
    cout << "Enter your full name: ";
    cin.ignore(); // 忽略之前输入的换行符
    getline(cin, fullName);

    // 布尔值输入(0为false，非0为true)
    bool employed;
    cout << "Are you employed? (0/1): ";
    cin >> employed;

    return 0;
}
```

### 输入注意事项：
1. `cin` 遇到空格、制表符、换行符会停止读取
2. 混合输入时注意缓冲区残留的换行符
3. 使用 `cin.ignore()` 清除缓冲区
4. 字符串输入推荐使用 `getline(cin, str)` 获取整行

## 数据类型选择建议
1. 整型：根据数值范围选择合适类型（默认用`int`）
2. 浮点型：精度要求不高用`float`，要求高用`double`
3. 布尔值：逻辑判断使用`bool`
4. 字符串：优先使用`std::string`而非C风格字符串

> 💡 提示：使用 `auto` 关键字可以让编译器自动推导变量类型（C++11）  
> 示例：`auto value = 3.14; // 自动推导为double类型`