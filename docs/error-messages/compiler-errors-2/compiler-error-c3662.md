---
title: 編譯器錯誤 C3662
ms.date: 11/04/2016
f1_keywords:
- C3662
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
ms.openlocfilehash: 48fe8bd4a6872ff214d185ac77553debab78ab20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758186"
---
# <a name="compiler-error-c3662"></a>編譯器錯誤 C3662

'member'：只允許在 Managed 或 WinRT 類別的成員函式上覆寫規範 'specifier'

不允許在原生類型的成員上使用覆寫規範。

如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3662。

```cpp
// C3662.cpp
// compile with: /clr /c
struct S {
   virtual void f();
};

struct S1 : S {
   virtual void f() new;   // C3662
};

ref struct T {
   virtual void f();
};

ref struct T1 : T {
   virtual void f() new;   // OK
};
```
