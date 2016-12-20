---
title: "處理文件中的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WM_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令處理"
  - "命令處理, 文件中的命令"
  - "文件, 處理其中的訊息"
  - "文件, 訊息對應"
  - "訊息處理, WM_COMMAND 訊息"
  - "訊息對應, 在文件類別中"
  - "WM_COMMAND"
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理文件中的命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的文件類別可能也會處理功能表項目、工具列按鈕或快速鍵產生的某些命令。  根據預設，使用序列化， **CDocument** 處理儲存和儲存為檔案功能表上的命令。  會影響資料的其他命令會由文件的成員函式來管理。  例如，在 Scribble 程式，類別 `CScribDoc` 為編輯完整清單命令的處理常式，刪除在目前文件中的所有資料。  檔案可能有訊息對應，不過，不同於檢視，文件無法處理標準 Windows 訊息—  **WM\_COMMAND** 只訊息或「命令」。  
  
## 請參閱  
 [使用文件](../mfc/using-documents.md)