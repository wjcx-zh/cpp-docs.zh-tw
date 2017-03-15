---
title: "auto_handle::operator= | Microsoft Docs"
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
  - "auto_handle::operator="
  - "msclr.auto_handle.operator="
  - "msclr::auto_handle::operator="
  - "auto_handle.operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::operator="
ms.assetid: 503ca172-e766-4a78-af98-36fd48c931ee
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::operator=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派運算子。  
  
## 語法  
  
```  
auto_handle<_element_type> % operator=(  
   auto_handle<_element_type> % _right  
);  
template<typename _other_type>  
auto_handle<_element_type> % operator=(  
   auto_handle<_other_type> % _right  
);  
```  
  
#### 參數  
 `_right`  
 將指定的 `auto_handle` 套用至目前 `auto_handle`。  
  
## 傳回值  
 目前的 `auto_handle`，現在擁有 `_right`。  
  
## 範例  
  
```  
// msl_auto_handle_op_assign.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:  
   String^ m_s;     
public:  
   ClassA(String^ s) : m_s(s) {  
      Console::WriteLine( "in ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "in ClassA destructor: " + m_s );  
   }  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:     
   ClassB( String^ s ) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main()  
{  
   auto_handle<ClassA> a;  
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );  
   a = a2; // assign from same type  
   a->PrintHello();  
  
   auto_handle<ClassB> b(gcnew ClassB( "second" ) );     
   b->PrintHello();  
   a = b; // assign from derived type     
   a->PrintHello();  
  
   Console::WriteLine("done");  
}  
```  
  
  **in ClassA constructor:first**  
**Hello from first A\!**  
**in ClassA constructor: second**  
**Hello from second B\!**  
**in ClassA destructor:first**  
**Hello from second A\!**  
**done**  
**in ClassA destructor: second**   
## 需求  
 **標頭檔** \<msclr \\ auto\_handle.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_handle 成員](../dotnet/auto-handle-members.md)