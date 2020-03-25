---
title: 資料錄集：更多更新的詳細資訊 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: f11c723e4589cb28a3f38100050a69a78fc0809e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212845"
---
# <a name="recordset-more-about-updates-odbc"></a>資料錄集：更多更新的詳細資訊 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [其他作業（例如交易）如何影響更新](#_core_how_transactions_affect_updates)。

- [您的更新和其他使用者](#_core_your_updates_and_the_updates_of_other_users)。

- [Update 和 Delete 成員函式的詳細資訊](#_core_more_about_update_and_delete)。

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您已執行大量資料列提取，部分資訊將不適用。 例如，您無法呼叫 `AddNew`、`Edit`、`Delete`和 `Update` 成員函式;不過，您可以執行交易。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>其他作業如何影響更新

您的更新會受到更新時生效的交易影響，方法是在完成交易之前關閉記錄集，然後在完成交易之前進行滾動。

###  <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>交易如何影響更新

除了瞭解 `AddNew`、`Edit`和 `Delete` 如何運作，請務必瞭解[CDatabase](../../mfc/reference/cdatabase-class.md)的 `BeginTrans`、`CommitTrans`和 `Rollback` 的成員函式如何使用[CRecordset](../../mfc/reference/crecordset-class.md)的更新功能。

根據預設，呼叫 `Update`時，`AddNew` 和 `Edit` 的呼叫會立即影響資料來源。 `Delete` 呼叫會立即生效。 但是，您可以建立交易並執行此類呼叫的批次。 更新在您認可之前並不永久。 如果您改變主意，就可以復原交易，而不是認可它。

如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)。

###  <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>關閉記錄集如何影響更新

如果您關閉記錄集或其相關聯的 `CDatabase` 物件，且交易正在進行中（您未呼叫[CDatabase：： CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[Cdatabase：： Rollback](../../mfc/reference/cdatabase-class.md#rollback)），則會自動回復交易（除非您的資料庫後端是 Microsoft Jet 資料庫引擎）。

> [!CAUTION]
>  如果您使用 Microsoft Jet 資料庫引擎，在明確交易內關閉記錄集，並不會導致釋放已修改的任何資料列，或是在認可或回復明確交易之前所放置的鎖定。 建議您一律在明確的 Jet 交易內部或外部開啟和關閉記錄集。

###  <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>滾動對更新的影響

當您的[記錄集：在記錄集中滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)時，編輯緩衝區會填入每個新的目前記錄（先前的記錄不會先儲存）。 滾動會略過先前已刪除的記錄。 如果您在 `AddNew` 或 `Edit` 呼叫之後滾動，但未先呼叫 `Update`、`CommitTrans`或 `Rollback`，則會在新記錄進入編輯緩衝區時遺失任何變更（不會發出警告）。 編輯緩衝區會填入滾動到的記錄，儲存的記錄會釋出，而且資料來源上不會發生任何變更。 這同時適用于 `AddNew` 和 `Edit`。

##  <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>您的更新和其他使用者的更新

當您使用記錄集來更新資料時，您的更新會影響其他使用者。 同樣地，在記錄集的存留期間，其他使用者的更新也會影響您。

在多使用者環境中，其他使用者可以開啟包含您在記錄集中所選取之相同記錄的記錄集。 在您抓取記錄之前進行的變更會反映在您的記錄集內。 因為動態集會在您每次滾動到記錄時都抓取，所以當您每次滾動到記錄時，動態集就會反映出變更。 快照集會在您第一次滾動到記錄時抓取，因此快照集只會反映在您一開始滾動到記錄之前發生的變更。

除非您重新查詢，否則在開啟記錄集之後，其他使用者加入的記錄不會顯示在記錄集中。 如果您的記錄集是動態集，則當您流覽至受影響的記錄時，其他使用者的現有記錄編輯動作就會顯示在您的動態集中。 如果您的記錄集是快照，則在您重新查詢快照之前，不會顯示編輯。 如果您想要查看快照中的其他使用者加入或刪除的記錄，或是您的動態集內的其他使用者所加入的記錄，請呼叫[CRecordset：： Requery](../../mfc/reference/crecordset-class.md#requery)來重建記錄集。 （請注意，其他使用者的刪除會顯示在您的動態集內）。您也可以呼叫 `Requery` 來查看您新增的記錄，但不會看到您的刪除。

> [!TIP]
>  若要一次強制快取整個快照集，請在開啟快照集之後立即呼叫 `MoveLast`。 然後呼叫 `MoveFirst` 以開始使用記錄。 `MoveLast` 相當於在所有記錄上滾動，但它會一次抓取全部。 不過要注意的是，這可能會降低效能，而某些驅動程式可能不需要這麼做。

您的更新對其他使用者所造成的影響，與其對您的影響很相似。

##  <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>深入瞭解更新和刪除

本節提供可協助您使用 `Update` 和 `Delete`的其他資訊。

### <a name="update-success-and-failure"></a>更新成功和失敗

如果 `Update` 成功，`AddNew` 或 `Edit` 模式就會結束。 若要再次開始 `AddNew` 或 `Edit` 模式，請呼叫 `AddNew` 或 `Edit`。

如果 `Update` 失敗（傳回 FALSE 或擲回例外狀況），則您會維持 `AddNew` 或 `Edit` 模式，視您最後呼叫的函式而定。 接著，就可以執行下列其中一個動作：

- 請修改欄位資料成員，然後再次嘗試 `Update`。

- 呼叫 `AddNew` 將欄位資料成員重設為 Null、設定欄位資料成員的值，然後再次呼叫 `Update`。

- 呼叫 `Edit` 在第一次呼叫 `AddNew` 或 `Edit`之前重載記錄集內的值、設定欄位資料成員的值，然後再次呼叫 `Update`。 成功 `Update` 呼叫（在 `AddNew` 呼叫之後除外）之後，欄位資料成員會保留其新值。

- 呼叫 `Move` （包括參數為 AFX_MOVE_REFRESH 的 `Move` 或0），這會清除任何變更，並結束作用中的任何 `AddNew` 或 `Edit` 模式。

### <a name="update-and-delete"></a>Update 和 Delete

本節同時適用于 `Update` 和 `Delete`。

在 `Update` 或 `Delete` 作業上，應該只更新一筆記錄。 該記錄是目前的記錄，其對應至記錄集欄位中的資料值。 如果因為某些原因而沒有任何記錄受到影響，或有多筆記錄受到影響，則會擲回例外狀況，其中包含下列其中一個**RETCODE**值：

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

當擲回這些例外狀況時，您會保留在呼叫 `Update` 或 `Delete`時所處的 `AddNew` 或 `Edit` 狀態。 以下是您會看到這些例外狀況的最常見案例。 您很有可能會看到：

- 當您使用開放式鎖定模式，而另一位使用者已修改記錄以防止架構識別要更新或刪除的正確記錄時，AFX_SQL_ERROR_NO_ROWS_AFFECTED。

- 當您要更新的資料表沒有主鍵或唯一索引，而且記錄集內沒有足夠的資料行可唯一識別資料表資料列時，AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[例外狀況：資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)
