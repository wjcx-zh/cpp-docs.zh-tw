---
title: 編譯器錯誤 C3648
ms.date: 11/04/2016
f1_keywords:
- C3648
helpviewer_keywords:
- C3648
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
ms.openlocfilehash: 3b26be9890bbbdf6276c61023e6867160528e236
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751829"
---
# <a name="compiler-error-c3648"></a>編譯器錯誤 C3648

這個明確覆寫語法需要/clr： oldSyntax

針對最新的 managed 語法進行編譯時，編譯器會找到不再支援之舊版的明確覆寫語法。

如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3648：

```cpp
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
