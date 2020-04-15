---
title: 資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366995"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題介紹`AddNew``CRecordset``Edit`類`Delete`的和 的成員函數的工作原理。 涵蓋的主題包括：

- [新增記錄的工作原理](#_core_adding_a_record)

- [已新增記錄的可見性](#_core_visibility_of_added_records)

- [編輯記錄的工作原理](#_core_editing_an_existing_record)

- [移除記錄的工作原理](#_core_deleting_a_record)

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果使用批量行提取,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

作為補充,您可能想要閱讀[記錄欄位交換:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md),它描述了 RFX 在更新操作中的相應作用。

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>新增記錄

向記錄集添加新記錄包括調用記錄集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函數、設置新記錄欄位資料成員的值以及調用[Update](../../mfc/reference/crecordset-class.md#update)成員函數將記錄寫入資料來源。

作為調用`AddNew`的先決條件,記錄集不能作為唯讀打開。 `CanUpdate`和`CanAppend`成員函數允許您確定這些條件。

當您致電`AddNew`:

- 存儲編輯緩衝區中的記錄,因此,如果操作被取消,可以還原其內容。

- 欄位資料成員將被標記,以便以後可以檢測到其中的更改。 欄位資料成員也標記為乾淨(未更改),並設置為 Null。

呼叫`AddNew`後 呼叫 ,編輯緩衝區表示新的空記錄,準備用值填充。 為此,您可以通過分配給這些值來手動設置值。 可以調用`SetFieldNull`以指定值 Null,而不是為欄位指定實際資料值。

要提交變更,請致電`Update`。 當您呼叫`Update`新紀錄時:

- 如果您的 ODBC 驅動`::SQLSetPos`程式支援 ODBC API 函數,MFC 使用 該函數在資料源上添加記錄。 使用`::SQLSetPos`MFC 可以更高效地添加記錄,因為它不必構造和處理 SQL 語句。

- 如果`::SQLSetPos`無法使用,MFC 會執行以下操作:

   1. 如果未偵測到任何更改`Update`, 則不執行任何操作並返回 0。

   1. 如果存在變更,`Update`請建構 SQL **INSERT**語句。 由所有髒欄位數據成員表示的列列在**INSERT**語句中列出。 要強制包含欄,請呼叫[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成員函數:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`提交新記錄 - INSERT**語句執行**,記錄將提交到數據源(以及記錄集(如果不是快照)上的表,除非事務正在進行。

   1. 存儲的記錄將還原到編輯緩衝區。 無論 INSERT 語句`AddNew`是否成功 執行,調用之前當前的**INSERT**記錄都是再次 最新的。

   > [!TIP]
   > 為了完全控制新記錄,請採用以下方法:設置具有值的任何欄位的值,然後通過調用指向欄位和參數 TRUE(預設值)的指標顯式`SetFieldNull`設置將保持為空的任何欄位。 如果要確保欄位未寫入資料來源,請使用指向欄位和參數 FALSE`SetFieldDirty`的指標呼叫,並且不修改欄位的值。 要確定是否允許欄位為 Null,請呼`IsFieldNullable`叫 。

   > [!TIP]
   > 要檢測記錄組資料成員何時更改值,MFC 使用適合可存儲在記錄集中的每個數據類型的PSEUDO_NULL值。 如果必須顯式將欄位設置為PSEUDO_NULL值,並且該欄位碰巧已標記為 Null,則還必須呼`SetFieldNull`叫 ,傳遞第一個參數中的欄位位址,並在第二個參數中傳遞 FALSE。

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>已新增記錄的可見性

添加到的記錄何時對記錄集可見? 添加的記錄有時會顯示,有時不可見,具體取決於兩件事:

- 您的驅動程式能夠做什麼。

- 框架可以利用什麼。

如果您的 ODBC 驅動`::SQLSetPos`程式支援 ODBC API 功能,MFC 將使用該函數添加記錄。 使用`::SQLSetPos`時,添加的記錄對於任何可向上的 MFC 記錄集都可見。 如果沒有對函數的支援,添加的記錄不可見,您必須調用`Requery`以查看它們。 使用`::SQLSetPos`效率也更高。

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>編輯現有記錄

編輯記錄集中的現有記錄包括滾動到記錄、調用記錄集的[「編輯成員」](../../mfc/reference/crecordset-class.md#edit)函數、設定新記錄的欄位資料成員的值以及調用[Update](../../mfc/reference/crecordset-class.md#update)成員函數將更改的記錄寫入資料來源。

作為調用`Edit`的先決條件,記錄集必須是可備份的,並且是記錄在案的。 `CanUpdate`和`IsDeleted`成員函數允許您確定這些條件。 當前記錄也必須尚未刪除,並且記錄集中必須存在記錄(和`IsBOF``IsEOF`返回 0)。

呼叫`Edit`時 ,將儲存編輯緩衝區(目前記錄)中的記錄。 存儲的記錄的值稍後用於檢測是否有任何欄位已更改。

調用`Edit`後,編輯緩衝區仍表示當前記錄,但現在已準備好接受對欄位數據成員的更改。 要更改記錄,請手動設置要編輯的任何欄位數據成員的值。 可以調用`SetFieldNull`以指定值 Null,而不是為欄位指定實際資料值。 要提交變更,請致電`Update`。

> [!TIP]
> 要`AddNew`離開`Edit`或模式,請`Move`使用參數*AFX_MOVE_REFRESH*呼叫 。

作為調用`Update`的先決條件,記錄集不能為空,並且當前記錄不得被刪除。 `IsBOF`,`IsEOF``IsDeleted`並且 應全部返回 0。

當您呼叫`Update`編輯的紀錄時:

- 如果您的 ODBC 驅動`::SQLSetPos`程式支援 ODBC API 功能,MFC 將使用 該函數更新數據來源上的記錄。 使用`::SQLSetPos`,驅動程式會將編輯緩衝區與伺服器上的相應記錄進行比較,如果兩者不同,則更新伺服器上的記錄。 使用`::SQLSetPos`MFC 可以更高效地更新記錄,因為它不必構造和處理 SQL 語句。

   \- 或 -

- 如果`::SQLSetPos`無法使用,MFC 會執行以下操作:

   1. 如果沒有更改,`Update`則不執行任何操作並返回 0。

   1. 如果存在變更,`Update`請建構 SQL **UPDATE**語句。 **UPDATE**語句中列出的列基於已更改的欄位數據成員。

   1. `Update`提交更改 - 執行**UPDATE**語句 - 並在資料源上更改記錄,但在事務正在進行時不會提交(請參閱[事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md),瞭解有關事務如何影響更新的資訊。 ODBC 保留記錄的副本,該副本也會更改。

   1. 與的過程`AddNew`不同`Edit`, 進程不還原存儲的記錄。 編輯的記錄將保持當前記錄的位置。

   > [!CAUTION]
   > 當您準備通過調用`Update`更新記錄集時,請注意記錄集包含組成表主鍵的所有列(或表上任何唯一索引的所有列,或足夠列來唯一標識該行)。 在某些情況下,框架只能使用記錄集中選擇的列來標識要更新的表中的記錄。 如果沒有所有必要的列,則表中可能會更新多個記錄。 在這種情況下,框架在調用`Update`時會引發異常。

   > [!TIP]
   > 如果以前`AddNew`調用`Edit`或 調用任一函數,但在`Update`調用 之前調用 ,則編輯緩衝區將刷新存儲的記錄,替換正在進行的新記錄或已編輯的記錄。 此行為為您提供了一種中止`AddNew``Edit`或 開始新記錄的方法:如果您確定正在進行的記錄有故障,只需調`Edit``AddNew`用或 再次調用即可。

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>刪除記錄

從記錄集中刪除記錄涉及滾動到記錄並調用記錄集的[「刪除](../../mfc/reference/crecordset-class.md#delete)」成員函數。 與`AddNew``Edit``Delete`和 不同`Update`,不需要對的匹配調用。

作為調用`Delete`的先決條件,記錄集必須是可向上的,並且必須在記錄上。 `CanUpdate``IsBOF`、`IsEOF``IsDeleted`和成員函數允許您確定這些條件。

當您致電`Delete`:

- 如果您的 ODBC 驅動`::SQLSetPos`程式支援 ODBC API 函數,MFC 將使用 該函數刪除資料來源上的記錄。 使用`::SQLSetPos`通常比使用 SQL 更有效。

   \- 或 -

- 如果`::SQLSetPos`無法使用,MFC 會執行以下操作:

   1. 編輯緩衝區中的目前紀錄不備份為`AddNew``Edit`與 。

   1. `Delete`建構刪除記錄的 SQL **DELETE**語句。

      編輯緩衝區中的目前紀錄不儲存為與`AddNew``Edit`。

   1. `Delete`提交刪除 = 執行**DELETE**語句。 記錄在資料源上標記為已刪除,如果記錄是快照,則在 ODBC 中。

   1. 已刪除的記錄的值仍位於記錄集的欄位資料成員中,但欄位數據成員標記為 Null,並且記錄`IsDeleted`集的成員函數返回非零值。

   > [!NOTE]
   > 刪除記錄後,應滾動到另一條記錄以用新記錄的數據重新填充編輯緩衝區。 再次調用`Delete`或調`Edit`用 是錯誤的。

有關更新操作中使用的 SQL 語句的資訊,請參閱[SQL](../../data/odbc/sql.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：更多更新的詳細資訊 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
