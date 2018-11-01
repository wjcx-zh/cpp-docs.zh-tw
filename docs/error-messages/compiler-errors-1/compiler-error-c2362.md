---
title: 編譯器錯誤 C2362
ms.date: 11/04/2016
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 17656b2a48a3680a9269d3ca300fd4188eda6b84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661106"
---
# <a name="compiler-error-c2362"></a>編譯器錯誤 C2362

'identifier' 的初始化會略過由 'goto label'

進行編譯時[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳至標籤導致無法進行初始化的識別項。

除非宣告括在不輸入，區塊中，您無法跳過具有初始設定式的宣告，或已初始化的變數。

下列範例會產生 C2326：

```
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解決方式：

```
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```