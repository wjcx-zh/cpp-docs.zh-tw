---
title: "TN047：放寬資料庫異動需求 | Microsoft Docs"
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
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN047"
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN047：放寬資料庫異動需求
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個技術注意事項，說明 MFC ODBC 資料庫類別的交易要求，現在已經過時。  在 MFC 4.2 之前，資料庫類別要求游標在資料錄集儲存在 **CommitTrans** 和 **Rollback** 作業之後。  如果 ODBC 驅動程式和 DBMS 不支援這個層級游標保存，則資料庫類別未啟用交易。  
  
 從 MFC 4.2 開始，資料庫類別會擴展了要求游標保存的限制。  如果驅動程式支援它們，交易會啟用。  不過，您現在必須檢查 **CommitTrans** 和 **Rollback** 作業的效果加入至開啟的資料錄集。  如需成員函式 [CDatabase::GetCursorCommitBehavior](../Topic/CDatabase::GetCursorCommitBehavior.md) 和 [CDatabase::GetCursorRollbackBehavior](../Topic/CDatabase::GetCursorRollbackBehavior.md) 以取得詳細資訊。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)