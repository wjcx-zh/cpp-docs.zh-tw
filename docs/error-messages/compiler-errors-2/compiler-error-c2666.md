---
title: 編譯器錯誤 C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: ca779269d573e3e5d270fccad6afe6220083fa42
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755989"
---
# <a name="compiler-error-c2666"></a>編譯器錯誤 C2666

' identifier '：數位多載具有類似的轉換

多載函數或運算子不明確。   型式參數清單可能太類似，編譯器無法解決不明確的問題。  若要解決這個錯誤，請明確地轉換一或多個實際參數。

下列範例會產生 C2666：

```cpp
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

針對 Visual Studio .NET 2003 進行的編譯器一致性工作，也可能產生此錯誤：

- 二元運算子和使用者定義的指標類型轉換

- 限定性轉換與身分識別轉換不同

針對二元運算子 \<、>、\<= 和 > =，如果參數的型別定義使用者定義的轉換運算子來轉換成運算元的型別，則傳遞的參數現在會隱含地轉換成運算元的型別。 現在有可能發生不明確的情況。

對於在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效的程式碼，請使用函式語法明確呼叫類別運算子。

## <a name="example"></a>範例

```cpp
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

## <a name="example"></a>範例

下列範例會產生 C2666

```cpp
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```
