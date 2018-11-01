---
title: 編譯器警告 (層級 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: f88a61a40a789c31e80875d785b95136ac69253c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466933"
---
# <a name="compiler-warning-level-4-c4481"></a>編譯器警告 (層級 4) C4481

使用非標準擴充： 覆寫規範 'keyword'

使用不是在 c + + 標準，例如，有一個也能在 /clr 下運作的覆寫規範的關鍵字。  如需詳細資訊，請參閱：

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>範例

下列範例會產生 C4481。

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```