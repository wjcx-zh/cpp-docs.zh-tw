---
title: "使用者定義屬性 （c + + 元件擴充功能） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d974e8526f983801ed011520f7f78ff8c6cb564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-attributes--c-component-extensions"></a>使用者定義屬性 (C++ 元件擴充功能)
自訂屬性可讓您擴充的介面、 類別或結構、 方法、 參數或列舉型別中繼資料。  
  
## <a name="all-runtimes"></a>所有執行階段  
 所有執行階段支援的自訂屬性。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 C + + /CX 屬性支援只有屬性，但不是屬性建構函式或方法。  
  
### <a name="remarks"></a>備註  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 自訂屬性可以讓您擴充的受管理的項目中繼資料。 如需詳細資訊，請參閱[屬性](/dotnet/standard/attributes/index)。  
  
### <a name="remarks"></a>備註  
 此主題中呈現的語法與資訊用來取代所顯示的資訊[屬性](../windows/attribute.md)。  
  
 您可以定義自訂屬性定義型別，並進行<xref:System.Attribute>基底類別的類型和選擇性地套用<xref:System.AttributeUsageAttribute>屬性。  
  
 比方說，在 Microsoft 交易伺服器 (MTS) 1.0，同步處理的交易而言，行為負載平衡，並透過自訂插入使用 ODL 自訂屬性的型別程式庫的 Guid 指定等等。 因此，MTS 伺服器的用戶端無法讀取類型程式庫來判斷其特性。 在.NET Framework 中，類型程式庫的類比是中繼資料，而 ODL 自訂屬性的類比是自訂屬性。 此外，讀取類型程式庫是類似於使用反映的類型。  
  
 如需詳細資訊，請參閱：  
  
-   [屬性目標](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [屬性參數類型](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 Visual c + + 中的簽署組件上的資訊，請參閱[強式名稱組件 （組件簽署） (C + + /CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**  
  
### <a name="examples"></a>範例  
 **範例**  
  
 下列範例會示範如何定義自訂屬性。  
  
```cpp  
// user_defined_attributes.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
ref struct Attr : public Attribute {  
   Attr(bool i){}  
   Attr(){}  
};  
  
[Attr]  
ref class MyClass {};  
```  
  
 **範例**  
  
 下列範例將說明一些重要功能的自訂屬性。 例如，此範例示範常見的自訂屬性的用法： 具現化完整用戶端描述自己的伺服器。  
  
```cpp  
// extending_metadata_b.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
  
public enum class Access { Read, Write, Execute };  
  
// Defining the Job attribute:  
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]  
public ref class Job : Attribute {  
public:  
   property int Priority {  
      void set( int value ) { m_Priority = value; }  
      int get() { return m_Priority; }  
   }  
  
   // You can overload constructors to specify Job attribute in different ways  
   Job() { m_Access = Access::Read; }  
   Job( Access a ) { m_Access = a; }  
   Access m_Access;  
  
protected:  
   int m_Priority;  
};  
  
interface struct IService {  
   void Run();  
};  
  
   // Using the Job attribute:  
   // Here we specify that QueryService is to be read only with a priority of 2.  
   // To prevent namespace collisions, all custom attributes implicitly   
   // end with "Attribute".   
  
[Job( Access::Read, Priority=2 )]  
ref struct QueryService : public IService {  
   virtual void Run() {}  
};  
  
// Because we said AllowMultiple=true, we can add multiple attributes   
[Job(Access::Read, Priority=1)]  
[Job(Access::Write, Priority=3)]  
ref struct StatsGenerator : public IService {  
   virtual void Run( ) {}  
};  
  
int main() {  
   IService ^ pIS;  
   QueryService ^ pQS = gcnew QueryService;  
   StatsGenerator ^ pSG = gcnew StatsGenerator;  
  
   //  use QueryService  
   pIS = safe_cast<IService ^>( pQS );  
  
   // use StatsGenerator  
   pIS = safe_cast<IService ^>( pSG );  
  
   // Reflection  
   MemberInfo ^ pMI = pIS->GetType();  
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);  
  
   // We can now quickly and easily view custom attributes for an   
   // Object through Reflection */  
   for( int i = 0; i < pObjs->Length; i++ ) {  
      Console::Write("Service Priority = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);  
      Console::Write("Service Access = ");  
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);  
   }  
}  
```  
  
 **輸出**  
  
```Output  
Service Priority = 0  
  
Service Access = Write  
  
Service Priority = 3  
  
Service Access = Write  
  
Service Priority = 1  
  
Service Access = Read  
```  
  
 **範例**  
  
 物件 ^ 類型會取代 variant 資料類型。 下列範例會定義的自訂屬性，會採用物件的陣列 ^ 做為參數。  
  
 屬性引數必須是編譯時間常數。在大部分情況下，它們應該是常數常值。  
  
 請參閱[typeid](../windows/typeid-cpp-component-extensions.md)如需有關如何從自訂屬性區塊中傳回值為 system:: type 資訊。  
  
```cpp  
// extending_metadata_e.cpp  
// compile with: /clr /c  
using namespace System;  
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]  
public ref class AnotherAttr : public Attribute {  
public:  
   AnotherAttr(array<Object^>^) {}  
   array<Object^>^ var1;  
};  
  
// applying the attribute  
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]  
public ref class SomeClass {};  
```  
  
 **範例**  
  
 執行階段需要之公開部分的自訂屬性類別必須是可序列化。  撰寫自訂屬性時，您的自訂屬性的具名引數會受限於編譯時間常數。  （將其視為附加至您的類別配置的中繼資料中的位元的序列。）  
  
```cpp  
// extending_metadata_f.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct abc {};  
  
[AttributeUsage( AttributeTargets::All )]  
ref struct A : Attribute {  
   A( Type^ ) {}  
   A( String ^ ) {}  
   A( int ) {}  
};  
  
[A( abc::typeid )]  
ref struct B {};  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)