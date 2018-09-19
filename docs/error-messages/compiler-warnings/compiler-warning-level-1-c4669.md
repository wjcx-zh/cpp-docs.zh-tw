---
title: 編譯器警告 （層級 1） C4669 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4669
dev_langs:
- C++
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f96bcf40b1fbc989daceabc810d019d1bb9aa98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060848"
---
# <a name="compiler-warning-level-1-c4669"></a>編譯器警告 (層級 1) C4669

'cast'：不安全的轉換：'class' 是 Managed 或 WinRT 型別的物件

轉換包含 Windows 執行階段型別或 Managed 型別。 編譯器會執行一個指標到另一個指標的位元複製來完成轉換，但不提供其他檢查。 若要解決這個警告，請不要轉換包含 Managed 成員或 Windows 執行階段型別的類別。

下列範例會產生 C4669，並示範如何修正此問題：

```
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