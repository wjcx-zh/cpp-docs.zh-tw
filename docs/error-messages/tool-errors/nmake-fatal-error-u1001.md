---
title: "NMAKE 嚴重錯誤 U1001 | Microsoft Docs"
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
  - "U1001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1001"
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 嚴重錯誤 U1001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 巨集中的字元 'character' 不合法  
  
 巨集中出現給定的字元，但不是字母、數字或底線。  
  
 錯誤的原因可能是在巨集展開中遺漏冒號：  
  
```  
syntax error : illegal character '=' in macro  
```