---
title: "連結器工具警告 LNK4022 | Microsoft Docs"
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
  - "LNK4022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4022"
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到與符號 'symbol' 完全相符的項目  
  
 LINK 或 LIB 找到多個相符於指定的未裝飾符號項目，而且無法解決模稜兩可 \(Ambiguity\) 的情況。  未產生輸出檔 \(.exe、.dll、exp 或.lib\)。  這個警告之後會出現每一個重複符號的警告 [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)，最後會出現嚴重錯誤 [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。  
  
 若要避免產生這個警告，請以裝飾形式指定符號。  在目的檔上執行 [DUMPBIN](../../build/reference/dumpbin-options.md) 可以看見裝飾的名稱。