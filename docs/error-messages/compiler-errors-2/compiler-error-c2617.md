---
title: "編譯器錯誤 C2617 | Microsoft Docs"
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
  - "C2617"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2617"
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2617
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 傳回陳述式不一致  
  
 指定的函式並不具有宣告的傳回型別 \(Return Type\)，且之前的傳回陳述式 \(Statement\) 並未提供一個值。  
  
 下列範例會產生 C2617：  
  
```  
// C2617.cpp  
int i;  
func() {   // no return type prototype  
   if( i ) return;   // no return value  
   else return( 1 );   // C2617 detected on this line  
}  
```  
  
 可能的解決方案：  
  
```  
// C2617b.cpp  
// compile with: /c  
int i;  
int MyF() {  
   if (i)  
      return 0;  
   else   
      return (1);  
}  
```