---
title: 異動： 異動如何影響更新 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e540b68b820234ee6d30295b40c7e0f4cb7c806d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338586"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>異動：異動如何影響更新 (ODBC)
若要更新[資料來源](../../data/odbc/data-source-odbc.md)透過編輯緩衝區 （交易外使用的相同方法） 使用的交易期間所管理。 資料錄集的欄位資料成員以下合稱做為編輯緩衝區，其中包含目前的記錄，以將資料錄集備份期間暫時`AddNew`或`Edit`。 期間`Delete`作業，目前的記錄不會備份在交易內。 如需有關編輯緩衝區和更新的目前記錄的儲存方式的詳細資訊，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`AddNew`， `Edit`，或`Delete`。 您必須改為撰寫您自己的函式來執行資料來源的更新。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在交易期間`AddNew`， `Edit`，和`Delete`可以認可或回復作業。 效果`CommitTrans`和`Rollback`可能會導致不會還原為編輯緩衝區目前的記錄。 若要確定目前的記錄會正確還原，務必了解如何`CommitTrans`並`Rollback`成員函式`CDatabase`搭配使用的更新函式`CRecordset`。  
  
##  <a name="_core_how_committrans_affects_updates"></a> CommitTrans 如何影響更新  
 下表說明的效果`CommitTrans`的交易。  
  
### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影響更新  
  
|運算|資料來源的狀態|  
|---------------|---------------------------|  
|`AddNew` 和`Update`，然後 `CommitTrans`|新的記錄會加入至資料來源。|  
|`AddNew` (不含`Update`)，然後 `CommitTrans`|新的記錄將會遺失。 不會加入至資料來源的記錄。|  
|`Edit` 和`Update`，然後 `CommitTrans`|認可的資料來源的編輯。|  
|`Edit` (不含`Update`)，然後 `CommitTrans`|編輯記錄將會遺失。 記錄對資料來源會維持不變。|  
|`Delete` 然後 `CommitTrans`|從資料來源刪除的記錄。|  
  
##  <a name="_core_how_rollback_affects_updates"></a> 復原對交易的影響  
 下表說明的效果`Rollback`的交易。  
  
### <a name="how-rollback-affects-transactions"></a>復原對交易的影響  
  
|運算|目前記錄的狀態|您也必須|資料來源的狀態|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew` 和`Update`，然後 `Rollback`|目前的資料錄的內容是暫時儲存，以騰出空間給新的記錄。 編輯緩衝區輸入新的記錄。 之後`Update`呼叫時，目前資料錄會還原至編輯緩衝區。||資料來源所做的加法`Update`會反轉。|  
|`AddNew` (不含`Update`)，然後 `Rollback`|目前的資料錄的內容是暫時儲存，以騰出空間給新的記錄。 編輯緩衝區會包含新的記錄。|呼叫`AddNew`可還原編輯緩衝區到空的新的記錄。 或致電`Move`(0) 還原至編輯緩衝區的舊值。|因為`Update`不會呼叫，沒有任何對資料來源所做的變更。|  
|`Edit` 和`Update`，然後 `Rollback`|目前資料錄的未編輯的版本會暫時儲存。 編輯緩衝區的內容進行編輯。 之後`Update`呼叫時，未編輯的記錄版本仍會暫時儲存。|*動態集*： 捲動關閉目前的記錄，然後再回到編輯緩衝區來還原記錄的未編輯的版本。<br /><br /> *快照集*： 呼叫`Requery`重新整理資料來源的資料錄集。|資料來源所做的變更`Update`會反轉。|  
|`Edit` (不含`Update`)，然後 `Rollback`|目前資料錄的未編輯的版本會暫時儲存。 編輯緩衝區的內容進行編輯。|呼叫`Edit`可還原至編輯緩衝區的記錄的未編輯的版本。|因為`Update`不會呼叫，沒有任何對資料來源所做的變更。|  
|`Delete` 然後 `Rollback`|刪除目前資料錄的內容。|呼叫`Requery`從資料來源還原目前的資料錄的內容。|刪除資料來源的資料會反轉。|  
  
## <a name="see-also"></a>另請參閱  
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [異動： 執行交易集中的資料錄 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)