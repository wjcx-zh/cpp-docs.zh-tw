---
title: 委派建構函數 (C++)
description: 在C++中使用委派構造函數來調用其他構造函數並減少代碼重複。
ms.date: 11/19/2019
ms.openlocfilehash: f26a013aa3c081d900ffc3eb32649acc77505db0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316664"
---
# <a name="delegating-constructors"></a>委派建構函式

許多類別有多個執行類似操作的建構函數,例如,驗證參數:

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

您可以通過添加執行所有驗證的函數來減少重複代碼,但如果一個構造函數可以將某些工作委託給`class_c`另一個構造函數,則代碼更易於理解和維護。 要新增委派建構函數,請使用語法`constructor (. . .) : constructor (. . .)`:

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

在遍歷前面的範例中,請注意建構函數`class_c(int, int, int)`首先呼叫式函數,而建構函數`class_c(int, int)`又呼`class_c(int)`叫 。 每個構造函數只執行其他構造函數未執行的工作。

調用物件的第一個構造函數將初始化該物件,以便此時為其所有成員初始化。 不能在委託給其他構造函數的構造函數中執行成員初始化,如下所示:

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

下一個範例顯示了非靜態數據成員初始化器的使用。 請注意,如果建構函數還初始化給定的資料成員,則成員初始化器將被覆蓋:

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

建構函數委派語法不會阻止意外創建構造函數遞歸 — 構造函數1 調用構造函數2,調用構造函數 1 — 並且在存在堆疊溢出之前不會引發任何錯誤。 你有責任避免迴圈。

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
