---
title: 編譯器警告（層級1） C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: 58f7150caeb3e06ba400a08c6e484f677a8deff9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051379"
---
# <a name="compiler-warning-level-1-c4669"></a>編譯器警告（層級1） C4669

'cast'：不安全的轉換：'class' 是 Managed 或 WinRT 型別的物件

轉換包含 Windows 執行階段型別或 Managed 型別。 編譯器會執行一個指標到另一個指標的位元複製來完成轉換，但不提供其他檢查。 若要解決這個警告，請不要轉換包含 Managed 成員或 Windows 執行階段型別的類別。

下列範例會產生 C4669，並示範如何修正此問題：

```cpp
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```