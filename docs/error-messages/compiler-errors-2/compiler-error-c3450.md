---
title: 編譯器錯誤 C3450
ms.date: 11/04/2016
f1_keywords:
- C3450
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
ms.openlocfilehash: a5228e0396221c51f5fc7336255656416c1e553b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328631"
---
# <a name="compiler-error-c3450"></a>編譯器錯誤 C3450

'type'：不是屬性，無法指定 [System::AttributeUsageAttribute] 或 [Windows::Foundation::Metadata::AttributeUsageAttribute]

使用者定義的 Managed 屬性必須繼承自 <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>。 Windows 執行階段屬性必須定義於 `Windows::Foundation::Metadata` 命名空間。

如需詳細資訊，請參閱 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3450，並示範如何修正此問題：

```
// C3450.cpp
// compile with: /clr
// C3450 expected
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref struct AtClass {
   AtClass(Type ^) {}
};

[attribute(AttributeTargets::All)]
ref struct AtClass2 {
   AtClass2() {}
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
// Delete the following line to resolve.
ref class B {};
// Uncomment the following line to resolve.
// ref class B : Attribute {};
```