---
title: 編譯器警告 (層級 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: fb51d16cc15c244b31d65f7777de66c372bbde33
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683197"
---
# <a name="compiler-warning-level-4-c4481"></a>編譯器警告 (層級 4) C4481

使用非標準的擴充：覆寫規範 ' 關鍵字 '

使用的關鍵字不在C++標準中，例如，其中一個也適用于/clr 的覆寫規範  如需詳細資訊，請參閱：

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [覆寫指定名稱](../../extensions/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>範例

下列範例會產生 C4481。

```cpp
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