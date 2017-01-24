---
title: "編譯器警告 (層級 1) C4612 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4612"
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Include 檔檔名錯誤  
  
 當檔案名稱不正確或遺漏時，**\#pragma include\_alias** 會發生這個錯誤。  
  
 **\#pragma include\_alias** 陳述式的引數可以使用引號格式 \(**"檔案名稱****"**\) 或角括弧格式 \(**\<**檔案名稱**\>**\)，但兩端都必須使用相同的格式。  
  
## 範例  
  
```  
// C4612.cpp // compile with: /W1 /LD #pragma include_alias("StandardIO", <stdio.h>) // C4612  
```