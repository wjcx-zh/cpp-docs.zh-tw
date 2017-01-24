---
title: "編譯器警告 (層級 4) C4239 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4239"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4239"
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4239
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 'token' : 從 'type' 轉換至 'type'  
  
 C\+\+ 標準不允許這種型別轉換，但在此處被視為擴充功能而允許進行。  此警告之後一定至少會有一行描述違反語言規則的說明。  
  
## 範例  
 下列範例會產生 C4239。  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## 範例  
 嚴格禁止將整數型別轉換成列舉型別。  
  
 下列範例會產生 C4239。  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```