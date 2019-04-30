---
title: 編譯器錯誤 C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 27eba3df800c42cc53a7031e958a675c84255440
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344517"
---
# <a name="compiler-error-c3609"></a>編譯器錯誤 C3609

'member'：密封或最終函式必須為虛擬

[密封](../../extensions/sealed-cpp-component-extensions.md)並[最終](../../cpp/final-specifier.md)關鍵字只允許在標記為類別、 結構或成員函式`virtual`。

下列範例會產生 C3609：

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
