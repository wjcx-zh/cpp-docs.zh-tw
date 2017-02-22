---
title: "NMAKE 的結束代碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "結束代碼"
  - "NMAKE 程式, 結束代碼"
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# NMAKE 的結束代碼
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 傳回下列結束代碼：  
  
|程式碼|意義|  
|---------|--------|  
|0|沒有錯誤 \(可能有警告\)|  
|1|組建不完整 \(只有在使用 \/K 時才會發出\)|  
|2|程式錯誤，可能是下列其中一個原因：|  
||-   在 Makefile 中有語法錯誤|  
||-   命令中的錯誤或結束代碼|  
||-   使用者的中斷|  
|4|系統錯誤 \- 記憶體不足|  
|255|目標不是最新的 \(只有在使用 \/Q 時才會發出\)|  
  
## 請參閱  
 [執行 NMAKE](../build/running-nmake.md)