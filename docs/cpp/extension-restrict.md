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
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183748"
---
# <a name="restrict"></a>__restrict

像是 **__declspec ([限制](../cpp/restrict.md))** 修飾詞 **__restrict**關鍵字會指出符號不是目前範圍中的別名。 **__Restrict**關鍵字與`__declspec ( restrict )`修飾詞，以下列方式：

- **__Restrict**關鍵字是只有在變數上有效和`__declspec ( restrict )`只適用於在函式宣告和定義。

- **__restrict**大致**限制**於 C99 規格中，但 **__restrict**可用在C++或 C 程式。

- 當 **__restrict**是使用，編譯器將不會傳播變數的無別名屬性。 亦即，如果您指派 **__restrict**變數設為非 **__restrict**變數，編譯器還是會允許非 __restrict 變數具有別名。 這是不同的行為**限制**C99 規格中的關鍵字。

一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。

為了與舊版中，相容性 **_restrict**同義 **__restrict**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)是指定此項目。

在 Visual Studio 2015 和更新版本， **__restrict**用於C++參考。

> [!NOTE]
>  也有一個變數上使用時[volatile](../cpp/volatile-cpp.md)關鍵字**volatile**會優先使用。

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