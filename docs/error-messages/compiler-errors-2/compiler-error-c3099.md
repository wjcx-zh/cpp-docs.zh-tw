---
title: 編譯器錯誤 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 81f508c47c678d86f8f95303861b42f8a70daa57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750048"
---
# <a name="compiler-error-c3099"></a>編譯器錯誤 C3099

'keyword': 對 Managed 屬性使用 [System::AttributeUsageAttribute]；對 WinRT 屬性使用 [Windows::Foundation::Metadata::AttributeUsageAttribute]

使用 <xref:System.AttributeUsageAttribute> 宣告 **/clr**屬性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 宣告 Windows 執行階段屬性。

如需/CLR 屬性的詳細資訊，請參閱[使用者定義屬性](../../extensions/user-defined-attributes-cpp-component-extensions.md)。 如需 Windows 執行階段中支援的屬性，請參閱[Windows. Foundation. Metadata 命名空間](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>範例

下列範例會產生 C3099，並示範如何修正此問題。

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
