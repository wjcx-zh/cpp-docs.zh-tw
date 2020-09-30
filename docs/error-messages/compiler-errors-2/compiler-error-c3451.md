---
title: 編譯器錯誤 C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: d6a0d1234d8f25c6a55fffa7170f37aae27f5817
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501314"
---
# <a name="compiler-error-c3451"></a>編譯器錯誤 C3451

' attribute '：無法將非受控屬性套用至 ' type '

C + + 屬性無法套用至 CLR 類型。 如需詳細資訊，請參閱 [c + + 屬性參考](../../windows/attributes/attributes-alphabetical-reference.md) 。

如需詳細資訊，請參閱 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

這項錯誤可能是因為針對 Visual Studio 2005 所進行的編譯器一致性工作所產生：使用 CLR 程式設計時，使用者定義的屬性已不再允許 [uuid](../../windows/attributes/uuid-cpp-attributes.md) 屬性。 請改用 <xref:System.Runtime.InteropServices.GuidAttribute>。

## <a name="example"></a>範例

下列範例會產生 C3451。

```cpp
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```
