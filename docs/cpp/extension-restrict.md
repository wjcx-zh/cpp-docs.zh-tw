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
ms.openlocfilehash: cb340554bc20516175400c4d14a5d0dba934a313
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188957"
---
# <a name="__restrict"></a>__restrict

如同 **__declspec （[限制](../cpp/restrict.md)）** 修飾詞， **__restrict**關鍵字指出符號在目前範圍中沒有別名。 **__Restrict**關鍵字與 `__declspec ( restrict )` 修飾詞有下列不同之處：

- **__Restrict**關鍵字只在變數上有效，而 `__declspec ( restrict )` 只對函式宣告和定義有效。

- **__restrict**類似于 C99 規格的**限制**，但 **__restrict**可以在或 C 程式中C++使用。

- 使用 **__restrict**時，編譯器不會傳播變數的「無別名」屬性。 也就是說，如果您將 **__restrict**變數指派給非 **__restrict**變數，編譯器仍然會允許非 __restrict 變數的別名。 這與 C99 規格中的**restrict**關鍵字行為不同。

一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_restrict**是 **__restrict**的同義字。

在 Visual Studio 2015 和更新版本中， **__restrict**可以在C++參考上使用。

> [!NOTE]
>  在也具有[volatile](../cpp/volatile-cpp.md)關鍵字的變數上使用時， **volatile**的優先順序會較高。

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
