---
title: "NMAKE 嚴重錯誤 U1100 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1100"
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 嚴重錯誤 U1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

巨集 'macroname' 不合法 \(在批次規則 'rule' 內容中\)  
  
 當批次模式規則的命令區塊直接或間接參考不是 $\< 的特殊檔案巨集時，NMAKE 就會產生此錯誤。  
  
 $\< 是批次模式規則中唯一允許的巨集。