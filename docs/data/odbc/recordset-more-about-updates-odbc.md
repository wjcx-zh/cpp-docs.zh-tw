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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368680"
---
# <a name="recordset-more-about-updates-odbc"></a>資料錄集：更多更新的詳細資訊 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題將說明：

- [其他操作(如事務)如何影響更新](#_core_how_transactions_affect_updates)。

- [您的更新和其他使用者的更新](#_core_your_updates_and_the_updates_of_other_users)。

- [有關更新和刪除成員函數](#_core_more_about_update_and_delete)的詳細資訊。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果已實現批量行提取,則某些資訊不適用。 例如,`AddNew`您不能呼叫`Edit``Delete``Update`、與成員函數;因此,不能呼叫、和但是,您可以執行事務。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>其他操作如何影響更新

更新受更新時生效的事務、在完成事務之前關閉記錄集以及完成事務之前滾動的影響。

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>交易如何影響更新

除了瞭解`AddNew`如何`Edit`、`Delete`和`BeginTrans`工作之外,瞭解[CDatabase](../../mfc/reference/cdatabase-class.md)和`Rollback`成員`CommitTrans`函數如何 使用[CRecordset](../../mfc/reference/crecordset-class.md)的更新函數也很重要。

預設情況下,呼叫`AddNew`與`Edit`影響資料來源時,您呼叫`Update`。 `Delete`呼叫立即生效。 但是,您可以建立事務並執行一批此類調用。 在提交更新之前,更新不是永久性的。 如果您改變主意,您可以回滾事務,而不是提交它。

有關交易記錄的詳細資訊,請參閱事務[(ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>關閉記錄集如何影響更新

如果關閉記錄集或其關聯`CDatabase`物件,事務正在進行中(您尚未調用[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)或[CDatabase::回滾](../../mfc/reference/cdatabase-class.md#rollback)),則事務將自動回滾(除非您的資料庫後端是 Microsoft Jet 資料庫引擎)。

> [!CAUTION]
> 如果使用 Microsoft Jet 資料庫引擎,則關閉顯式事務中的記錄集不會導致釋放在提交或回滾顯式事務之前已修改的任何行或已放置的鎖。 建議您始終在顯式 Jet 事務內外打開和關閉記錄集。

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>捲動如何影響更新

當您[記錄集:在記錄集中滾動 (ODBC) 時](../../data/odbc/recordset-scrolling-odbc.md),編輯緩衝區將填充每個新的當前記錄(不會首先存儲以前的記錄)。 捲動跳過以前刪除的記錄。 `AddNew`如果在`Edit`未調用 或調`Update`用後`CommitTrans`滾動`Rollback`而不調用 ,或第一次,則當新記錄被引入編輯緩衝區時,任何更改都將丟失(無需警告)。 編輯緩衝區將填充滾動到的記錄,釋放存儲的記錄,並且數據源上不會發生任何更改。 這同時適用於`AddNew`與`Edit`。

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>您的更新和其他使用者的更新

當您使用記錄集更新數據時,更新會影響其他使用者。 同樣,在記錄集的生存期內其他使用者的更新也會影響您。

在多使用者環境中,其他使用者可以打開包含您在記錄集中選擇的某些相同記錄集的記錄集。 檢索記錄之前對記錄的更改將反映在記錄集中。 由於每次滾動到記錄時,動態集都會檢索記錄,因此每次滾動到記錄時,動態集都會反映更改。 快照在首次滾動到記錄時檢索記錄,因此快照僅反映最初滾動到記錄之前發生的更改。

除非重新查詢,否則其他使用者在打開記錄集後添加的記錄不會顯示在記錄集中。 如果記錄集是動態集,則當您滾動到受影響的記錄時,其他使用者對現有記錄進行編輯確實會顯示在動態集中。 如果記錄集是快照,則在重新查詢快照之前不會顯示編輯。 如果要查看快照中的其他使用者添加或刪除的記錄,或者動態集中的其他使用者添加的記錄,請調用[CRecordset::重新查詢](../../mfc/reference/crecordset-class.md#requery)以重建記錄集。 (請注意,其他使用者的刪除將顯示在您的動態集中。您也可以打電話`Requery`查看您添加的記錄,但不能查看您的刪除內容。

> [!TIP]
> 要強制一次緩存整個快照,請立即在打開`MoveLast`快照后調用。 然後調用`MoveFirst`開始處理記錄。 `MoveLast`等效於滾動所有記錄,但它一次檢索所有記錄。 但是請注意,這可能會降低性能,並且某些驅動程式可能不需要這樣做。

更新對其他用戶的影響類似於它們對您的影響。

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>有關更新與移除的詳細資訊

本節提供其他資訊,以説明您使用`Update``Delete`和 。

### <a name="update-success-and-failure"></a>更新成功與失敗

如果`Update`成功,或`AddNew``Edit`模式將結束。 要重新開始`AddNew``Edit`或模式`AddNew`,`Edit`請呼叫或 。

如果`Update`失敗(返回 FALSE 或引發異常),則保持`AddNew`或`Edit`模式,具體取決於您上次調用的函數。 接著，就可以執行下列其中一個動作：

- 修改欄位數據成員,然後`Update`重試。

- 呼叫`AddNew`將欄位資料成員重置為 Null,設定欄位資料成員的值,然後再次`Update`呼叫 。

- 呼叫`Edit`以重新載入記錄集中的值,然後再調`AddNew`用`Edit`或 ,設置欄位資料成員的值,然後再次`Update`調用。 成功`Update`呼叫後`AddNew`(呼叫後除外),欄位數據成員將保留其新值。

- 呼叫`Move`(`Move`包括 參數為 AFX_MOVE_REFRESH 或 0),該呼叫刷新`AddNew`任何`Edit`更改並結束任何有效的或模式。

### <a name="update-and-delete"></a>更新與移除

本節適用於`Update`和`Delete`。

在`Update`或`Delete`操作上,應更新一條記錄和一條記錄。 該記錄是當前記錄,對應於記錄集欄位中的數據值。 如果由於某種原因沒有記錄受到影響或多個記錄受到影響,則引發包含以下**RETCODE**值之一的異常:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

當引發這些異常時,您將`AddNew`處於調用`Edit``Update``Delete`或 時處於或 狀態。 下面是最常見的方案,在這些方案中您將看到這些異常。 您最有可能看到:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED當您使用樂觀鎖定模式,而另一個使用者已修改記錄的方式,阻止框架識別要更新或刪除的正確記錄。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED,當您正在更新的表沒有主鍵或唯一索引時,並且記錄集中沒有足夠的列來唯一標識表行。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[例外狀況：資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)
