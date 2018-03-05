---
title: "異動： 異動如何影響更新 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59eb8aecbf2dd2138c8a0469d71364b55fd82774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>異動：異動如何影響更新 (ODBC)
若要更新[資料來源](../../data/odbc/data-source-odbc.md)透過編輯緩衝區 （交易外使用的相同方法） 使用的交易期間所管理。 資料錄集的欄位資料成員共同做為編輯緩衝區，其中包含目前的記錄資料錄集備份期間暫時`AddNew`或**編輯**。 期間**刪除**作業，目前的記錄不會備份在交易內。 如需編輯緩衝區和更新將目前記錄的儲存方式的詳細資訊，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`AddNew`，**編輯**，或**刪除**。 相反地，您必須撰寫您自己的函式來執行資料來源的更新。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 在交易期間`AddNew`，**編輯**，和**刪除**作業可加以認可或回復。 效果**CommitTrans**和**復原**可能會導致目前的記錄不會還原為編輯緩衝區。 若要確定會正確還原目前的記錄，請務必了解如何**CommitTrans**和**復原**的成員函式`CDatabase`使用的更新函式`CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a>CommitTrans 如何影響更新  
 下表說明的效果**CommitTrans**在交易上。  
  
### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影響更新  
  
|運算|資料來源的狀態|  
|---------------|---------------------------|  
|`AddNew`和**更新**，然後**CommitTrans**|新的記錄會加入至資料來源。|  
|`AddNew`(不含**更新**)，然後**CommitTrans**|新的記錄將會遺失。 記錄不會加入至資料來源。|  
|**編輯**和**更新**，然後**CommitTrans**|認可至資料來源的編輯。|  
|**編輯**(不含**更新**)，然後**CommitTrans**|資料錄的編輯都會遺失。 記錄資料來源上維持不變的。|  
|**刪除**然後**CommitTrans**|刪除資料來源的記錄。|  
  
##  <a name="_core_how_rollback_affects_updates"></a>復原對交易的影響  
 下表說明的效果**復原**在交易上。  
  
### <a name="how-rollback-affects-transactions"></a>復原對交易的影響  
  
|運算|目前記錄的狀態|您也必須|資料來源的狀態|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew`和**更新**，然後**復原**|暫時儲存目前資料錄的內容以騰出空間給新的記錄。 編輯緩衝區輸入新的記錄。 之後**更新**呼叫時，目前資料錄會還原至編輯緩衝區。||資料來源所做的加法**更新**會反轉。|  
|`AddNew`(不含**更新**)，然後**復原**|暫時儲存目前資料錄的內容以騰出空間給新的記錄。 編輯緩衝區會包含新的記錄。|呼叫`AddNew`可編輯緩衝區還原至空的新的記錄。 或呼叫**移動**(0) 還原至編輯緩衝區的舊值。|因為**更新**不呼叫沒有任何資料來源所做的變更。|  
|**編輯**和**更新**，然後**復原**|暫時儲存目前記錄的未編輯的版本。 編輯對編輯緩衝區的內容。 之後**更新**呼叫時，未編輯的資料仍然會暫時儲存的記錄版本。|*動態集*： 捲動登出目前的記錄，然後再回到編輯緩衝區來還原記錄的未編輯的版本。<br /><br /> *快照集*： 呼叫**Requery**重新整理資料來源的資料錄集。|資料來源所做的變更**更新**會反轉。|  
|**編輯**(不含**更新**)，然後**復原**|暫時儲存目前記錄的未編輯的版本。 編輯對編輯緩衝區的內容。|呼叫**編輯**可編輯緩衝區來還原記錄的未編輯的版本。|因為**更新**不呼叫沒有任何資料來源所做的變更。|  
|**刪除**然後**復原**|目前的資料錄的內容會遭到刪除。|呼叫**Requery**從資料來源還原目前的資料錄的內容。|刪除資料來源的資料會反轉。|  
  
## <a name="see-also"></a>請參閱  
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [異動 (ODBC)](../../data/odbc/transaction-odbc.md)   
 [異動： 執行交易集中的資料錄 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)