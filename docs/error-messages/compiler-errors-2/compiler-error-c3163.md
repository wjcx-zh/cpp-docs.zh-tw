---
title: 編譯器錯誤 C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 436fb112758dfdec9997ff7e6dd7ef8f9dcdc66e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761773"
---
# <a name="compiler-error-c3163"></a>編譯器錯誤 C3163

' 結構 '：屬性與先前的宣告不一致

套用至定義的屬性會與套用至宣告的屬性發生衝突的情況。

解決 C3163 的其中一種方法是排除向前宣告的屬性。 正向宣告上的任何屬性都應該小於定義上的屬性，或最多隻能等於它們。

C3163 錯誤的可能原因包括 Microsoft 原始程式碼注釋語言（SAL）。 除非您使用 **/analyze**旗標來編譯您的專案，否則 SAL 宏不會展開。 如果您嘗試使用/analyze 選項來重新編譯，則在沒有/analyze 編譯的程式中，可能會擲回 C3163。 如需 SAL 的詳細資訊，請參閱[Sal 注釋](../../c-runtime-library/sal-annotations.md)。

## <a name="example"></a>範例

下列範例會產生 C3163。

```cpp
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>請參閱

[SAL 註釋](../../c-runtime-library/sal-annotations.md)
