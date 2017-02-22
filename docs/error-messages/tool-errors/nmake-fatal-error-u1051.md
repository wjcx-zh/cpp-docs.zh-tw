---
title: "NMAKE 嚴重錯誤 U1051 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1051"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1051"
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 嚴重錯誤 U1051
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

記憶體不足  
  
 由於 Makefile 太大或太複雜，導致 NMAKE 記憶體不足，包含虛擬記憶體在內。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  釋放磁碟的部分空間。  
  
2.  增加 Windows NT 分頁檔或 Windows 交換檔 \(Swap File\) 的大小。  
  
3.  如果只使用部分的 Makefile，可以將 Makefile 切割為多個檔案，或使用 **\!IF** 前置處理器指示詞來限制 NMAKE 必須處理的數量。  **\!IF** 指示詞包含 **\!IF**、`!IFDEF`、**\!IFNDEF**、**\!ELSE IF**、**\!ELSE** `IFDEF` 及 **\!ELSE** `IFNDEF`。