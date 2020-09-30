---
title: 編譯器錯誤 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: c77c5c0fff8f8d9c1c64ba11773503b197006b67
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510114"
---
# <a name="compiler-error-c3533"></a>編譯器錯誤 C3533

' type '：參數不能有包含 ' auto ' 的類型

**`auto`** 如果預設的[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)編譯器選項作用中，則不能使用關鍵字宣告方法或範本參數。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請 **`auto`** 從參數宣告中移除關鍵字。

## <a name="examples"></a>範例

下列範例會產生 C3533，因為它會使用關鍵字宣告函式參數 **`auto`** ，並使用 **/zc： auto**來編譯。

```cpp
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

下列範例會在 c + + 14 模式中產生 C3533，因為它會使用關鍵字宣告樣板參數 **`auto`** ，並使用 **/zc： auto**來編譯。 (在 c + + 17 中，這是類別樣板的有效定義，其類型為推算的單一非類型樣板參數。 ) 

```cpp
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-cpp.md)<br/>
[/Zc： auto (推算變數類型) ](../../build/reference/zc-auto-deduce-variable-type.md)
