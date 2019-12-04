---
title: 編譯器錯誤 C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 2970c4851d3e5cbbe9952c12a71c913c5e3ac656
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755326"
---
# <a name="compiler-error-c3753"></a>編譯器錯誤 C3753

不允許泛型屬性

泛型參數清單只能出現在 managed 類別、結構或函式上。

如需詳細資訊，請參閱[泛型](../../extensions/generics-cpp-component-extensions.md)和[屬性](../../extensions/property-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3753。

```cpp
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```
