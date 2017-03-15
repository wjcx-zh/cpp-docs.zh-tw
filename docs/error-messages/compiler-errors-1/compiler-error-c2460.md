---
title: "編譯器錯誤 C2460 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2460"
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier1' : 使用已經定義的 'identifier2'  
  
 將類別或結構 \(`identifier2`\) 宣告成自身 \(`identifier1`\) 的成員。  不允許類別和結構的遞迴定義。  
  
 下列範例會產生 C2460：  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 在類別中改為使用指標參考。  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```