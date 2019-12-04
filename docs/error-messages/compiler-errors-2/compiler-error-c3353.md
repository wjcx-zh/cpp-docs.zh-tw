---
title: 編譯器錯誤 C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747445"
---
# <a name="compiler-error-c3353"></a>編譯器錯誤 C3353

'delegate'：只能從全域函式或 Managed 或 WinRT 類型的成員函式建立委派

使用[委派](../../extensions/delegate-cpp-component-extensions.md)關鍵字宣告的委派，只能在全域範圍中宣告。

下列範例會產生 C3353：

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
