---
title: 編譯器警告 (層級 4) C4127
ms.date: 09/13/2018
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 7f1e23d15d8daa126987278611cb5a85a5a36fc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614431"
---
# <a name="compiler-warning-level-4-c4127"></a>編譯器警告 (層級 4) C4127

> 條件運算式是常數

## <a name="remarks"></a>備註

控制運算式**如果**陳述式或**雖然**迴圈會評估為常數。 因為其常見慣用語，從 Visual Studio 2015 update 3，一般的常數，例如 1 或 **，則為 true**不會觸發警告，除非它們是在運算式中作業的結果。

如果的控制運算式**雖然**迴圈是常數，因為迴圈會結束，中間，請考慮更換**雖然**迴圈**的**迴圈。 您可以省略初始化、 終止測試，並在迴圈的遞增**針對**迴圈中，這會導致無限的就像迴圈`while(1)`，和您可以結束迴圈的主體**的**陳述式。

## <a name="example"></a>範例

下列範例會示範兩種方式 C4127 產生，並示範如何使用 for 迴圈來避免出現警告：

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