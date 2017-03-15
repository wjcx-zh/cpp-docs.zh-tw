---
title: "連結器工具警告 LNK4102 | Microsoft Docs"
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
  - "LNK4102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4102"
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4102
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除解構函式 'name' 的匯出；映像可能無法正確執行  
  
 程式嘗試匯出一個刪除中的解構函式 \(Destructor\)。  最後刪除可能會跨 DLL 界限發生，使處理序釋放非自身所擁有的記憶體。  請確定您的 .def 檔並未列出指定符號，且該符號也不是連結器命令列中 **\/IMPORT** 或 **\/EXPORT** 選項所列出的引數。  
  
 如果您是要重建 C 執行階段程式庫，請忽略這個訊息。