---
title: 屬性參數類型  (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
ms.openlocfilehash: c7b219ddad939aab7d6093787dc2fe4131ccced5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225159"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>屬性參數類型  (C++/CLI 和 C++/CX)

在編譯時期，編譯器必須能辨識傳遞至屬性的值。  屬性參數可以是下列其中一種類型：

- **`bool`**

- **`char`**, **`unsigned char`**

- **`short`**, **`unsigned short`**

- **`int`**, **`unsigned int`**

- **`long`**, **`unsigned long`**

- **`__int64`**，不**帶正負**號的 __int64

- **`float`**, **`double`**

- **`wchar_t`**

- **`char*`** 或 `wchar_t*` 或`System::String*`

- `System::Type ^`

- `System::Object ^`

- **`enum`**

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

[使用者定義屬性](user-defined-attributes-cpp-component-extensions.md)
