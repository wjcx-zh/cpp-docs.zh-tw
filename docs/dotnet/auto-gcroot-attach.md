---
title: "auto_gcroot::attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_gcroot.attach"
  - "auto_gcroot::attach"
  - "msclr::auto_gcroot::attach"
  - "msclr.auto_gcroot.attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::attach"
ms.assetid: 996ede65-bcb5-41f2-bfbf-507f8a578241
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# auto_gcroot::attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

附加`auto_gcroot`到一個物件。  
  
## 語法  
  
```  
auto_gcroot<_element_type> & attach(  
   _element_type _right  
);  
auto_gcroot<_element_type> & attach(  
   auto_gcroot<_element_type> & _right  
);  
template<typename _other_type>  
auto_gcroot<_element_type> & attach(  
   auto_gcroot<_other_type> & _right  
);  
```  
  
#### 參數  
 `_right`  
 要附加的物件或包含要附加的 `auto_gcroot` 物件。  
  
## 傳回值  
 目前的 `auto_gcroot`。  
  
## 備註  
 如果 `_right` 是 `auto_gcroot`，它會釋放物件的擁有權，在物件附加到目前 `auto_gcroot`之前。  
  
## 範例  
  
```  
// msl_auto_gcroot_attach.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:     
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "in ClassA constructor:" + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "in ClassA destructor:" + m_s );  
   }  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:  
   ClassB( String ^ s) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main() {  
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );  
   a->PrintHello();  
   a.attach( gcnew ClassA( "second" ) ); // attach same type  
   a->PrintHello();  
   ClassA^ ha = gcnew ClassA( "third" );  
   a.attach( ha ); // attach raw handle  
   a->PrintHello();  
   auto_gcroot<ClassB^> b( gcnew ClassB("fourth") );  
   b->PrintHello();  
   a.attach( b ); // attach derived type  
   a->PrintHello();  
}  
```  
  
  **in ClassA constructor:first**  
**Hello from first A\!**  
**在ClassA constructor: second**  
**in ClassA destructor:first**  
**Hello from second A\!**  
**在 ClassA 建構函式: 第三個**  
**在ClassA destructor: second**  
**Hello 從第三個 A\!**  
**在 ClassA 建構函式: 第四個**  
**Hello 從第四個 B\!**  
**在 ClassA 解構函式: 第三個**  
**Hello 從第四個 A\!**  
**在 ClassA 解構函式: 第四個**   
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator\=](../dotnet/auto-gcroot-operator-assign.md)   
 [auto\_gcroot::release](../dotnet/auto-gcroot-release.md)