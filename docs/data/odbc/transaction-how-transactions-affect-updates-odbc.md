---
title: 異動：異動如何影響更新 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376427"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>異動：異動如何影響更新 (ODBC)

數據源[的更新在](../../data/odbc/data-source-odbc.md)事務期間使用編輯緩衝區(與事務之外使用的方法相同)進行管理。 記錄集的欄位資料成員集體用作包含當前記錄的編輯緩衝區,記錄集在`AddNew``Edit`或 期間暫時備份該記錄。 在`Delete`操作期間,當前記錄不會在事務中備份。 有關編輯緩衝區和更新如何存儲當前記錄的詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`AddNew`或`Edit` `Delete` 。 相反,您必須編寫自己的函數才能對數據源執行更新。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

在事務期間`AddNew`,`Edit`可以`Delete`提交 或回滾 和操作。 的效果`CommitTrans``Rollback`可能會導致當前記錄無法還原到編輯緩衝區。 為了確保正確還原當前記錄,請務必`CommitTrans`瞭解的`Rollback``CDatabase`和成員函數如何使用`CRecordset`的更新函數。

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>提交轉換如何影響更新

下表解釋了`CommitTrans`對事務的影響。

### <a name="how-committrans-affects-updates"></a>提交轉換如何影響更新

|作業|資料來源的狀態|
|---------------|---------------------------|
|`AddNew`和`Update`,然後`CommitTrans`|新記錄將添加到資料源中。|
|`AddNew`(沒有`Update`),然後`CommitTrans`|新記錄將丟失。 未添加到數據源的記錄。|
|`Edit`和`Update`,然後`CommitTrans`|提交到數據源的編輯。|
|`Edit`(沒有`Update`),然後`CommitTrans`|對記錄的編輯將丟失。 在數據源上記錄保持不變。|
|`Delete`然後`CommitTrans`|從資料源中刪除的記錄。|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>回滾如何影響事務

下表解釋了`Rollback`對事務的影響。

### <a name="how-rollback-affects-transactions"></a>回滾如何影響事務

|作業|目前紀錄的狀態|您必須|資料來源的狀態|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`和`Update`,然後`Rollback`|當前記錄的內容將暫時存儲,以便為新記錄騰出空間。 新記錄將輸入到編輯緩衝區中。 調用`Update`後,當前記錄將還原到編輯緩衝區。||對所`Update`做數據源的添加是反向的。|
|`AddNew`(沒有`Update`),然後`Rollback`|當前記錄的內容將暫時存儲,以便為新記錄騰出空間。 編輯緩衝區包含新記錄。|再次`AddNew`調用以將編輯緩衝區還原到空的新記錄。 或調用`Move`(0) 將舊值還原到編輯緩衝區。|因為`Update`未調用,因此對數據源沒有進行任何更改。|
|`Edit`和`Update`,然後`Rollback`|暫存儲存目前記錄的未經編輯的版本。 編輯對編輯緩衝區的內容進行編輯。 調用`Update`後,記錄的未編輯版本仍暫時存儲。|*動態集*:滾動當前記錄,然後返回以將未編輯的記錄版本還原到編輯緩衝區。<br /><br /> *快照*`Requery`: 呼叫從資料源刷新記錄集。|對數據源`Update`所做的更改將發生逆轉。|
|`Edit`(沒有`Update`),然後`Rollback`|暫存儲存目前記錄的未經編輯的版本。 編輯對編輯緩衝區的內容進行編輯。|再次`Edit`調用以將未編輯的記錄版本還原到編輯緩衝區。|因為`Update`未調用,因此對數據源沒有進行任何更改。|
|`Delete`然後`Rollback`|將刪除當前記錄的內容。|調用`Requery`從數據源還原當前記錄的內容。|從數據源中刪除數據將顛倒。|

## <a name="see-also"></a>另請參閱

[異動 (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[異動：在一個資料錄集內執行異動 (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
