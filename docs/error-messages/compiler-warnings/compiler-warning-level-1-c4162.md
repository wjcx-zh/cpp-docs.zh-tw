---
title: 編譯器警告 （層級 1） C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 6c6b675fd47cb6e98255515c7cd77c6dd48ea02b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578255"
---
# <a name="compiler-warning-level-1-c4162"></a>編譯器警告 （層級 1） C4162

'identifier': 使用 C 連結找到的任何函式

具有 C 連結的函式已宣告，但找不到。

若要解決這個警告，編譯.c 檔案中 （叫用 C 編譯器）。  如果您必須叫用 c + + 編譯器，放置 extern"C"函式宣告的前面。

下列範例會產生 C4162

```
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

可能的解決方式：

```
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```