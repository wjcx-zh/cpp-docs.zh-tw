---
title: 編譯器警告（層級3） C4018
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: f5708a9f52b6fc8206094454c352710199437f27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161694"
---
# <a name="compiler-warning-level-3-c4018"></a>編譯器警告（層級3） C4018

' expression '：帶正負號/不帶正負號

比較帶正負號和不帶正負號的數位，編譯器會將已簽署的值轉換為未簽署。

如果您在測試已簽署和不帶正負號的類型時，轉換這兩種類型的其中一種，就可以修正這個

下列範例會產生 C4018：

```cpp
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```
