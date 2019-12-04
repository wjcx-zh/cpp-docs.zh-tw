---
title: 編譯器錯誤 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: ce95bba417e9be3603f15376a0fd65a48f951a2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755638"
---
# <a name="compiler-error-c3533"></a>編譯器錯誤 C3533

' type '：參數不能有包含 ' auto ' 的類型

如果預設的[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)編譯器選項生效，則無法使用 `auto` 關鍵字來宣告方法或範本參數。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 請從參數宣告中移除 `auto` 關鍵字。

## <a name="example"></a>範例

下列範例會產生 C3533，因為它會宣告具有 `auto` 關鍵字的函式參數，並使用 **/zc： auto**進行編譯。

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>範例

下列範例會在 c + + 14 模式中產生 C3533，因為它會宣告具有 `auto` 關鍵字的樣板參數，並使用 **/zc： auto**進行編譯。（在 c + + 17 中，這是具有推斷類型的單一非類型樣板參數之類別樣板的有效定義）。

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (推算變數類型)](../../build/reference/zc-auto-deduce-variable-type.md)
