---
title: 使用陣列 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
ms.openlocfilehash: 7f7a987a2b4c18e59dd058ccfc4375c304188398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152740"
---
# <a name="using-arrays-c"></a>使用陣列 (C++)

使用陣列註標運算子 (`[ ]`)，您可以存取陣列的個別項目。 如果一維陣列用於沒有註標的運算式，陣列名稱判斷值為陣列中第一個項目的指標。

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

當您使用多維陣列時，您可以在運算式中使用各種組合。

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

在上述程式碼中，`multi`是一個三維陣列型別的**double**。 `p2multi`指標會指向的型別陣列**double**大小為三。 在此範例中，陣列搭配使用的註標有一個、兩個和三個。 雖然更常見的是指定所有註標 (如在 `cout` 陳述式中)，但有時選取陣列元素的特定子集是很有用的 (如 `cout` 之後的陳述式所示)。

## <a name="see-also"></a>另請參閱

[陣列](../cpp/arrays-cpp.md)