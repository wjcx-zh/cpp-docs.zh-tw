---
title: "連結器工具警告 LNK4204 | Microsoft Docs"
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
  - "LNK4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4204"
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4204
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'filename' 遺漏參考模組的偵錯資訊；當做沒有偵錯資訊，連結物件  
  
 .pdb 檔簽章 \(Signature\) 錯誤。  連結器會繼續不使用偵錯資訊來連結目的檔。  您必須用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 選項重新編譯目的檔。  
  
 如果程式庫中的某些物件參考到已不存在的檔案，就可能發生 LNK4204。  例如，這可能發生在重建方案時，某物件檔案已被刪除，但因為編譯錯誤而未重建。  在此情況下，利用 **\/Z7** 或 **\/Fd** 編譯，以更新物件，每個程式庫指向單一檔案 \(不是預設的 .pdb 檔案名稱\)。如需詳細資訊，請參閱[\/Fd \(程式資料庫檔名\)](../../build/reference/fd-program-database-file-name.md)。確保 .pdb 每一次在原始檔控制系統中更新時，都是以程式庫儲存。