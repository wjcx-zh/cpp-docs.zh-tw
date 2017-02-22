---
title: "運算錯誤 M6201 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6201"
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算錯誤 M6201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': \_DOMAIN 錯誤  
  
 給定函式的引數超出該函式的合法輸入值定義域。  
  
## 範例  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 這項錯誤會以函式名稱、函式的引數和錯誤類型來呼叫 `_matherr` 函式。  您可以重新撰寫 `_matherr` 函式來自訂某些執行階段浮點運算錯誤的處理。