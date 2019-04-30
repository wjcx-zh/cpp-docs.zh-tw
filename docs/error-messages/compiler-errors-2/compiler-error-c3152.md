---
title: 編譯器錯誤 C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: 270d2fb02365f9c2460257d96bb5f6028707553e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374881"
---
# <a name="compiler-error-c3152"></a>編譯器錯誤 C3152

'construct'：'keyword' 只能套用至類別、結構或虛擬成員函式

某些關鍵字只能套用至 C++ 類別。

下列範例會產生 C3152，並示範如何修正此問題：

```
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
