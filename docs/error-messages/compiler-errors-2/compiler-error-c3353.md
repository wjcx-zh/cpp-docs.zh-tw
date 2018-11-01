---
title: 編譯器錯誤 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: eb7b55f63e911f155c13e777e2e84ae7b587e9a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432665"
---
# <a name="compiler-error-c3353"></a>編譯器錯誤 C3353

'delegate'：只能從全域函式或 Managed 或 WinRT 類型的成員函式建立委派

使用宣告的委派[委派](../../windows/delegate-cpp-component-extensions.md)關鍵字，只能在全域範圍內宣告。

下列範例會產生 C3353：

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```