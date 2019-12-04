---
title: 編譯器錯誤 C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: 52fa349b735a228a6acbe2fd6e1af461db2cf5c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745937"
---
# <a name="compiler-error-c3152"></a>編譯器錯誤 C3152

'construct'：'keyword' 只能套用至類別、結構或虛擬成員函式

某些關鍵字只能套用至 C++ 類別。

下列範例會產生 C3152，並示範如何修正此問題：

```cpp
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
