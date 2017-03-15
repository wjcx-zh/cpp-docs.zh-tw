---
title: "auto_gcroot::release | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_gcroot::release"
  - "auto_gcroot::release"
  - "auto_gcroot.release"
  - "msclr.auto_gcroot.release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "release 方法"
ms.assetid: 40b253f0-154e-4d79-80a4-ff13199c3ff0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# auto_gcroot::release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 `auto_gcroot` 管理釋放物件。  
  
## 語法  
  
```  
_element_type release();  
```  
  
## 傳回值  
 釋放的物件。  
  
## 範例  
  
```  
// msl_auto_gcroot_release.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {  
      Console::WriteLine( "ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "ClassA destructor: " + m_s );  
   }  
  
   void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );     
   }  
};  
  
int main()  
{  
   ClassA^ a;  
  
   // create a new scope:  
   {  
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );  
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );  
      a = agc1.release();  
   }  
   // agc1 and agc2 go out of scope here  
  
   a->PrintHello();  
  
   Console::WriteLine( "done" );  
}  
```  
  
  **ClassA constructor: first**  
**ClassA constructor: second**  
**ClassA destructor: second**  
**Hello from first A\!**  
**done**   
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::~auto\_gcroot](../dotnet/auto-gcroot-tilde-auto-gcroot.md)