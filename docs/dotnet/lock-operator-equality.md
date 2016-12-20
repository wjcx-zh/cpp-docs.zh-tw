---
title: "lock::operator== | Microsoft Docs"
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
  - "lock::operator=="
  - "msclr.lock.operator=="
  - "msclr::lock::operator=="
  - "lock.operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock::operator=="
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
caps.latest.revision: 6
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock::operator==
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

等號比較運算子。  
  
## 語法  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### 參數  
 `t`  
 要比較是否相等的物件。  
  
## 傳回值  
 如果 `t` 和鎖定的物件相同則傳回 `true`，否則傳回 `false`。  
  
## 範例  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
  **Equal\!**   
## 需求  
 **標頭檔** \<msclr\\lock.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [lock 成員](../dotnet/lock-members.md)   
 [lock::operator\!\=](../dotnet/lock-operator-inequality.md)