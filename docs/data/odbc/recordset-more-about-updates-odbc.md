---
title: "資料錄集： 更多有關更新 (ODBC) |Microsoft 文件"
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
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ad9042c4001fc1a0e0c8c8d19e5ac53b6312875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-more-about-updates-odbc"></a>資料錄集：更多更新的詳細資訊 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明：  
  
-   [其他作業，例如交易，如何影響更新](#_core_how_transactions_affect_updates)。  
  
-   [您的更新和其他使用者的](#_core_your_updates_and_the_updates_of_other_users)。  
  
-   [深入了解的更新和刪除的成員函式](#_core_more_about_update_and_delete)。  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果您已實作大量資料列擷取，資訊的某些部分不適用。 例如，您不能呼叫`AddNew`，**編輯**，**刪除**，和**更新**成員函式; 不過，您可以在其中執行的交易。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_how_other_operations_affect_updates"></a>其他作業如何影響更新  
 您的更新會影響交易作用中時的更新，完成交易之前，關閉資料錄集，以及完成交易之前捲動。  
  
###  <a name="_core_how_transactions_affect_updates"></a>異動如何影響更新  
 超出了解如何`AddNew`，**編輯**，和**刪除**工作，務必了解如何**BeginTrans**， **CommitTrans**，和**復原**的成員函式[CDatabase](../../mfc/reference/cdatabase-class.md)工作與更新函式的[CRecordset](../../mfc/reference/crecordset-class.md)。  
  
 根據預設，呼叫`AddNew`和**編輯**影響的資料來源，當您呼叫立即**更新**。 **刪除**呼叫會立即生效。 但是，您可以在建立交易並執行這類呼叫的批次。 更新不是永久的直到您認可它們。 如果您改變心意，可以回復交易，不會認可它。  
  
 如需有關交易的詳細資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a>關閉資料錄集如何影響更新  
 如果您關閉資料錄集，或是其相關`CDatabase`物件，並將進行中交易 (尚未呼叫[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback))，則會復原交易自動 （除非您的資料庫後端是 Microsoft Jet 資料庫引擎） 備份。  
  
> [!CAUTION]
>  如果您使用 Microsoft Jet 資料庫引擎，關閉明確交易內的資料錄集不會導致釋放任何已修改的資料列或外顯交易認可或回復之前已放置的鎖定。 建議，您永遠都開啟和關閉資料錄集之內或之外 Jet 外顯交易。  
  
###  <a name="_core_how_scrolling_affects_updates"></a>捲動如何影響更新  
 當您[資料錄集： 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)資料錄集，在編輯緩衝區會填入新的目前資料錄 （上一筆記錄不會儲存第一次）。 您可以捲動會跳過先前刪除的記錄。 當您捲動之後`AddNew`或**編輯**呼叫，而不需呼叫**更新**， **CommitTrans**，或**復原**第一個，任何變更因為編輯緩衝區資料被引進新的記錄，則會遺失 （與您任何警告）。 編輯緩衝區填滿資料錄捲動至、 預存的記錄會釋出，而且不會變更資料來源。 這同時適用於`AddNew`和**編輯**。  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a>您的更新和其他使用者的更新  
 當您使用資料錄集更新資料時，您的更新會影響其他使用者。 同樣地，其他使用者資料錄集的存留期間的更新會影響您。  
  
 在多使用者環境中，其他使用者可以開啟包含您已選取資料錄集中的相同記錄部分的資料錄集。 在擷取前一筆記錄的變更會反映在資料錄集。 動態集擷取的記錄每次您捲動到它，因為動態集反映出變更每次您捲動至資料錄。 快照集擷取的記錄您捲動，所以只有在您捲動資料錄一開始之前發生的變更會反映快照集的第一次。  
  
 在開啟資料錄集之後，其他使用者所加入的記錄不會顯示資料錄集中除非您重新查詢。 動態資料錄集時，對其他使用者的現有記錄不要顯示在動態集時您捲動至受影響的資料錄。 如果您的資料錄集的快照集，直到您重新查詢快照集，不要顯示編輯。 如果您想要查看資料錄加入或刪除您的快照集或在動態集，其他使用者所加入的記錄中的其他使用者呼叫[CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery)重建資料錄集。 （請注意其他使用者刪除顯示在動態集）。您也可能會呼叫**Requery**查看記錄您將新增，但若要看到您的刪除動作。  
  
> [!TIP]
>  若要強制整個一次快照集的快取，請呼叫`MoveLast`立即開啟快照集之後。 然後呼叫**MoveFirst** ，開始使用記錄。 `MoveLast`相當於捲動透過所有記錄，不過它會擷取它們一次。 不過請注意，這會降低效能，而且可能不必要的部分驅動程式。  
  
 對其他使用者更新的影響很類似上您的影響。  
  
##  <a name="_core_more_about_update_and_delete"></a>更新與刪除的詳細資訊  
 本節提供其他資訊來協助您使用**更新**和**刪除**。  
  
### <a name="update-success-and-failure"></a>更新成功和失敗  
 如果**更新**成功，`AddNew`或**編輯**模式結束。 若要開始`AddNew`或**編輯**一次模式中，呼叫`AddNew`或**編輯**。  
  
 如果**更新**失敗 (傳回**FALSE**或擲回例外狀況)，您仍握有`AddNew`或**編輯**模式中，根據哪一個函式上一次呼叫。 接著，您可以執行下列其中一項：  
  
-   修改欄位資料成員並再試一次**更新**一次。  
  
-   呼叫`AddNew`重欄位資料成員設為 Null，將欄位資料成員的值設定，然後呼叫**更新**一次。  
  
-   呼叫**編輯**重新載入前的第一個呼叫資料錄集中的值`AddNew`或**編輯**、 設定欄位資料成員的值，然後呼叫**更新**一次。 之後成功**更新**呼叫 (除了之後`AddNew`呼叫)，欄位資料成員保留在新的值。  
  
-   呼叫**移動**(包括**移動**和參數**AFX_MOVE_REFRESH**，則為 0)，這會清除任何變更並結束任何`AddNew`或**編輯**作用中的模式。  
  
### <a name="update-and-delete"></a>Update 和 Delete  
 本節同時適用於**更新**和**刪除**。  
  
 在**更新**或**刪除**作業，應該更新只能有一個記錄。 該記錄是目前的記錄對應至資料錄集的欄位中的資料值。 如果沒有記錄受到影響或是多筆記錄會受到影響，由於某種原因，擲回例外狀況包含下列其中一種**RETCODE**值：  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**  
  
 擲回這些例外狀況時，您仍握有`AddNew`或**編輯**狀態時呼叫，您還在**更新**或**刪除**。 以下是最常見的案例中，您會看到這些例外狀況。 您應該會看到：  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**使用開放式的鎖定模式與另一位使用者已修改的記錄，以防止架構用來識別要更新或刪除的正確資料錄的方式。  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**當您要更新的資料表沒有主索引鍵或唯一索引，而且您沒有足夠的資料行中唯一識別資料表的資料列的資料錄集。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [例外狀況：資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)