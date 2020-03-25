---
title: 編譯器錯誤 C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 330932f53627f8ba09e9e089cec7809eeeb6ab1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206072"
---
# <a name="compiler-error-c2362"></a>編譯器錯誤 C2362

> ' goto *label*' 已略過 '*identifier*' 的初始化

當使用[/za](../../build/reference/za-ze-disable-language-extensions.md)進行編譯時，跳至標籤會防止識別碼初始化。

如果宣告包含在未輸入的區塊中，或如果已初始化變數，您就只能使用初始化運算式來跳過宣告。

下列範例會產生 C2362：

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

可能的解決方案：

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
