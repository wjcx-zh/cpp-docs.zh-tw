---
title: "編譯器錯誤 C2194 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2194"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2194"
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2194
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 是文字區段  
  
 `data_seg` Pragma 使用了已用於 `code_seg` 的區段名稱。  
  
 下列範例會產生 C2194：  
  
```  
// C2194.cpp  
// compile with: /c  
#pragma code_seg("MYCODE")  
#pragma data_seg("MYCODE")   // C2194  
#pragma data_seg("MYCODE2")   // OK  
```