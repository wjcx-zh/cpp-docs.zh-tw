---
title: "編譯器錯誤 C2563 | Microsoft Docs"
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
  - "C2563"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2563"
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2563
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在型式參數清單中不相符  
  
 函式 \(或函式指標\) 的型式參數清單與另一個函式 \(或成員函式的指標\) 的型式參數清單不相符。  因此，無法進行函式或指標的指派。  
  
 下列範例會產生 C2563：  
  
```  
// C2563.cpp  
void func( int );  
void func( int, int );  
int main() {  
   void *fp();  
   fp = func;   // C2563  
}  
```