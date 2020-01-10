---
title: 委派的函C++式（）
description: 在中使用委派C++的函式來叫用其他的函式，並減少程式碼重複。
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250671"
---
# <a name="delegating-constructors"></a>委派建構函式

許多類別都有多個執行類似專案的函式，例如，驗證參數：

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

您可以藉由新增可執行所有驗證的函式來減少重複的程式碼，但是 `class_c` 的程式碼會更容易瞭解和維護，如果一個函式可以將一些工作委派給另一個函式。 若要加入委派的函式，請使用 `constructor (. . .) : constructor (. . .)` 語法：

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

當您逐步執行前一個範例時，請注意，此函式 `class_c(int, int, int)` 會先呼叫 `class_c(int, int)`的函式，而該函式會接著呼叫 `class_c(int)`。 每個函式都只會執行其他函式未執行的工作。

第一個呼叫的函式會初始化物件，使其所有成員都在該點初始化。 您無法在委派給另一個函式的函式中執行成員初始化，如下所示：

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

下一個範例示範如何使用非靜態資料成員初始化運算式。 請注意，如果某個函數也初始化了指定的資料成員，則會覆寫成員初始化運算式：

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

「函式委派」語法不會防止意外建立的「函式遞迴」（Constructor1 會呼叫呼叫 Constructor1 的 Constructor2），而且不會擲回任何錯誤，直到發生堆疊溢位為止。 您必須負責避免迴圈。

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
