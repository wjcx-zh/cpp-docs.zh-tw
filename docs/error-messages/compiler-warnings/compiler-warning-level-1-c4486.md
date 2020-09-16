---
title: 編譯器警告 (層級 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 893dd9241f83895d253fc8b5513f56cab272e31c
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684673"
---
# <a name="compiler-warning-level-1-c4486"></a>編譯器警告 (層級 1) C4486

' function '： ref 類別或實值類別的私用虛擬方法應標記為 ' sealed '

由於無法存取或覆寫 managed 類別或結構的私用虛擬成員函式，因此它應該標示為 [sealed](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="examples"></a>範例

下列範例會產生 C4486。

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

下列範例會示範私用密封虛擬函式的一種可能用途。

```cpp
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```
