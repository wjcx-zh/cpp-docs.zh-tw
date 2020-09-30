---
title: 編譯器錯誤 C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 1e1f131d551440e44e1a2ed9ed9b9c18c71eb22d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508162"
---
# <a name="compiler-error-c3538"></a>編譯器錯誤 C3538

在宣告子清單中 'auto' 必須永遠推算為相同型別

宣告清單中所有已宣告的變數未解析為相同類型。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定清單中的所有宣告都推算 **`auto`** 為相同的類型。

## <a name="example"></a>範例

下列陳述式會產生 C3538。 每個語句會宣告多個變數，但每次使用關鍵字時，都 **`auto`** 不會推算為相同的類型。

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)
