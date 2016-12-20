---
title: "swap 函式 (auto_handle) | Microsoft Docs"
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
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# swap 函式 (auto_handle)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 `auto_handle` 之間交換物件。  
  
## 語法  
  
```  
template<typename _element_type>  
void swap(  
   auto_handle<_element_type> % _left,  
   auto_handle<_element_type> % _right  
);  
```  
  
#### 參數  
 `_left`  
 `auto_handle`。  
  
 `_right`  
 另一個 `auto_handle`。  
  
## 範例  
  
```  
// msl_swap_auto_handle.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1 = "string one";  
   auto_handle<String> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   swap( s1, s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
  **s1 \= 「字串一」， s2 \= 「字串二」**  
**s1 \= 「字串二」， s2 \= 「字串一」**   
## 需求  
 **標頭檔** \<msclr \\ auto\_handle.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_handle](../dotnet/auto-handle.md)   
 [auto\_handle::swap](../dotnet/auto-handle-swap.md)