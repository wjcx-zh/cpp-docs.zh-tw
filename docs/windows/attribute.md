---
title: 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9826b689e2b8a640efe66e8625b97b3cec347acf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="attribute"></a>屬性
可讓您建立的自訂屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *AllowOn*  
 指定自訂屬性可以套用的語言項目。 預設值是**System::AttributeTargets::All** (請參閱[System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx))。  
  
 `AllowMultiple`  
 指定是否套用自訂屬性可以重複到建構函式。 預設值是**FALSE**。  
  
 `Inherited`  
 指出屬性是否會繼承由子類別。 編譯器不提供特殊支援這項功能。屬性取用者 （例如反映） 的工作是遵守這項資訊。 如果`Inherited`是**TRUE**，繼承屬性。 如果`AllowMultiple`是**TRUE**，屬性將會累積在衍生的成員; 如果`AllowMultiple`是**FALSE**，屬性會覆寫 （或取代） 繼承中。 如果`Inherited`是**FALSE**，都不會繼承屬性。 預設值是**TRUE**。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  `attribute`屬性現在已被取代。  使用 common language runtime 屬性 System.Attribute 直接建立使用者定義的屬性。  如需詳細資訊，請參閱[使用者定義的屬性](../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 您定義[自訂屬性](../windows/custom-attributes-cpp.md)放入`attribute`上受管理的類別或結構定義的屬性。 類別的名稱會是自訂的屬性。 例如:   
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 定義稱為 MyAttr 可以套用至函式參數的屬性。 類別必須是公用，如果屬性要使用的其他組件中。  
  
> [!NOTE]
>  若要避免命名空間衝突，所有的屬性名稱隱含結尾 「 屬性 」。在此範例中，屬性和類別名稱實際上 MyAttrAttribute 但 MyAttr 和 MyAttrAttribute 可以交換使用。  
  
 類別的公用建構函式定義屬性的未命名的參數。 多載建構函式可讓多種方式來指定屬性，因此會為自訂屬性定義以下列方式：  
  
```  
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
  
```  
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
  
 如需可能屬性參數類型的清單，請參閱[自訂屬性](../windows/custom-attributes-cpp.md)。  
  
 請參閱[使用者定義的屬性](../windows/user-defined-attributes-cpp-component-extensions.md)的屬性目標的討論。  
  
 `attribute`屬性有`AllowMultiple`指定自訂屬性是否為單一用途的參數或 multiuse （可出現一次以上相同的實體）。  
  
```  
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
  
 自訂屬性的類別會直接或間接衍生自<xref:System.ComponentModel.AttributeCollection.%23ctor%2A>，讓識別屬性定義快速、 輕鬆地中繼資料中的。 `attribute`屬性隱含繼承自 system:: attribute，因此不需要明確衍生：  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 相當於  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` 是的別名<xref:System.AttributeUsageAttribute?displayProperty=fullName>(不 AttributeAttribute; 這是屬性的命名規則的例外狀況)。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`ref` **類別**， **ref 結構**|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 `Inherited`具名引數會指定是否套用基底類別上的自訂屬性會顯示在衍生類別的反映。  
  
```  
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
 [依字母順序排列的屬性參考](../windows/attributes-alphabetical-reference.md)   
 [自訂屬性](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)