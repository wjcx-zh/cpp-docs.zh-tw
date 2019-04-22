---
title: 編譯器警告 (層級 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: fe96ff50f4081e3c9dbe3c7eb68da156a69c96ab
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776358"
---
# <a name="compiler-warning-level-4-c4481"></a>編譯器警告 (層級 4) C4481

使用非標準擴充： 覆寫規範 'keyword'

使用了不在關鍵字C++標準，例如，有一個也能在 /clr 下運作的覆寫規範。  如需詳細資訊，請參閱：

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [覆寫指定名稱](../../extensions/override-specifiers-cpp-component-extensions.md)

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