---
title: "User-Defined Attributes  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "metadata, extending"
  - "custom attributes, extending metadata"
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
caps.latest.revision: 27
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# User-Defined Attributes  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂屬性可讓您擴充介面的中繼資料、類別或結構、方法、參數或列舉型別。  
  
## 所有執行階段  
 所有執行階段支援自訂屬性。  
  
## Windows Runtime \- Windows 執行階段  
 C\+\+\/C 屬性僅支援屬性，不過，沒有屬性的建構函式或方法。  
  
### 備註  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 自訂屬性可以讓您擴充 Managed 項目的中繼資料。  如需詳細資訊，請參閱[屬性](../Topic/Extending%20Metadata%20Using%20Attributes.md)。  
  
### 備註  
 本主題和語法提出的資訊視為代替 [attribute](../windows/attribute.md)中顯示的資訊。  
  
 您可以定義型別且 <xref:System.Attribute> 型別的基底類別和選擇性套用 <xref:System.AttributeUsageAttribute> 屬性定義自訂屬性。  
  
 例如，在 Microsoft 交易 Server \(MTS\) 1.0，如需交易的行為，同步，負載平衡，依此類推使用 ODL 自訂屬性將自訂 GUID 指定的插入至型別程式庫。  因此， MTS 伺服器的用戶端可以讀取型別判斷其特性程式庫。  在 .NET Framework 中，這個型別程式庫的類比是中繼資料，因此，ODL 自訂屬性的型別會是自訂屬性。  此外，讀取型別程式庫類似於使用型別上的反應。  
  
 如需詳細資訊，請參閱：  
  
-   [Attribute Targets](../windows/attribute-targets-cpp-component-extensions.md)  
  
-   [Attribute Parameter Types](../windows/attribute-parameter-types-cpp-component-extensions.md)  
  
 如需在 Visual C\+\+ 專案中簽署組件的詳細資訊，請參閱[強式名稱組件 \(組件簽署\)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例顯示如何定義一個自訂屬性：  
  
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
  
 下列範例說明如何自訂屬性的一些重要功能。  例如，這個範例顯示自訂屬性的常見用法: 具現化可完整描述自己給用戶端的伺服器。  
  
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
  
 **Output**  
  
  **Service Priority \= 0**  
 **Service Access \= Write**  
 **Service Priority \= 3**  
 **Service Access \= Write**  
 **Service Priority \= 1**  
 **Service Access \= Read** **範例**  
  
 Object^ 型別取代不同的資料型別。  下列範例會定義取得陣列 Object^ 做為參數的自訂屬性。  
  
 屬性引數必須是編譯時期常數；在大部分情況下，它們應該是常數的文字。  
  
 請參閱 [typeid](../windows/typeid-cpp-component-extensions.md) 知道如何從自訂屬性區塊中傳回 System::Type 值的資訊。  
  
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
  
 執行階段需要自訂屬性類別的 public 區段必須可序列化。當建立自訂屬性時，您的自訂屬性的具名引數僅限於編譯時期常數。\(想像為位元組序列附加至中繼資料的類別配置\)。  
  
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
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)