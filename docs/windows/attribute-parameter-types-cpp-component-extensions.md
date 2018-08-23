---
title: 屬性參數類型 （c + + 元件延伸模組） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84c97dc0eb449ed0a2e835c46e77981dda0b67e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611902"
---
# <a name="attribute-parameter-types--c-component-extensions"></a>屬性參數類型 (C++ 元件擴充功能)

在編譯時期，編譯器必須能辨識傳遞至屬性的值。  屬性參數可以是下列其中一種類型：

- **bool**

- **char**， **unsigned char**

- **short**、**unsigned short**

- **int**，**不帶正負號的 int**

- **長**，**不帶正負號長時間**

- **__int64**，**不帶正負號的 __int64**

- **浮點數**， **double**

- **wchar_t**

- `char*`、`wchar_t*` 或 `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>範例

### <a name="description"></a>描述

當指定屬性時，所有未命名的 (位置) 引數都必須放在任何具名引數前面。

### <a name="code"></a>程式碼

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>範例

### <a name="description"></a>描述

屬性參數可以是前述類型的一維陣列。

### <a name="code"></a>程式碼

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>另請參閱

[使用者定義的屬性](../windows/user-defined-attributes-cpp-component-extensions.md)