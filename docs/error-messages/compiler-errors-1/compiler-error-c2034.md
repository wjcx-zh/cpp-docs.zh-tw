---
title: "編譯器錯誤 C2034 | Microsoft Docs"
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
  - "C2034"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2034"
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2034
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 位元成員的位元欄位型別太小  
  
 位元欄位宣告中的位元數目超過基底型別 \(Base Type\) 的大小。  
  
 下列範例會產生 C2034：  
  
```  
// C2034.cpp  
struct A {  
   char test : 9;   // C2034, char has 8 bits  
};  
```  
  
 可能的解決方案：  
  
```  
// C2034b.cpp  
// compile with: /c  
struct A {  
   char test : 8;  
};  
```