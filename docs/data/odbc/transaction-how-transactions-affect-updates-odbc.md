---
title: 異動：交易影響更新的方式（ODBC）
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: d03ec3f71c38f7790d66fbf6f800b7647e080147
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311924"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>異動：交易影響更新的方式（ODBC）

[資料來源](../../data/odbc/data-source-odbc.md)的更新會在交易期間透過使用編輯緩衝區（這是在交易外使用的相同方法）進行管理。 記錄集的欄位資料成員會共同做為編輯緩衝區，其中包含目前的記錄，而記錄集會在`AddNew`或`Edit`期間暫時備份。 `Delete`在作業期間，不會在交易內備份目前的記錄。 如需編輯緩衝區以及更新如何儲存目前記錄的詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)ODBC）。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法`AddNew`呼叫`Edit`、或`Delete`。 您必須改為撰寫自己的函式，以對資料來源執行更新。 如需大量資料列擷取的詳細資訊，請參閱[資料錄集：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

在交易期間`AddNew`， `Edit`可以認可`Delete`或回復、和作業。 `CommitTrans` 和`Rollback`的效果可能會導致目前的記錄不會還原至編輯緩衝區。 若要確定目前的記錄已正確還原，請務必瞭解`CommitTrans`的和`Rollback`成員`CDatabase`函式如何與的更新功能`CRecordset`搭配運作。

##  <a name="_core_how_committrans_affects_updates"></a>CommitTrans 如何影響更新

下表說明交易上的`CommitTrans`效果。

### <a name="how-committrans-affects-updates"></a>CommitTrans 如何影響更新

|運算|資料來源的狀態|
|---------------|---------------------------|
|`AddNew`和`Update`，然後`CommitTrans`|新記錄會新增至資料來源。|
|`AddNew`（不`Update`含），然後`CommitTrans`|新記錄已遺失。 記錄未新增至資料來源。|
|`Edit`和`Update`，然後`CommitTrans`|已認可資料來源的編輯。|
|`Edit`（不`Update`含），然後`CommitTrans`|記錄的編輯會遺失。 資料來源上的記錄保持不變。|
|`Delete`請`CommitTrans`|已從資料來源刪除記錄。|

##  <a name="_core_how_rollback_affects_updates"></a>復原如何影響交易

下表說明交易上的`Rollback`效果。

### <a name="how-rollback-affects-transactions"></a>復原如何影響交易

|運算|目前記錄的狀態|您也必須|資料來源的狀態|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`然後`Update`，`Rollback`|目前記錄的內容會暫時儲存，以騰出空間給新的記錄。 已在編輯緩衝區中輸入新記錄。 呼叫`Update`之後，目前的記錄會還原至編輯緩衝區。||除了所建立的`Update`資料來源之外，也會反轉。|
|`AddNew`（不`Update`含），然後`Rollback`|目前記錄的內容會暫時儲存，以騰出空間給新的記錄。 編輯緩衝區包含新記錄。|再次`AddNew`呼叫，將編輯緩衝區還原為空白的新記錄。 或呼叫`Move`（0），將舊值還原至編輯緩衝區。|因為`Update`不會呼叫，所以不會對資料來源進行任何變更。|
|`Edit`然後`Update`，`Rollback`|目前記錄的未編輯版本會暫時儲存。 編輯緩衝區的內容會進行編輯。 呼叫`Update`之後，仍會暫時儲存未編輯的記錄版本。|*動態集*：將目前的記錄回復，然後返回以將未編輯的記錄版本還原至編輯緩衝區。<br /><br /> *快照*集：呼叫`Requery`以重新整理資料來源中的記錄集。|對所做的`Update`資料來源所做的變更會反轉。|
|`Edit`（不`Update`含），然後`Rollback`|目前記錄的未編輯版本會暫時儲存。 編輯緩衝區的內容會進行編輯。|再次`Edit`呼叫，將未編輯的記錄版本還原至編輯緩衝區。|因為`Update`不會呼叫，所以不會對資料來源進行任何變更。|
|`Delete`請`Rollback`|刪除目前記錄的內容。|呼叫`Requery` ，以從資料來源還原目前記錄的內容。|從資料來源中刪除資料是相反的。|

## <a name="see-also"></a>另請參閱

[異動 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
