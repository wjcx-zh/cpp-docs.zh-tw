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
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360807"
---
# <a name="__restrict"></a>__restrict

與 **__declspec ([限制](../cpp/restrict.md))** 修飾符一樣 **,__restrict**關鍵字表示符號在當前作用域中未進行別名。 **__restrict**關鍵字`__declspec ( restrict )`與 修飾符在以下方面有所不同:

- **__restrict**關鍵字僅在變數上有效,`__declspec ( restrict )`並且僅在函數聲明和定義上有效。

- **__restrict**類似於 C99 規範**的限制**,但 **__restrict**可用於C++或 C 程式。

- 使用 **__restrict**時,編譯器不會傳播變數的無別名屬性。 也就是說,如果將 **__restrict**變數分配給非 **__restrict**變數,編譯器仍將允許對非__restrict變數進行別名化。 這與 C99 規範中**限制**關鍵字的行為不同。

一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。

為了與早期版本相容,**除非**指定編譯器選項[/Za\(禁用語言擴展,](../build/reference/za-ze-disable-language-extensions.md)否則_restrict是 **__restrict**的同義詞。

在 Visual Studio 2015 及更高版本中 **,__restrict**可用於C++引用。

> [!NOTE]
> 當在也有[易失性](../cpp/volatile-cpp.md)關鍵字的變數上使用時,**揮發性**將優先。

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
