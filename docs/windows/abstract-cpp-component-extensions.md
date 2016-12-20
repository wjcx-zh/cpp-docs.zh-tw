---
title: "abstract  (C++ Component Extensions) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "abstract"
  - "abstract_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abstract keyword [C++]"
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# abstract  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`abstract` 關鍵字會宣告以下其中一項：  
  
-   類型可以當做基底類型，但是類型本身無法具現化。  
  
-   類型成員函式只能在衍生的類型中定義。  
  
## 所有平台  
 **語法**  
  
```  
  
class-declaration class-identifier abstract {}  
virtual return-type member-function-identifier() abstract ;  
  
```  
  
 **備註**  
  
 第一個範例語法會將類別宣告為抽象。  *class\-declaration* 元件可以是原生 C\+\+ 宣告 \(`class` 或 `struct`\)，或如果指定了 **\/ZW** 或 **\/clr** 編譯器選項，則可以是 C\+\+ 擴充功能宣告 \(`ref class` 或 `ref struct`\)。  
  
 第二個範例語法會將虛擬成員函式宣告為抽象。  將函式宣告為抽象等同於將它宣告為純虛擬函式。  將成員宣告為抽象也會造成含括類別被宣告為抽象。  
  
 `abstract` 關鍵字支援原生與平台特定程式碼；也就是說，它可以使用或不使用 **\/ZW** 或 **\/clr** 編譯器選項來編譯。  
  
 您可以在編譯時期偵測是否某個類型是具有 `__is_abstract(``type``)` 類型特性的抽象。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `abstract` 關鍵字是內容相關性的覆寫規範。  如需內容相關性關鍵字的詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  如需覆寫規範的詳細資訊，請參閱[作法：在原生編譯中宣告覆寫規範](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 如需詳細資訊，請參閱 [Ref 類別與結構](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例會產生錯誤，因為類別 `X` 標示為 `abstract`。  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **範例**  
  
 下列程式碼範例會產生錯誤，因為它會具現化標示為原生類別的 `abstract`。  無論是否有 **\/clr** 編譯器選項，都會發生此錯誤。  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **範例**  
  
 下列程式碼範例會產生錯誤，因為函式 `f` 包括定義，但標示為 `abstract`。  在範例中的最後一個陳述式會顯示宣告抽象虛擬函式相當於宣告純虛擬函式。  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)