---
title: 編譯器警告 (層級 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: afca92602aa6033c56869d3f84192ca0f029a23e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218113"
---
# <a name="compiler-warning-level-4-c4127"></a>編譯器警告 (層級 4) C4127

> 條件運算式是常數

## <a name="remarks"></a>備註

**`if`** 語句或迴圈的控制運算式會 **`while`** 評估為常數。 由於常見的慣用使用方式，從 Visual Studio 2015 update 3 開始，簡單的常數（例如1或） **`true`** 不會觸發警告，除非它們是運算式中的作業結果。

如果迴圈的控制運算式 **`while`** 是常數，因為迴圈會在中間結束，請考慮 **`while`** 以迴圈取代迴圈 **`for`** 。 您可以省略迴圈的初始化、終止測試和迴圈增量 **`for`** ，這會使迴圈成為無限的，就像一樣 `while(1)` ，您也可以從語句的主體結束迴圈 **`for`** 。

## <a name="example"></a>範例

下列範例顯示兩種產生 C4127 的方式，並示範如何使用 for 迴圈來避免此警告：

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

當在條件運算式中使用編譯時間常數時，也會產生這個警告：

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```
