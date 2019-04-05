---
title: 編譯器錯誤 C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 314b75a9d0ab8cde2886a7466fa0f95b5bbdd8f1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778048"
---
# <a name="compiler-error-c3299"></a>編譯器錯誤 C3299

'member_function' : 無法指定條件約束，因為它們是繼承自基底方法

在覆寫泛型成員函式時，您無法指定條件約束子句 (重複條件約束表示不會繼承條件約束)。

將會繼承您正在覆寫的泛型函式上的條件約束子句。

如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C + + /cli CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3299：

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```