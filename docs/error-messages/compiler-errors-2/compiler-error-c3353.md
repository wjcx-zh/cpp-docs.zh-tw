---
title: 編譯器錯誤 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776137"
---
# <a name="compiler-error-c3353"></a>編譯器錯誤 C3353

'delegate'：只能從全域函式或 Managed 或 WinRT 類型的成員函式建立委派

使用宣告的委派[委派](../../extensions/delegate-cpp-component-extensions.md)關鍵字，只能在全域範圍內宣告。

下列範例會產生 C3353：

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```