---
title: "Generic Functions (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "functions [C++], generic"
  - "generic methods"
  - "generics [C++], functions"
  - "methods [C++], generic"
  - "generic functions"
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generic Functions (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型函式是宣告具有型別參數的函式。  呼叫時，使用實際型別而不是型別參數。  
  
## 所有平台  
 **備註**  
  
 此功能不適用於所有平台。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **備註**  
  
 在[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中不支援此功能。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 泛型函式是宣告具有型別參數的函式。  呼叫時，使用實際型別而不是型別參數。  
  
 **語法**  
  
```  
[attributes] [modifiers]  
return-type identifier <type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{  
   function-body  
}  
```  
  
 **參數**  
  
 *attributes* \(選擇性\)  
 補充宣告資訊。  如需關於屬性及屬性類別的詳細資訊，請參閱屬性。  
  
 *modifiers*\(選擇性的\)  
 函式的修飾詞，例如 `static`。因為虛擬方法不可為泛型，`virtual` 不允許。  
  
 *return\-type*  
 此方法傳回的型別。  如果傳回型別為虛值，則不需要傳回值。  
  
 *identifier*  
 函式名稱。  
  
 *type\-parameter identifier\(s\)*  
 逗號分隔識別項的清單。  
  
 *formal\-parameters* \(選擇性\)  
 參數清單  
  
 *type\-parameter\-constraints\-clauses*  
 這可以用來做為型別引數的型別指定限制，而且會在 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)中指定的表單。  
  
 *function\-body*  
 方法的主體，可能代表型別參數識別項。  
  
 **備註**  
  
 泛型函式是宣告具有泛型型別參數的函式。  它們可能是類別或結構的方法或獨立函式。  單一泛型宣告隱含宣告在不同的實際型別替代只在於泛型型別參數的函式系列。  
  
 在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]中，類別或結構建構函式不可宣告為泛型型別參數。  
  
 呼叫時，實際型別取代泛型型別參數。  這個實際型別在角括弧可能明確指定使用語法類似於樣板函式呼叫。  如果沒用型別參數呼叫，則編譯器會嘗試從在函式呼叫提供的參數推算這個實際型別。  如果預期的型別引數不能從所使用的參數推算得出，編譯器就會報告錯誤。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例示範泛型函式。  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **範例**  
  
 泛型函式可以多載根據簽章或 Arity，函式的型別參數數目。  此外，函式只要在某些不同型別參數，泛型函式可以多載同名的非泛型函式。  例如，可多載下列函式：  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **範例**  
  
 下列範例使用泛型函式尋找陣列的第一個項目。  宣告 `MyClass`，從基底類別`MyBaseClass`繼承。  `MyClass` 包含泛型函式，則為 `MyFunction`，呼叫另一個泛型函式，則為 `MyBaseClassFunction`，在基底類別中。  使用不同的型別引數，在 **main**，泛型函式，則為 `MyFunction` 呼叫。  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **Output**  
  
  **My function returned an int: 2003**  
 **My function returned a string: Hello generic functions\!**   
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)   
 [Generics](../windows/generics-cpp-component-extensions.md)