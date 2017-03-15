---
title: "異動：異動如何影響更新 (ODBC) | Microsoft Docs"
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
  - "CommitTrans 方法"
  - "ODBC 資料錄集, 異動"
  - "Rollback 方法, ODBC 異動"
  - "異動, 復原"
  - "異動, 更新資料錄集"
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 異動：異動如何影響更新 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[資料來源](../../data/odbc/data-source-odbc.md)的更新是透過使用編輯緩衝區 \(和交易外使用的方法相同\) 在交易中管理的。  全體的資料錄集欄位資料成員 \(Field Data Member\) 是做為包含目前資料錄的一個編輯緩衝區，在此資料錄集於 `AddNew` 或 **Edit** 期間將暫時地備份。  在 **Delete** 作業時，不會將目前的資料錄在交易內備份。  如需編輯緩衝區和更新如何儲存目前資料錄的詳細資訊，請參閱[資料錄集：資料錄集如何更新資料錄 \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，就無法呼叫 `AddNew`、**Edit** 或 **Delete**。  否則，您必須撰寫自己的函式以執行資料來源的更新。  如需關於大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在交易期間，可以認可或復原 `AddNew`、**Edit** 和 **Delete** 作業。  **CommitTrans** 和 **Rollback** 的效果可能造成目前的資料錄無法還原成編輯緩衝區。  必須了解 `CDatabase` 的 **CommitTrans** 和 **Rollback** 成員函式是如何使用 `CRecordset` 的更新函式，才能夠確保可以正確還原目前的資料錄。  
  
##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans 如何影響更新  
 下表說明 **CommitTrans** 對交易的影響：  
  
### CommitTrans 如何影響更新  
  
|作業|資料來源的狀態|  
|--------|-------------|  
|`AddNew` 和 **Update** 以及 **CommitTrans**|將新資料錄加入至資料來源。|  
|`AddNew` \(沒有 **Update**\) 以及 **CommitTrans**|遺失新資料錄。  未將資料錄加入到資料來源內。|  
|**Edit** 和 **Update** 以及 **CommitTrans**|編輯認可的資料來源。|  
|**Edit** \(沒有 **Update**\) 以及 **CommitTrans**|資料錄的編輯已遺失。  資料來源上的資料錄保持不變。|  
|**Delete** 然後 **CommitTrans**|從資料來源中刪除資料錄。|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Rollback 如何影響交易  
 下表說明 **Rollback** 對交易的影響：  
  
### Rollback 如何影響交易  
  
|作業|目前資料錄的狀態|您也必須|資料來源的狀態|  
|--------|--------------|----------|-------------|  
|`AddNew` 和 **Update**，然後 **Rollback**|暫時將目前資料錄的內容儲存，騰出空間給新的資料錄。  新資料錄進入編輯緩衝區內。  呼叫 **Update** 後，目前的資料錄會還原至編輯緩衝區。||逆轉 **Update** 對資料來源所做的新增。|  
|`AddNew` \(沒有 **Update**\)，然後 **Rollback**。|暫時將目前資料錄的內容儲存，騰出空間給新的資料錄。  編輯緩衝區包含新的資料錄。|再次呼叫 `AddNew`，將編輯緩衝區還原為空的新資料錄。  或呼叫 **Move** \(0\) 將舊的值還原至編輯緩衝區中。|沒有呼叫 **Update**，所以資料來源不會有任何變動。|  
|**Edit** 和 **Update**，然後 **Rollback**。|會暫時儲存一個未編輯過的目前資料錄版本。  對編輯緩衝區的內容做編輯。  呼叫 **Update** 後，仍暫時儲存未編輯過的資料錄版本。|動態集 \(Dynaset\)：捲回目前的資料錄以返回，然後將未編輯的資料錄版本還原至編輯緩衝區。<br /><br /> 快照集 \(Snapshot\)：呼叫 **Requery**，重新整理資料來源的資料錄集。|逆轉 **Update** 對資料來源所進行的變更。|  
|**Edit** \(沒有 **Update**\)，然後 **Rollback**。|會暫時儲存一個未編輯過的目前資料錄版本。  對編輯緩衝區的內容做編輯。|再次呼叫 **Edit**，將未編輯的資料錄版本還原為編輯緩衝區。|沒有呼叫 **Update**，所以資料來源不會有任何變動。|  
|**Delete** 然後 **Rollback**。|刪除目前資料錄的內容。|呼叫 **Requery**，從資料來源還原目前資料錄的內容。|逆轉對資料來源的資料所做的刪除。|  
  
## 請參閱  
 [異動 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [異動 \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [異動：在一個資料錄集內執行異動 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)