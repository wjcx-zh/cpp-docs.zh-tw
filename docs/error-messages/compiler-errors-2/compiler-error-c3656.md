---
title: 編譯器錯誤 C3656
ms.date: 11/04/2016
f1_keywords:
- C3656
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
ms.openlocfilehash: 9709f3105e957012c05111ea818890b6d1df8259
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778406"
---
# <a name="compiler-error-c3656"></a>編譯器錯誤 C3656

'override': 覆寫規範不可重複

明確覆寫關鍵字只指定一次。 如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

下列範例會產生 C3656:

```
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```