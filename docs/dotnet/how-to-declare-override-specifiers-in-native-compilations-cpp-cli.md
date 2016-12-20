---
title: "如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "原生編譯中的覆寫指定名稱，覆寫"
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在原生編譯中宣告覆寫指定名稱 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[密封](../windows/sealed-cpp-component-extensions.md)、 [摘要](../windows/abstract-cpp-component-extensions.md)和 [覆寫](../windows/override-cpp-component-extensions.md) 可以在不使用 **\/ZW** 或 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)的編輯。  
  
> [!NOTE]
>  C\+\+11 ISO 標準語言有 [覆寫](../cpp/override-specifier.md) 識別項和 [最後](../cpp/final-specifier.md) 識別項，，和兩個 Visual Studio 支援使用 `final` 而非 `sealed` 會被視為編譯為原生的程式碼。  
  
## 範例  
  
### 說明  
 下列範例中， `sealed` 是有效原生編譯。  
  
### 程式碼  
  
```  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## 範例  
  
### 說明  
 下面的範例會表示為 `override` ，表示在原生編譯。  
  
### 程式碼  
  
```  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## 範例  
  
### 說明  
 這個範例中， `abstract` 是有效原生編譯。  
  
### 程式碼  
  
```  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## 請參閱  
 [覆寫規範](../windows/override-specifiers-cpp-component-extensions.md)