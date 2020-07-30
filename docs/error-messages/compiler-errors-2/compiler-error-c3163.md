---
title: 編譯器錯誤 C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 29f810ab1ab1608ab9c0492c9f88b8edfe042168
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390022"
---
# <a name="compiler-error-c3163"></a>編譯器錯誤 C3163

> '*結構*'：屬性與先前的宣告不一致

套用至定義的屬性會與套用至宣告的屬性發生衝突的情況。

解決 C3163 的其中一種方法是排除向前宣告的屬性。 正向宣告上的任何屬性都應該小於定義上的屬性，或最多隻能等於它們。

C3163 錯誤的可能原因包括 Microsoft 原始程式碼注釋語言（SAL）。 除非您使用旗標來編譯專案，否則 SAL 宏不會展開 **`/analyze`** 。 **`/analyze`** 如果您嘗試使用選項重新編譯，則會在沒有的情況下編譯的程式，而不會擲回 C3163 **`/analyze`** 。 如需 SAL 的詳細資訊，請參閱[Sal 注釋](../../c-runtime-library/sal-annotations.md)。

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

## <a name="see-also"></a>另請參閱

[SAL 注釋](../../c-runtime-library/sal-annotations.md)
