---
title: 資料錄欄位交換：RFX 的運作方式
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367165"
---
# <a name="record-field-exchange-how-rfx-works"></a>資料錄欄位交換：RFX 的運作方式

本主題介紹 RFX 流程。 這是一個高級主題,涵蓋:

- [RFX 和記錄集](#_core_rfx_and_the_recordset)

- [RFX 流程](#_core_the_record_field_exchange_process)

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的類別。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 要瞭解差異,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX 和記錄集

記錄集物件的欄位數據成員(一起)構成一個編輯緩衝區,該緩衝區保存一條記錄的選定列。 當記錄集首次打開並即將讀取第一條記錄時,RFX 會將每個選定的列綁定(關聯)到相應欄位數據成員的位址。 當記錄集更新記錄時,RFX 調用 ODBC API 函數向驅動程序發送 SQL**更新**或**INSERT**語句。 RFX 使用對欄位數據成員的知識來指定要寫入的列。

框架在某些階段備份編輯緩衝區,以便在必要時還原其內容。 RFX 在添加新記錄之前和編輯現有記錄之前備份編輯緩衝區。 在某些情況下,它還原編輯緩衝區,例如,在以下`Update``AddNew`調用之後。 如果放棄新更改的編輯緩衝區,例如,在調用`Update`之前移動到另一條記錄,則不會還原編輯緩衝區。

除了在數據源和記錄集的欄位數據成員之間交換數據外,RFX 還管理綁定參數。 開啟記錄集時,任何參數數據成員都按`CRecordset::Open`建構的 SQL 語句中的"? 有關詳細資訊,請參閱[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

記錄集類的重寫`DoFieldExchange`執行所有工作,將數據雙向移動。 與對話框數據交換 (DDX) 一樣,RFX 需要有關類數據成員的資訊。 該嚮導通過根據嚮導指定的欄位數據成員名稱和數據類型為您編寫特定於`DoFieldExchange`記錄集的實現來提供必要的資訊。

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>記錄欄位交換流程

本節將 RFX 事件的順序描述為記錄集物件被打開以及添加、更新和刪除記錄時。 本主題中的[RFX 操作在記錄集打開期間](#_core_sequence_of_rfx_operations_during_recordset_open)的順序表[序列和滾動期間 RFX 操作的表序列](#_core_sequence_of_rfx_operations_during_scrolling)顯示該過程,因為`Move`RFX 在記錄集中處理命令,並且 RFX 管理更新。 在這些過程中[,DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)被調用以執行許多不同的操作。 `m_nOperation` [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的數據成員確定請求的操作。 在閱讀此材料之前,您可能會發現閱讀[「記錄集:記錄集如何選擇記錄 (ODBC)」](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)與[「記錄集:記錄集如何更新記錄」(ODBC)非常有用](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX:列和參數的初始綁定

呼叫記錄集物件的[Open](../../mfc/reference/crecordset-class.md#open)成員函數時,按照顯示的順序發生以下 RFX 活動:

- 如果記錄集具有參數數據成員,則框架將調用`DoFieldExchange`以將參數綁定到記錄集 SQL 語句字串中的參數占位符。 參數值的值的數據類型相關表示形式用於**SELECT**語句中找到的每個占位符。 這將在 SQL 語句準備後,但在執行之前發生。 有關語句準備的資訊,請參閱`::SQLPrepare`ODBC*程式師參考 中的*函數。

- 框架第二`DoFieldExchange`次調用以將選取的值綁定到記錄集中的相應欄位數據成員。 這將記錄集物件設置為包含第一個記錄列的編輯緩衝區。

- 記錄集執行 SQL 語句,數據來源選擇第一條記錄。 記錄的列將載入到記錄集的欄位資料成員中。

下表顯示了打開記錄集時的 RFX 操作順序。

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>記錄集開啟期間的 RFX 操作順序

|您的作業|多菲爾德交換操作|資料庫/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1. 打開記錄集。|||
||2. 構建 SQL 語句。||
|||3. 傳送 SQL。|
||4. 綁定參數數據成員。||
||5. 將欄位數據成員綁定到列。||
|||6. ODBC 執行移動並填寫資料。|
||7. 修復C++的數據。||

記錄集使用 ODBC 的已準備執行,以便使用相同的 SQL 語句快速重新查詢。 有關準備執行的詳細資訊,請參閱 MSDN 函式庫中的 ODBC SDK*程式設計師參考*。

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX:滾動

當您從一條記錄滾動到另一個記錄時,`DoFieldExchange`框架將調用以新記錄的值替換以前存儲在字段數據成員中的值。

下表顯示了使用者從記錄移動到記錄時的 RFX 操作順序。

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>捲動期間的 RFX 操作順序

|您的作業|多菲爾德交換操作|資料庫/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.`MoveNext`呼叫或其他移動功能之一。|||
|||2. ODBC 執行移動並填寫資料。|
||3. 修復C++的數據。||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX:新增新記錄並編輯現有記錄

如果添加新記錄,記錄集將充當編輯緩衝區以構建新記錄的內容。 與添加記錄一樣,編輯記錄涉及更改記錄集的欄位數據成員的值。 從 RFX 的角度來看,順序如下:

1. 對記錄集的[「AddNew」](../../mfc/reference/crecordset-class.md#addnew)或[「編輯」](../../mfc/reference/crecordset-class.md#edit)成員函數的調用會導致 RFX 儲存目前編輯緩衝區,以便以後可以還原該緩衝區。

1. `AddNew`或`Edit`準備編輯緩衝區中的欄位,以便 RFX 可以檢測更改的欄位數據成員。

   由於新記錄沒有要比較新值的值,因此`AddNew`將每個欄位數據成員的值設置為PSEUDO_NULL值。 稍後,當您調用`Update`時,RFX 將每個數據成員的值與PSEUDO_NULL值進行比較。 如果存在差異,則已設置數據成員。 (PSEUDO_NULL與具有真實 Null 值的記錄列不同,或者與 C++ NULL 相同。

   與`Update`的`AddNew`調用不同,`Update`調`Edit`用 將更新的值與以前存儲的值進行比較,而不是使用PSEUDO_NULL。 區別在於,`AddNew`沒有以前存儲的值進行比較。

1. 您可以直接設置欄位數據成員的值,這些成員的值要編輯或要填充的新記錄。 這可以包括呼叫`SetFieldNull`。

1. 如步驟 2 中所述,對[更新](../../mfc/reference/crecordset-class.md#update)的調用將檢查已更改的欄位數據成員(請參閱[滾動期間 RFX 操作的表序列](#_core_sequence_of_rfx_operations_during_scrolling))。 如果沒有更改,`Update`則返回 0。 如果某些欄位資料成員已更改,`Update`請準備並執行包含記錄中所有更新欄位的值的 SQL **INSERT**語句。

1. 最後`AddNew`還`Update``AddNew`原 調用之前當前記錄的以前存儲的值。 對於`Edit`,編輯的新值將保留在位。

下表顯示了添加新記錄或編輯現有記錄時 RFX 操作的順序。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>新增和編輯期間的 RFX 操作順序

|您的作業|多菲爾德交換操作|資料庫/SQL 操作|
|--------------------|-------------------------------|-----------------------------|
|1.`AddNew`呼`Edit`叫或 。|||
||2. 備份編輯緩衝區。||
||3.`AddNew`對於 ,將欄位數據成員標記為"乾淨"和"空"。||
|4. 將值分配給記錄集欄位數據成員。|||
|5.`Update`致電 .|||
||6. 檢查更改的欄位。||
||7.**INSERT**`AddNew`為 產生 SQL INSERT**語句或**更新敘述`Edit`。||
|||8. 傳送 SQL。|
||9.`AddNew`對於 ,將編輯緩衝區還原到其備份的內容。 對於`Edit`,請刪除備份。||

### <a name="rfx-deleting-existing-records"></a>RFX:刪除現有記錄

刪除記錄時,RFX 將所有欄位設置為 NULL,以提醒該記錄已被刪除,您必須將其移掉。 您不需要任何其他 RFX 序列資訊。

## <a name="see-also"></a>另請參閱

[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[巨集、全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
