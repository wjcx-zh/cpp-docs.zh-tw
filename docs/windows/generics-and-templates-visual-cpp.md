---
title: "Generics and Templates (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "generics [C++], vs. templates"
  - "templates, C++"
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generics and Templates (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

泛型和樣板都是支援參數型型別的語言功能。  但是，它們不同而有不同的用途。  本主題將概要說明許多不同。  
  
 如需詳細資訊，請參閱[Windows Runtime and Managed Templates](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)與[樣板概觀](../Topic/Templates%20Overview.md)。  
  
## 比較範本和泛型  
 樣板和泛型之間的主要差異  
  
-   泛型是泛型，直到型別使用它們會在執行階段取代。  樣板特製化在編譯時期，因此它們仍然不是在執行階段的參數型型別  
  
-   Common Language Runtime 專門支援 MSIL 中的泛型。  由於執行階段知道泛型，特定型別可以是泛型型別會替代，當參考包含泛型型別的組件。  範本，相反地，在編譯時期解析成泛型型別，而且產生的型別不可以是專門用來其他組件。  
  
-   具有相同型別的引數之兩個不同組件特製化的泛型型別相同。  具有相同型別的引數之兩個不同組件特製化的樣板執行階段視為不同的型別。  
  
-   泛型會以對所有參考型別引數使用可執行的單一片段程式碼 \(這不適用於實值型別，都有唯一的實作每個實值型別\)。  JIT 編譯器知道使用做為型別引數的泛型且可最佳化參考或實值型別的程式碼。  範本會產生每個特製化的執行階段程式碼。  
  
-   泛型不允許非型別樣板參數，例如 `template <int i> C {}`。  範本允許它們。  
  
-   泛型不允許明確特製化\(意即自訂特定型別的樣板實作\)。  範本  
  
-   泛型不允許部分特製化\(意即自訂型別引數子集的實作\)。  範本  
  
-   泛型不允許將型別參數當做泛型型別的基底類別使用。  範本  
  
-   樣板支援樣板樣板參數 \(如:   `template<template<class T> class X> class MyClass`\)，而不是泛型。  
  
## 結合範本和泛型  
  
-   在泛型的基本差異有合併範本和泛型建置應用程式的影響。  例如，假設您有一個樣板類別要建立泛用包裝函式來公開該範本以其他語言為泛型。  您不能有泛型雖然接受型別的參數則會傳遞至範本，因為範本需要有該型別參數在編譯時期，不過，一般不會解析型別參數在執行階段內。  巢狀於泛型內的範本無法運作，因為無法展開範本就能在執行階段的選擇性泛型型別的編譯時期。  
  
## 範例  
  
### 說明  
 下列範例會顯示一個簡單的範例範本和泛型。  在此範例中，範本類別傳遞其參數為泛型型別。  反轉是不可能的。  
  
 可使用這個慣用語，當您在與是在 Visual C\+\+ 組件的範本程式碼中現有的泛型應用程式開發介面要建置，或者，當您需要將參數化額外層到泛型型別，利用泛型不支援範本的某些功能。  
  
### 程式碼  
  
```  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### Output  
  
```  
F  
```  
  
## 請參閱  
 [Generics](../windows/generics-cpp-component-extensions.md)