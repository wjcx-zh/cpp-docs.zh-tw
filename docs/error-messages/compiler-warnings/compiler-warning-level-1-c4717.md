---
title: 編譯器警告 (層級 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 40897e54601793431671bc14f855db43e905c656
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175284"
---
# <a name="compiler-warning-level-1-c4717"></a>編譯器警告 (層級 1) C4717

' function '：在所有控制路徑上遞迴，函式會造成執行時間堆疊溢位

透過函式的每個路徑都包含對函數的呼叫。 因為沒有任何方法可以結束函式，而不需要先以遞迴方式呼叫它本身，所以函式永遠不會結束。

下列範例會產生 C4717：

```cpp
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```
