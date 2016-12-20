---
title: "auto_gcroot::operator bool | Microsoft Docs"
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
  - "auto_gcroot.operator bool"
  - "auto_gcroot::operator bool"
  - "msclr.auto_gcroot.operator bool"
  - "msclr::auto_gcroot::operator bool"
  - "operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bool 運算子"
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在條件運算式中用於 `auto_gcroot` 的運算子。  
  
## 語法  
  
```  
operator bool() const;  
```  
  
## 傳回值  
 如果包起的物件有效，則為 `true`，否則為 `false`。  
  
## 備註  
 比 `bool` 安全性的這個運算子實際上會轉換成 `_detail_class::_safe_bool` ，因為它無法轉換為整數型別。  
  
## 範例  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
  **s 無效。**  
**現在的 s 有效**  
**現在的 s 無效**   
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator\!](../dotnet/auto-gcroot-operator-logical-not.md)