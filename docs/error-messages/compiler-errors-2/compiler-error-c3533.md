---
title: 編譯器錯誤 C3533
ms.date: 11/04/2016
f1_keywords:
- C3533
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
ms.openlocfilehash: 7a567e4396999f98d9e9740db0acf951c443d525
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026301"
---
# <a name="compiler-error-c3533"></a>編譯器錯誤 C3533

'type': 參數名稱不可包含 'auto' 的類型

方法或樣板參數不能以宣告`auto`關鍵字如果預設值[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)編譯器選項處於作用中。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 移除`auto`從參數宣告的關鍵字。

## <a name="example"></a>範例

下列範例會產生 C3533，因為它會宣告的函式參數`auto`關鍵字，它會使用編譯 **/zc: auto**。

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>範例

下列範例會產生以 C + + 14 模式 C3533 因為它會宣告與樣板參數`auto`關鍵字，它會使用編譯 **/zc: auto**。（在 c++17 中，這是有效的定義，具有單一的非類型範本參數的類型推算的類別範本。）

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (推算變數類型)](../../build/reference/zc-auto-deduce-variable-type.md)
