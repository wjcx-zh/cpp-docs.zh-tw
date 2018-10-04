---
title: 屬性 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++/CLI], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7fc581d35b1bb1c36808f77783e9724ac6ed6def
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790726"
---
# <a name="attribute"></a>屬性

可讓您建立自訂屬性。

## <a name="syntax"></a>語法

```cpp
[ attribute(
   AllowOn,
   AllowMultiple=boolean,
   Inherited=boolean
) ]
```

### <a name="parameters"></a>參數

*AllowOn*<br/>
指定可以套用自訂屬性的語言項目。 預設值是`System::AttributeTargets::All`(請參閱 < [System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx))。

*AllowMultiple*<br/>
指定是否將自訂屬性可以套用重複建構。 預設值為 FALSE。

*繼承*<br/>
指出屬性是否會繼承由子類別。 編譯器不提供特殊支援這項功能;它是屬性取用者的工作 (`Reflection`，例如) 遵從這項資訊。 如果*繼承*為 TRUE，繼承屬性。 如果*AllowMultiple*為 TRUE 時，屬性將會累積在衍生的成員; 如果*AllowMultiple*為 FALSE 時，此屬性會覆寫 （或取代） 在繼承。 如果*繼承*為 FALSE 時，將不會繼承屬性。 預設值為 TRUE。

## <a name="remarks"></a>備註

> [!NOTE]
> **屬性**屬性現在已被取代。  使用通用語言執行階段屬性`System.Attribute`來直接以建立使用者定義的屬性。 如需詳細資訊，請參閱 < [User-Defined Attributes](../user-defined-attributes-cpp-component-extensions.md)。

您定義[自訂屬性](custom-attributes-cpp.md)加上**屬性**上受管理的類別或結構定義的屬性。 類別的名稱是自訂的屬性。 例如: 

```cpp
[ attribute(Parameter) ]
public ref class MyAttr {};
```

定義稱為屬性`MyAttr`，可以套用至函式參數。 類別必須是公用，如果屬性要使用其他組件中。

> [!NOTE]
> 若要避免命名空間衝突，所有的屬性名稱會隱含地結束以"Attribute";在此範例中，屬性和類別的名稱是實際上`MyAttrAttribute`，但`MyAttr`和`MyAttrAttribute`可以交換使用。

類別的公用建構函式定義屬性的未命名的參數。 多載的建構函式允許多種方式來指定屬性，讓自訂屬性，是以下列方式定義：

```cpp
// cpp_attr_ref_attribute.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes
public ref class MyAttr {
public:
   MyAttr() {}   // Constructor with no parameters
   MyAttr(int arg1) {}   // Constructor with one parameter
};

[MyAttr]
ref class ClassA {};   // Attribute with no parameters

[MyAttr(123)]
ref class ClassB {};   // Attribute with one parameter
```

類別的公用資料成員和屬性是屬性的選擇性具名的參數：

```cpp
// cpp_attr_ref_attribute_2.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]
ref class MyAttr {
public:
   // Property Priority becomes attribute's named parameter Priority
    property int Priority {
       void set(int value) {}
       int get() { return 0;}
   }
   // Data member Version becomes attribute's named parameter Version
   int Version;
   MyAttr() {}   // constructor with no parameters
   MyAttr(int arg1) {}   // constructor with one parameter
};

[MyAttr(123, Version=2)]
ref class ClassC {};
```

如需可能的屬性參數類型的清單，請參閱 <<c0> [ 自訂屬性](custom-attributes-cpp.md)。

請參閱[User-Defined Attributes](../user-defined-attributes-cpp-component-extensions.md)如屬性目標的討論。

**屬性**屬性具有*AllowMultiple*指定自訂屬性是否為單次使用的參數或 multiuse （可出現一次以上相同的實體）。

```cpp
// cpp_attr_ref_attribute_3.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]
ref struct MyAttr {
   MyAttr(){}
};   // MyAttr is a multiuse attribute

[MyAttr, MyAttr()]
ref class ClassA {};
```

自訂屬性的類別是直接或間接衍生自<xref:System.ComponentModel.AttributeCollection.%23ctor%2A>，它能識別屬性定義，快速又簡單的中繼資料中。 **屬性**屬性會隱含繼承自`System::Attribute`，因此不需要明確衍生：

```cpp
[ attribute(Class) ]
ref class MyAttr
```

相當於

```cpp
[ attribute(Class) ]
ref class MyAttr : System::Attribute   // OK, but redundant.
```

**屬性**是的別名<xref:System.AttributeUsageAttribute?displayProperty=fullName>(不 AttributeAttribute; 這是屬性的命名規則的例外狀況)。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**ref 類別**， **ref 結構**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_attribute_4.cpp
// compile with: /c /clr
using namespace System;
[attribute(AttributeTargets::Class)]
ref struct ABC {
   ABC(Type ^) {}
};

[ABC(String::typeid)]   // typeid operator yields System::Type ^
ref class MyClass {};
```

## <a name="example"></a>範例

`Inherited`具名引數會指定是否在基底類別上套用的自訂屬性會顯示在衍生類別的反映。

```cpp
// cpp_attr_ref_attribute_5.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

[attribute( AttributeTargets::Method, Inherited=false )]
ref class BaseOnlyAttribute { };

[attribute( AttributeTargets::Method, Inherited=true )]
ref class DerivedTooAttribute { };

ref struct IBase {
public:
   [BaseOnly, DerivedToo]
   virtual void meth() {}
};

// Reflection on Derived::meth will show DerivedTooAttribute
// but not BaseOnlyAttribute.
ref class Derived : public IBase {
public:
   virtual void meth() override {}
};

int main() {
   IBase ^ pIB = gcnew Derived;

   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );
   Console::WriteLine( pObjs->Length ) ;
}
```

```Output
2
```

## <a name="see-also"></a>另請參閱

[依字母順序排列的屬性參考](attributes-alphabetical-reference.md)  
