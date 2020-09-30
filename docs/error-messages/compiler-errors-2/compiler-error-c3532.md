---
title: 編譯器錯誤 C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: b8d516074b79704b10d27dd4638585a5ada08323
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510121"
---
# <a name="compiler-error-c3532"></a>編譯器錯誤 C3532

' type '： ' auto ' 的使用不正確

無法使用關鍵字宣告指定的型別 **`auto`** 。 例如，您不能使用 **`auto`** 關鍵字來宣告陣列或方法傳回型別。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定初始化運算式會產生有效的型別。

1. 確定您未宣告陣列或方法傳回型別。

## <a name="examples"></a>範例

下列範例會產生 C3532，因為 **`auto`** 關鍵字無法宣告方法傳回型別。

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

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

[auto 關鍵字](../../cpp/auto-cpp.md)
