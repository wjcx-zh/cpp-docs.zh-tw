---
title: __restrict |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d9754f8b0b218fc4d627eb0e27504e8521bf776
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076433"
---
# <a name="restrict"></a>__restrict

像是 **__declspec ([限制](../cpp/restrict.md))** 修飾詞 **__restrict**關鍵字會指出符號不是目前範圍中的別名。 **__Restrict**關鍵字與`__declspec ( restrict )`修飾詞，以下列方式：

- **__Restrict**關鍵字是只有在變數上有效和`__declspec ( restrict )`只適用於在函式宣告和定義。

- **__restrict**大致**限制**於 C99 規格中，但 **__restrict**可以用於 c + + 或 C 程式中。

- 當 **__restrict**是使用，編譯器將不會傳播變數的無別名屬性。 亦即，如果您指派 **__restrict**變數設為非 **__restrict**變數，編譯器還是會允許非 __restrict 變數具有別名。 這是不同的行為**限制**C99 規格中的關鍵字。

一般而言，如果您要影響整個函式的行為，使用 `__declspec ( restrict )` 的效果會比使用關鍵字更好。

在 Visual Studio 2015 和更新版本， **__restrict**可以用於 c + + 參考。

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