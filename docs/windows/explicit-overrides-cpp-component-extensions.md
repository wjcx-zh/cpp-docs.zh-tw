---
title: "Explicit Overrides  (C++ Component Extensions) | Microsoft Docs"
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
  - "overriding, override [C++]"
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Explicit Overrides  (C++ Component Extensions)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題討論如何明確覆寫基底類別或介面的成員。  應該只用於具名 \(明確\) 覆寫與具有不同名稱的衍生方法中呼叫方法。  
  
## 所有執行階段  
 **語法**  
  
```  
  
        overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **參數**  
  
 *overriding\-function\-declarator*  
 覆寫函式的傳回型別、名稱和引數清單。請注意覆寫函式不能有名稱和要覆寫的函式相同。  
  
 *type*  
 包含函式覆寫的基底型別。  
  
 *function*  
 覆寫的一或多個函式名稱的逗號分隔清單。  
  
 *overriding\-function\-definition*  
 定義覆寫函式的函式主體陳述式。  
  
 **備註**  
  
 建立方法的簽章別名，或提供不同的實作中使用明確覆寫的有相同的簽章的方法。  
  
 如需修改繼承型別和繼承型別成員行為的詳細資訊，請參閱 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **備註**  
  
 如需明確覆寫的資訊以機器碼或程式碼編譯 **\/clr:oldSyntax**，請參閱 [明確覆寫](../cpp/explicit-overrides-cpp.md)。  
  
### 需求  
 編譯器選項：**\/clr**  
  
### 範例  
 **範例**  
  
 下列程式碼範例顯示成員的簡單，隱含覆寫和實作的基底介面，而非使用明確覆寫。  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Output**  
  
  **I1::f 的 X::f 覆寫** **範例**  
  
 下列程式碼範例示範如何使用明確覆寫語法實作具有通用簽章的所有介面成員。  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Output**  
  
  **X::f override of I1::f and I2::f**  
 **X::f override of I1::f and I2::f** **範例**  
  
 下列程式碼範例顯示了函式覆寫方式都有自己從函式不同的名稱實作。  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Output**  
  
  **X::g** **範例**  
  
 下列程式碼範例將示範實作型別安全集合的明確介面實作。  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## 請參閱  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)