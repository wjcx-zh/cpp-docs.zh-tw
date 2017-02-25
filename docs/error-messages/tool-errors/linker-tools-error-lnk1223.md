---
title: "連結器工具錯誤 LNK1223 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1223"
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK1223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案無效或損毀：檔案包含無效的 .pdata 比重  
  
 針對使用 pdata 的 RISC 平台，如果編譯器發出的 .pdata 區段具有未排序的項目，會發生這個錯誤。  
  
 若要修正這個問題，請在未啟用 [\/GL \(Whole Program Optimization\)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) 下嘗試編譯。  空白的函式主體也可能在某些情況下導致此錯誤。