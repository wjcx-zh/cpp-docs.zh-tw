---
title: "auto_handle::~auto_handle | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_handle.~auto_handle"
  - "msclr.auto_handle.~auto_handle"
  - "auto_handle::~auto_handle"
  - "~auto_handle"
  - "msclr::auto_handle::~auto_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::~auto_handle"
ms.assetid: e83e95a8-015b-4f27-ad63-70efb3690726
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::~auto_handle
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`auto_handle` 解構函式。  
  
## 語法  
  
```  
~auto_handle();  
```  
  
## 備註  
 解構函式也會被主控物件。  
  
## 範例  
  
```  
// msl_auto_handle_dtor.cpp  
// compile with: /clr  
#include "msclr\auto_handle.h"  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
public:  
   ClassA() { Console::WriteLine( "ClassA constructor" ); }  
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }  
};  
  
int main()  
{  
   // create a new scope for a:  
   {  
      auto_handle<ClassA> a = gcnew ClassA;  
   }  
   // a goes out of scope here, invoking its destructor  
   // which in turns destructs the ClassA object.  
  
   Console::WriteLine( "done" );  
}  
```  
  
  **ClassA 建構函式**  
**ClassA 解構函式**  
**done**   
## 需求  
 **標頭檔** \<msclr \\ auto\_handle.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_handle 成員](../dotnet/auto-handle-members.md)   
 [auto\_handle::release](../dotnet/auto-handle-release.md)   
 [auto\_handle::auto\_handle](../dotnet/auto-handle-auto-handle.md)