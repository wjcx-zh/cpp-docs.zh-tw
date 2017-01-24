---
title: "auto_gcroot::operator! | Microsoft Docs"
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
  - "msclr.auto_gcroot.operator!"
  - "auto_gcroot.operator!"
  - "msclr::auto_gcroot::operator!"
  - "auto_gcroot::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::operator!"
ms.assetid: f9728be3-2e09-4c01-a594-43e0d59d40d3
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

運算子用於 `auto_gcroot` 條件運算式。  
  
## 語法  
  
```  
bool operator!() const;  
```  
  
## 傳回值  
 `true` ，如果包裝的物件無效;否則為 `false` 。  
  
## 範例  
  
```  
// msl_auto_gcroot_operator_not.cpp  
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
  
  **的無效**  
**現在的有效**  
**現在的無效**   
## 需求  
 **標頭檔** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [auto\_gcroot 成員](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator bool](../dotnet/auto-gcroot-operator-bool.md)