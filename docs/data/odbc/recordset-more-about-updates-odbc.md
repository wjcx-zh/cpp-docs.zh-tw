---
title: "資料錄集：更多更新的詳細資訊 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多使用者環境, 資料錄集的更新"
  - "ODBC 資料錄集, 更新"
  - "資料錄, 更新"
  - "資料錄集, 更新"
  - "捲動, 資料錄集的更新"
  - "異動, 更新資料錄集"
  - "更新資料錄集"
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 資料錄集：更多更新的詳細資訊 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明：  
  
-   [其他作業 \(例如交易\) 如何影響更新](#_core_how_transactions_affect_updates)  
  
-   [您的更新和其他使用者的更新](#_core_your_updates_and_the_updates_of_other_users)  
  
-   [更多的 Update 和 Delete 成員函式的詳細資訊](#_core_more_about_update_and_delete)  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  若您已經實作大量資料列擷取，某些資訊便不適用。  例如，您不能呼叫 `AddNew`、**Edit**、**Delete** 和 **Update** 成員函式；然而，您可執行交易。  如需大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_how_other_operations_affect_updates"></a> 其他作業如何影響更新  
 您的更新會受到更新時仍具效用的交易、完成交易前的資料錄集關閉和捲動等因素影響。  
  
###  <a name="_core_how_transactions_affect_updates"></a> 交易如何影響更新  
 除了了解 `AddNew`、**Edit** 和 **Delete** 如何運作以外，了解 [CDatabase](../../mfc/reference/cdatabase-class.md) 的 **BeginTrans**、**CommitTrans** 和 **Rollback** 成員函式如何和 [CRecordset](../../mfc/reference/crecordset-class.md) 的更新函式搭配使用，也是很重要的。  
  
 預設情況下，先前呼叫的 `AddNew` 和 **Edit** 會在您呼叫 **Update** 後立即影響資料來源。  **Delete** 呼叫會立即影響。  但您可建立一筆交易並執行一組這類的呼叫。  這種更新在您認可之前是暫時的。  若您改變心意，可以還原此交易而不認可它。  
  
 如需交易的詳細資訊，請參閱[異動 \(ODBC\)](../../data/odbc/transaction-odbc.md)。  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> 關閉資料錄如何影響更新  
 若在交易處理中 \(尚未呼叫 [CDatabase::CommitTrans](../Topic/CDatabase::CommitTrans.md) 或 [CDatabase::Rollback](../Topic/CDatabase::Rollback.md)\) 關閉資料錄集或相關的 `CDatabase` 物件，該交易便會自動還原 \(除非您的資料庫後端是 Microsoft Jet 資料庫引擎\)。  
  
> [!CAUTION]
>  若您正使用 Microsoft Jet 資料庫引擎，關閉明確交易內的資料錄集並不會導致釋放所有已修改的資料列，或導致釋放在認可或還原明確交易之前所鎖定的資料列。  建議您總是在明確 Jet 交易的內外都開啟和關閉資料錄集。  
  
###  <a name="_core_how_scrolling_affects_updates"></a> 捲動如何影響更新  
 當您在資料錄集中[資料錄集：捲動 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md) 時，編輯緩衝區會填入每個新的目前資料錄 \(先前的資料錄並未先預存\)。  捲動會跳過先前刪除的資料錄。  若您在 `AddNew` 或 **Edit** 呼叫後捲動，而沒有先呼叫 **Update**、**CommitTrans** 或 **Rollback**，所有的變動會遺失 \(這點將不會有警告\)，因為一筆新資料錄會被帶進編輯緩衝區中。  編輯緩衝區會填入捲動到的資料錄，預存的資料錄已釋放，而資料來源上不會發生任何的變動。  這點亦適用於 `AddNew` 和 **Edit**。  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> 您的更新和其他使用者的更新  
 當您使用資料錄集來更新資料，您的更新將會影響其他使用者。  相同地，其他使用者在您的資料錄集存留期 \(Lifetime\) 內所做的更新會影響您。  
  
 在一個多使用者的環境中，其他使用者所開啟的資料錄集可包含某些您已在您的資料錄集中選取的資料錄。  變更資料錄在擷取前會反映在您的資料錄集。  因為動態集會在每次您捲動至資料錄時加以擷取，因此動態集會在每次捲動至一筆資料錄時反映出變更。  快照集會在您第一次捲動至一筆資料錄時擷取它，因此快照集只會在您最初捲動至資料錄前反映這些變動。  
  
 在開啟資料錄集後，其他使用者所加入的資料錄不會顯示在您的資料錄集中，除非您重新查詢。  若您的資料錄集是一個動態集，其他使用者對現存資料錄所做的編輯動作會在您捲動至受影響的資料錄時，顯示在您的動態集中。  若您的資料錄集是一個快照集，編輯將不會顯示，除非您重新查詢快照集。  如果想在您的快照集中查閱其他使用者加入或刪除的資料錄，或在動態集中查閱其他使用者加入的資料錄，可呼叫 [CRecordset::Requery](../Topic/CRecordset::Requery.md) 來重建資料錄集 \(請注意，其他使用者所做的刪除動作會顯示在您的動態集中\)。也可呼叫 **Requery** 來查閱您加入的資料錄，但是無法看到刪除動作。  
  
> [!TIP]
>  若要強制一次快取整個快照集，請在您開啟快照集後立即呼叫 `MoveLast`。  然後呼叫 **MoveFirst** 以開始使用資料錄。  `MoveLast` 相當於捲動所有資料錄，但是會一次擷取全部。  請注意，這個動作會減慢效能，且某些驅動程式可能不需要。  
  
 您的更新對其他使用者所造成的影響類似於他們對您所造成的影響。  
  
##  <a name="_core_more_about_update_and_delete"></a> 更多 Update 和 Delete 的詳細資訊  
 本章節內容提供幫您使用 **Update** 和 **Delete** 的附加資訊。  
  
### 更新成功和失敗  
 若 **Update** 成功，則 `AddNew` 或 **Edit** 模式就會終止。  若要在次開始一個 `AddNew` 或 **Edit** 模式，就要呼叫 `AddNew` 或 **Edit**。  
  
 若 **Update** 失敗 \(傳回 **FALSE** 或擲回一個例外狀況\)，根據您最後呼叫的函式，您還會在 `AddNew` 或 **Edit** 模式。  然後，您可選擇下列其中一種方式執行：  
  
-   修改欄位資料成員並再次嘗試 **Update**。  
  
-   呼叫 `AddNew` 將欄位資料成員重設為 Null，設定欄位資料成員的值，然後再次呼叫 **Update**。  
  
-   呼叫 **Edit** 以重新載入那些在呼叫 `AddNew` 或 **Edit** 之前就存在資料錄集中的值，設定欄位資料成員的值，然後再次呼叫 **Update**。  在 **Update** 呼叫成功後 \(除了在呼叫 `AddNew` 後\)，欄位資料成員會保留它們的新值。  
  
-   呼叫 **Move** \(包括 **Move** 與 **AFX\_MOVE\_REFRESH** 參數，或 0\)，這會清除所有的變動並終止任何實施中的 `AddNew` 或 **Edit** 模式。  
  
### Update 和 Delete  
 本章節內容同時適用於 **Update** 和 **Delete**。  
  
 在一個 **Update** 或 **Delete** 作業上，只有一個資料錄應該更新。  那個資料錄就是目前的資料錄，它與資料錄集欄位內的資料值一致。  若基於某種理由，沒有任何的資料錄受到影響，或超過一個以上的資料錄受到影響，則會擲回包含下列其中一種 **RETCODE** 值的例外狀況：  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED**  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED**  
  
 當擲回這些例外狀況時，您仍在呼叫 **Update** 或 **Delete** 時的 `AddNew` 或 **Edit** 狀態。  這裡是您會看到這些例外狀況的最常見案例。  您應該會看到：  
  
-   **AFX\_SQL\_ERROR\_NO\_ROWS\_AFFECTED** 當您正使用開放式鎖定模式，且其他使用者已用某種方法來修改資料錄，此方法會防止架構識別正確的資料錄以進行更新或刪除。  
  
-   **AFX\_SQL\_ERROR\_MULTIPLE\_ROWS\_AFFECTED** 當您所更新的資料表沒有主索引鍵或唯一索引鍵，且在資料錄集中沒有足夠的資料行可識別唯一的資料表資料列。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：資料錄集選取資料錄的方式 \(ODBC\)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [例外狀況：資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)