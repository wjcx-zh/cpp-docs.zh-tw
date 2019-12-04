---
title: 編譯器錯誤 C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 148433f0d959985eb5a874f588f8cbf9d377e8b7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735953"
---
# <a name="compiler-error-c3299"></a>編譯器錯誤 C3299

'member_function' : 無法指定條件約束，因為它們是繼承自基底方法

在覆寫泛型成員函式時，您無法指定條件約束子句 (重複條件約束表示不會繼承條件約束)。

將會繼承您正在覆寫的泛型函式上的條件約束子句。

如需詳細資訊，請參閱[泛型型別參數的限制式 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3299：

```cpp
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
