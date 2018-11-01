---
title: 編譯器錯誤 C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: b6b1e8c3241a778b29045e734fffebb663554e62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498367"
---
# <a name="compiler-error-c3753"></a>編譯器錯誤 C3753

不允許泛型屬性

泛型參數清單只能出現在受管理的類別、 結構或函式。

如需詳細資訊，請參閱 <<c0> [ 泛型](../../windows/generics-cpp-component-extensions.md)並[屬性](../../windows/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3753。

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```