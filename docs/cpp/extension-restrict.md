---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 6318e6d78f6c4c4bb6827a79d26bca028dfe3f3f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233739"
---
# <a name="__restrict"></a>__restrict

如同 **__declspec （[限制](../cpp/restrict.md)）** 修飾詞， **`__restrict`** 關鍵字會指出符號在目前範圍中沒有別名。 關鍵字與修飾詞有 **`__restrict`** 下列不同之處 `__declspec ( restrict )` ：

- **`__restrict`** 關鍵字只在變數上有效，而且 `__declspec ( restrict )` 只有在函式宣告和定義上才有效。

- **`__restrict`** 類似于 **`restrict`** C99 規格，但 **`__restrict`** 可在 c + + 或 c 程式中使用。

- **`__restrict`** 使用時，編譯器不會傳播變數的「無別名」屬性。 也就是說，如果您將變數指派 **`__restrict`** 至非 **`__restrict`** 變數，編譯器仍然會允許非 __restrict 變數的別名。 這與 C99 規格中關鍵字的行為不同 **`restrict`** 。

一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。

為了與舊版相容， **_restrict** **`__restrict`** 除非指定了編譯器選項[/za 停用 \( 語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能，否則 _restrict 是同義字。

在 Visual Studio 2015 和更新版本中， **`__restrict`** 可以用於 c + + 參考。

> [!NOTE]
> 當用於也具有[volatile](../cpp/volatile-cpp.md)關鍵字的變數時， **`volatile`** 將會優先使用。

## <a name="example"></a>範例

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
