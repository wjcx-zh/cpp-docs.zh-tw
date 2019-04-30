---
title: 編譯器錯誤 C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: d362480b3380fe4576ef56b8ca76dfa10eaa1408
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384279"
---
# <a name="compiler-error-c3816"></a>編譯器錯誤 C3816

'declaration' 先前已宣告或定義與另一個受控或 WinRTmodifier

向前宣告或實際宣告需要屬性宣告中沒有衝突和不一致。

下列範例會產生 C3816，並示範如何修正此問題：

```
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```