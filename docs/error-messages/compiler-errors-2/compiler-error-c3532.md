---
title: 編譯器錯誤 C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: 91d8e28e053d8ce1b307f9345ab3249386bdf1ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568881"
---
# <a name="compiler-error-c3532"></a>編譯器錯誤 C3532

'type': 不正確的使用方式，'auto'

指定的類型不可以宣告具有`auto`關鍵字。 例如，您無法使用`auto`關鍵字來宣告陣列或方法傳回型別。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請確定的初始化運算式會產生有效的型別。

1. 請確定不要宣告陣列或方法的傳回型別。

## <a name="example"></a>範例

下列範例會產生 C3532，因為`auto`關鍵字不能宣告方法的傳回型別。

```
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>範例

下列範例會產生 C3532，因為`auto`關鍵字不能宣告陣列。

```
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