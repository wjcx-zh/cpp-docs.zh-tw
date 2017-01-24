---
title: "lock::operator!= | Microsoft Docs"
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
  - "lock.operator!="
  - "msclr.lock.operator!="
  - "msclr::lock::operator!="
  - "lock::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::operator!="
ms.assetid: ed1d674e-9ee9-4257-8a7e-2e3567d50222
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::operator!=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不等比較運算子。  
  
## 語法  
  
```  
template<class T> bool operator!=(  
   T t  
);  
```  
  
#### 參數  
 `t`  
 要比較的物件是否不相等。  
  
## 傳回值  
 傳回 `true` ，如果 `t` 等於鎖定的物件不同，否則為 `false` 。  
  
## 範例  
  
```  
// msl_lock_op_ineq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   Object^ o2 = gcnew Object;  
   lock l1(o1);  
   if (l1 != o2) {  
      Console::WriteLine("Inequal!");  
   }  
}  
```  
  
  **不相等\!**   
## 需求  
 **標頭檔** \<msclr \\ lock.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::operator\=\=](../dotnet/lock-operator-equality.md)