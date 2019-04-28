---
title: 編譯器警告 (層級 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0cf9aef8f68ca5972fd3d7886cd8061b88d043ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221137"
---
# <a name="compiler-warning-level-1-c4717"></a>編譯器警告 (層級 1) C4717

'function': 在所有控制路徑上的遞迴，函式會導致執行階段堆疊溢位

透過函式的每個路徑包含函式的呼叫。 因為沒有任何方法可以結束而不需本身的第一次呼叫函式以遞迴方式，就會永遠不會結束函式。

下列範例會產生 C4717:

```
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