---
title: "連結器工具錯誤 LNK1158 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1158"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1158"
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK1158
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法執行 'filename'  
  
 [LINK](../../build/reference/linker-command-line-syntax.md) 呼叫的指定可執行檔不是位在包含 LINK 的目錄，也不在 PATH 環境變數所指定的目錄中。  
  
 例如，如果您嘗試在 32 位元電腦作業系統的 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 連結器選項使用 PGOPTIMIZE 參數，就會出現這種錯誤。