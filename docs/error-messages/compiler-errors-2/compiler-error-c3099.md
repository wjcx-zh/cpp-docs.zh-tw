---
title: 編譯器錯誤 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: beaa34bb9bed4824383cdad32c6bfd0aea19f6b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418567"
---
# <a name="compiler-error-c3099"></a>編譯器錯誤 C3099

'keyword': 對 Managed 屬性使用 [System::AttributeUsageAttribute]；對 WinRT 屬性使用 [Windows::Foundation::Metadata::AttributeUsageAttribute]

使用<xref:System.AttributeUsageAttribute>來宣告 **/clr**屬性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 宣告 Windows 執行階段屬性。

如需 /CLR 屬性的詳細資訊，請參閱 < [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。 支援 Windows 執行階段中的屬性，請參閱[Windows.Foundation.Metadata 命名空間](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>範例

下列範例會產生 C3099，並示範如何修正此問題。

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```