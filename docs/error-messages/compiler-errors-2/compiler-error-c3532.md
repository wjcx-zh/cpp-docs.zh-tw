---
title: 編譯器錯誤 C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: e2329111e916df9eac99d156bcf58a58e148cb08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228813"
---
# <a name="compiler-error-c3532"></a>編譯器錯誤 C3532

' type '： ' auto ' 的使用不正確

指定的類型不能使用關鍵字來宣告 **`auto`** 。 例如，您不能使用 **`auto`** 關鍵字來宣告陣列或方法傳回型別。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請確定初始化運算式會產生有效的型別。

1. 請確定您未宣告陣列或方法傳回型別。

## <a name="example"></a>範例

下列範例會產生 C3532，因為 **`auto`** 關鍵字無法宣告方法傳回型別。

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>範例

下列範例會產生 C3532，因為 **`auto`** 關鍵字無法宣告陣列。

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
