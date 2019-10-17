---
title: 編譯器警告 (層級 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: bef825f546573b878c415c385e1a2a2286e08db4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444899"
---
# <a name="compiler-warning-level-4-c4127"></a>編譯器警告 (層級 4) C4127

> 條件運算式是常數

## <a name="remarks"></a>備註

**If**語句或**while**迴圈的控制運算式會評估為常數。 由於其常見的慣用使用方式，從 Visual Studio 2015 update 3 開始，簡單的常數（例如1或**true** ）不會觸發警告，除非它們是運算式中的運算結果。

如果**while**迴圈的控制運算式是常數，因為迴圈會在中間結束，請考慮將**while**迴圈取代**為 for**迴圈。 您可以省略「 **for**迴圈」的初始化、終止測試和迴圈增量，這會使迴圈成為無限的，就像 `while(1)` 一樣，而且您可以從**for**語句的主體結束迴圈。

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