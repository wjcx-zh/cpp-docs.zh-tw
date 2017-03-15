---
title: "資料錄集：加入大量資料錄 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "大量資料錄加入至資料錄集"
  - "ODBC 資料錄集, 加入資料錄"
  - "資料錄集, 加入資料錄"
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：加入大量資料錄 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 MFC [CRecordset](../../mfc/reference/crecordset-class.md) 類別有一個新的最佳化，可改善您加入大量新資料錄至資料表的效率。  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 **optimizeBulkAdd** 是 [CRecordset::Open](../Topic/CRecordset::Open.md) 成員函式的 **dwOptions** 參數新選項，可讓您在未呼叫 **Requery** 或 **Close** 的情況下便可加入多筆資料錄，因而提升效能。  只有在呼叫第一個 **Update** 之前是 Dirty 的那些欄位，會在接續的 `AddNew`\/**Update** 呼叫時標記成 Dirty。  
  
 若您正使用資料庫類別的 **::SQLSetPos** ODBC API 函式來加入、編輯和刪除資料錄，就不需要此最佳化。  
  
 如果已載入 ODBC 資料指標程式庫 \(Cursor Library\)，或是該 ODBC 驅動程式不支援經由 **::SQLSetPos** 來加入、編輯和刪除，這個最佳化應該會提升大量加入的效能。  若要開始這個最佳化，請將資料錄集的 **Open** 呼叫之 **dwOptions** 參數設定成下列：  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：加入、更新和刪除資料錄 \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [資料錄集：鎖定資料錄 \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)