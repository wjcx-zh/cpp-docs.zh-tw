---
title: 編譯器錯誤 C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: 5e31138d50676c312028e35b480cc682dc146a43
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757120"
---
# <a name="compiler-error-c3816"></a>編譯器錯誤 C3816

' 宣告 ' 先前已使用不同的 managed 或 WinRTmodifier 來宣告或定義

向前宣告或實際宣告需要屬性宣告中沒有衝突和不一致。

下列範例會產生 C3816，並示範如何修正此問題：

```cpp
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```
