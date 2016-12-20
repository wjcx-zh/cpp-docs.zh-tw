---
title: "sealed  (C++ Component Extensions) | Microsoft Docs"
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
  - "sealed_cpp"
  - "sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed keyword [C++]"
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sealed  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`sealed` 是表示不能覆寫虛擬成員、或類型不能用做基底類型的 ref 類別內容相關性關鍵字。  
  
> [!NOTE]
>  ISO C\+\+11 標準語言有 Visual Studio 支援的[最終](../cpp/final-specifier.md)關鍵字。  在標準類別上使用 `final` 而在 ref 類別上使用`sealed`。  
  
## 所有執行階段  
 **語法**  
  
```  
  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
  
```  
  
 **參數**  
  
 *識別項*  
 函式或類別的名稱。  
  
 *傳回類型*  
 由函數傳回的類型。  
  
 **備註**  
  
 在第一個語法範例中，已密封類別。  在第二個範例中，已密封虛擬函式。  
  
 `sealed` 關鍵字對原生目標有效，也對 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和 Common Language Runtime \(CLR\) 有效。  如需詳細資訊，請參閱[覆寫規範和原生編譯](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 您可以在編譯時期使用 `__is_sealed (``type``)` 類型特性來偵測是否已密封類型。  如需詳細資訊，請參閱[Compiler Support for Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。  
  
 `sealed` 是即時線上關鍵字。  如需詳細資訊，請參閱[視內容而有所區別的關鍵字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 請參閱 [Ref 類別及結構](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx)。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 \(這個語言功能沒有只適用於 Common Language Runtime 的備註。\)  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 這個程式碼範例顯示 `sealed` 在虛擬成員上的效果。  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
 **輸出**  
  
  **I1::f 的 X::f 覆寫**  
 **I1::g 的 X::f 覆寫**  
 **I1::f 的 Y::f 覆寫** 下一步的程式碼範例示範如何將類別標示為已密封。  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)