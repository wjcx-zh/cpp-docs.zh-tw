---
title: 編譯器錯誤 C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: db36afa1376a0b64b3e110acd1722d3e0f2af449
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758953"
---
# <a name="compiler-error-c2203"></a>編譯器錯誤 C2203

delete 運算子無法指定陣列的界限

使用 **/za** （ANSI）選項，`delete` 運算子可以刪除整個陣列，而不是陣列的部分或特定成員。

下列範例會產生 C2203：

```cpp
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```
