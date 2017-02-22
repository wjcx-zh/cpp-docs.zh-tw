---
title: "編譯器錯誤 C2021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2021"
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必須是指數值，而非 'character'  
  
 某浮點常數指數所用的字元不是有效數字。  請確定使用範圍中的指數。  
  
## 範例  
 下列範例會產生 C2021：  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## 範例  
 可能的解決方案：  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```