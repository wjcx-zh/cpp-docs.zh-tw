---
title: "swap 函式 (auto_gcroot) | Microsoft Docs"
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
  - "msclr::swap"
  - "msclr.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap 函式"
ms.assetid: 2fe8146b-a7f7-445a-9ae9-53b5556be701
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# swap 函式 (auto_gcroot)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 `auto_gcroot` 之間交換物件。  
  
## 語法  
  
```  
template<typename _element_type>  
void swap(  
   auto_gcroot<_element_type> & _left,  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### 參數  
 `_left`  
 `auto_gcroot`。  
  
 `_right`  
 另一個 `auto_gcroot`。  
  
## 範例  
  
```  
// msl_swap_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   swap( s1, s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
  **s1 \= 'string one', s2 \= 'string two'**  
**s1 \= 'string two', s2 \= 'string one'**   
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot](../dotnet/auto-gcroot.md)   
 [auto\_gcroot::swap](../dotnet/auto-gcroot-swap.md)