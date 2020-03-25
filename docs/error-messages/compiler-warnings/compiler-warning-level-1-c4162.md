---
title: 編譯器警告（層級1） C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 68e3a752f2aa039f4a2aba24d6433dc9fe2372f6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200053"
---
# <a name="compiler-warning-level-1-c4162"></a>編譯器警告（層級1） C4162

' identifier '：找不到具有 C 連結的函式

已宣告具有 C 連結的函式，但找不到該函式。

若要解決這個警告，請在 .c 檔案中進行編譯（叫用 C 編譯器）。  如果您必須叫用C++編譯器，請將 Extern "C" 放在函式宣告之前。

下列範例會產生 C4162

```cpp
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

可能的解決方案：

```cpp
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
