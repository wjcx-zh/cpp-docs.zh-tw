---
title: 編譯器錯誤 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: e9a76fa2e0dc5602a88324cfd2fef85457ad7e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512108"
---
# <a name="compiler-error-c3099"></a>編譯器錯誤 C3099

'keyword': 對 Managed 屬性使用 [System::AttributeUsageAttribute]；對 WinRT 屬性使用 [Windows::Foundation::Metadata::AttributeUsageAttribute]

使用<xref:System.AttributeUsageAttribute>來宣告 **/clr**屬性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 宣告 Windows 執行階段屬性。

如需 /CLR 屬性的詳細資訊，請參閱 < [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。 支援 Windows 執行階段中的屬性，請參閱[Windows.Foundation.Metadata 命名空間](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)

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