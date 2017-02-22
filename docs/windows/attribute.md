---
title: "attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.attribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof keyword"
  - "custom attributes, creating"
  - "attribute attribute"
  - "attributes [C++], custom"
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# attribute
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可讓您建立自訂屬性。  
  
## 語法  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### 參數  
 *AllowOn*  
 指定自訂的屬性可以套用的語言項目。  預設值是 **System::AttributeTargets::All** \(請參閱 [System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)\)。  
  
 `AllowMultiple`  
 指定是否這個自訂屬性可以套用重複到建構函式。  預設值是 **，則為 FALSE**。  
  
 `Inherited`  
 表示屬性是否是由子類別所繼承。  編譯器不提供特殊支援這項功能。 他必須的屬性消費者 \(例如反映\) 應遵守這項資訊。  如果`Inherited`是 **，則為 TRUE**，繼承屬性。  如果`AllowMultiple`是 **，則為 TRUE**，屬性會累積在衍生的成員。 如果`AllowMultiple`是 **，則為 FALSE**，該屬性會覆寫 \(或取代\) 中繼承。  如果`Inherited`是 **，則為 FALSE**，都不會繼承屬性。  預設值是 **，則為 TRUE**。  
  
## 備註  
  
> [!NOTE]
>  `attribute`屬性現在已被取代。  您可以使用的通用語言執行階段屬性 System.Attribute 直接建立使用者定義的屬性。  如需詳細資訊，請參閱 [User\-Defined Attributes](../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
 您定義[的自訂屬性](../windows/custom-attributes-cpp.md)藉由放置`attribute`上的受管理的類別或結構定義的屬性。  類別的名稱是自訂的屬性。  例如：  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 定義可套用至函式參數的 MyAttr 屬性。  類別必須是公用，如果屬性要在其他組件中使用。  
  
> [!NOTE]
>  若要防止發生命名空間衝突時，所有的屬性名稱隱含以結束 「 屬性 」; 在這個範例中，屬性和類別名稱實際上是 MyAttrAttribute，但 MyAttr 和 MyAttrAttribute 可以交換使用。  
  
 此類別的公用建構函式定義的屬性未命名的參數。  多載建構函式可讓多種方式可以指定這個屬性，因此是一個自訂屬性定義如下：  
  
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
  
 此類別的公用資料成員和屬性是屬性的選擇性的具名的參數：  
  
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
  
 如需可能的屬性參數型別的清單，請參閱[自訂屬性](../windows/custom-attributes-cpp.md)。  
  
 請參閱[User\-Defined Attributes](../windows/user-defined-attributes-cpp-component-extensions.md)的屬性目標的討論。  
  
 `attribute`屬性有`AllowMultiple`指定的自訂屬性是否為每次使用的參數或 multiuse \(可以出現多次相同的實體\)。  
  
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
  
 自訂屬性類別會直接或間接衍生自<xref:System.ComponentModel.AttributeCollection.%23ctor%2A>，因此可以用來識別快速又簡單的中繼資料中的屬性定義。  `attribute`屬性表示 System::Attribute，繼承，因此不需要明確的衍生：  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 相等於  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute`為<xref:System.AttributeUsageAttribute?displayProperty=fullName> \(不是 AttributeAttribute。 這是屬性的命名規則的例外狀況\)。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`ref` **類別**，  **ref 結構**|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 範例  
  
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
  
## 範例  
 `Inherited`具名引數會指定基底類別中所套用的自訂屬性是否會出現在衍生類別的反映。  
  
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
  
  **2**   
## 請參閱  
 [Attributes Alphabetical Reference](../windows/attributes-alphabetical-reference.md)   
 [Custom Attributes](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)