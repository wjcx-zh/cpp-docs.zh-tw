---
title: "NMAKE 警告 U4010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U4010"
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# NMAKE 警告 U4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'target' : 建置失敗；已指定 \/K，正在繼續...  
  
 給定目標之命令區塊中的命令傳回非零的結束代碼。  \/K 選項告訴 NMAKE 繼續處理建置中其他不相關的部分，並在 NMAKE 作業階段完成後發出結束代碼 1。  
  
 如果給定的目標本身是其他目標的相依，NMAKE 會在這個警告之後發出 [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) 警告。