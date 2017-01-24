---
title: "typeid (C++ 元件擴充功能) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "typeid 關鍵字 [C++]"
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
caps.latest.revision: 35
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typeid (C++ 元件擴充功能)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得值，這個值表示物件的型別。  
  
> [!WARNING]
>  本主題是關於 typeid 的 C\+\+ 元件擴充功能版本。  如需此範例的 ISO C\+\+ 版本的關鍵字，請參閱[typeid 運算子](../cpp/typeid-operator.md)。  
  
## 所有執行階段  
  
### 語法  
  
```cpp  
  
T::typeid  
```  
  
### 參數  
 *T*  
 型別名稱。  
  
## Windows 執行階段  
  
### 語法  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### 參數  
 `T`  
 型別名稱。  
  
### 備註  
 在 [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)] 中，typeid 會傳回從執行階段型別資訊建構的 [Platform::Type](../Topic/Platform::Type%20Class.md)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **語法**  
  
```  
  
type::typeid  
```  
  
 **參數**  
  
 *type*  
 您要為 System::Type 物件設定之型別 \(抽象宣告子\) 的名稱。  
  
 **備註**  
  
 `typeid` 在編譯時期用來取得型別的 <xref:System.Type>。  
  
 `typeid` 類似於使用 <xref:System.Type.GetType%2A> 或 <xref:System.Object.GetType%2A>，在執行階段取得型別的 System::Type。  不過，typeid 只接受型別名稱做為參數。如果您想要型別的執行個體取得其 System::Type 名稱，請使用 GetType。  
  
 `typeid` 必須能夠在編譯時期評估型別名稱 \(型別\)，而 GetType 會評估要在執行階段傳回的型別。  
  
 `typeid` 可以接受原生型別名稱或原生型別名稱的 Common Language Runtime 別名。如需詳細資訊，請參閱[C\+\+ 原生類型的 .NET Framework 對應項](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)。  
  
 `typeid` 也會使用原生型別，但是仍將傳回 System::Type。若要取得 type\_info 結構，請使用 [typeid 運算子](../cpp/typeid-operator.md)。  
  
 `typeid` 在先前的 **\/clr** 語法中是 [\_\_typeof](../misc/typeof.md) 的後置項。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列範例會將 typeid 關鍵字與 GetType\(\) 成員進行比較。  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **Output**  
  
  **typeid 和 GetType 傳回了相同的 System::Type**  
**G**  
 **System.Single\*** **範例**  
  
 下列範例顯示，System::Type 型別的變數可以用來取得型別的屬性。這也表示，您必須為某些型別建立 typedef，才能使用 `typeid`。  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **Output**  
  
  **True**  
 **在 AtClass2 建構函式中**  
 **在 AtClass Type ^ 建構函式中**  
 **AtClass2**  
 **System.AttributeUsageAttribute**  
 **AtClass**  
 **int::typeid \!\= pointer\_to\_int::typeid，一如預期**  
 **int::typeid \=\= handle\_to\_int::typeid，一如預期**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)