---
title: "編譯器錯誤 C2511 | Microsoft Docs"
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
  - "C2511"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2511"
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2511
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 在 'class' 找不到多載成員函式  
  
 沒有使用指定參數宣告的函式版本。可能的原因：  
  
1.  傳遞到函式的參數是錯誤的。  
  
2.  參數傳遞的順序錯誤。  
  
3.  參數名稱拼字錯誤。  
  
 下列範例會產生 C2511：  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```