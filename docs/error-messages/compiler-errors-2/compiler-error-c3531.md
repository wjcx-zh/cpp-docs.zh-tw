---
title: 編譯器錯誤 C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 7da9da2daedc79db619f82848dc864d1cb7bd1f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750087"
---
# <a name="compiler-error-c3531"></a>編譯器錯誤 C3531

' symbol '：其類型包含 ' auto ' 的符號必須有初始化運算式

指定的變數沒有初始化運算式運算式。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 當您宣告變數時，請指定初始化運算式運算式，例如使用等號語法的簡單指派。

## <a name="example"></a>範例

下列範例會產生 C3531，因為變數 `x1`、`y1, y2, y3`和 `z2` 並未初始化。

```cpp
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
