---
title: 編譯器錯誤 C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: d48806982bbb6cdda4d29e47f6692e7e3601d6de
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503217"
---
# <a name="compiler-error-c2362"></a>編譯器錯誤 C2362

> 初始化 '*識別碼*' 會被略過 ' goto*標籤*'

藉由編譯時[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳至標籤導致無法進行初始化的識別項。

如果宣告括在區塊中不輸入，或如果已初始化的變數，您只可以跳過的初始設定式的宣告。

下列範例會產生 C2362:

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解決方式：

```cpp
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