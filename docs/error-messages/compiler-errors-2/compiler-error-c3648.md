---
title: 編譯器錯誤 C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: f3ef949b2651631f30a9c614a0d21b2668b7239f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653761"
---
# <a name="compiler-error-c3648"></a>編譯器錯誤 C3648

明確覆寫語法需要 /clr: oldsyntax

在編譯時的最新的 managed 語法，編譯器發現明確覆寫先前的版本不受支援的語法。

如需詳細資訊，請參閱 <<c0> [ 明確覆寫](../../windows/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3648:

```
// C3648.cpp
// compile with: /clr
public interface struct I {
   void f();
};

public ref struct R : I {
   virtual void I::f() {}   // C3648
   // try the following line instead
   // virtual void f() = I::f{}
};
```