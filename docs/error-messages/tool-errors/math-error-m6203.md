---
title: "運算錯誤 M6203 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6203"
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算錯誤 M6203
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': \_OVERFLOW 錯誤  
  
 給定函式的結果太大，無法表示。  
  
 這項錯誤會以函式名稱、函式的引數和錯誤類型來呼叫 `_matherr` 函式。  您可以重新撰寫 `_matherr` 函式來自訂某些執行階段浮點運算錯誤的處理。