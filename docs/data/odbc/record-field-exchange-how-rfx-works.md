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
ms.openlocfilehash: 9e717d0f0ce3b8841feee2beb457fee7221fcf69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403786"
---
# <a name="record-field-exchange-how-rfx-works"></a>資料錄欄位交換：RFX 的運作方式

本主題將說明 RFX 進程。 這是一個涵蓋下列內容的先進主題：

- [RFX 和記錄集](#_core_rfx_and_the_recordset)

- [RFX 進程](#_core_the_record_field_exchange_process)

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的類別。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 若要瞭解差異，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX 和記錄集

記錄集物件的欄位資料成員（結合在一起）組成一個編輯緩衝區，其中包含一個記錄的選取資料行。 當記錄集第一次開啟，而且即將讀取第一筆記錄時，RFX 會將每個選取的資料行系結（關聯）至適當欄位資料成員的位址。 當記錄集更新記錄時，RFX 會呼叫 ODBC API 函數，將 SQL **UPDATE**或**INSERT**語句傳送到驅動程式。 RFX 會使用欄位資料成員的知識來指定要寫入的資料行。

架構會在特定階段備份編輯緩衝區，讓它可以在必要時還原其內容。 RFX 會在新增記錄之前，以及在編輯現有記錄之前，先備份編輯緩衝區。 在某些情況下，它會還原編輯緩衝區，例如，在 `Update` 呼叫之後 `AddNew` 。 如果您放棄新變更的編輯緩衝區（例如，在呼叫之前移至另一筆記錄），則不會還原編輯緩衝區。 `Update`

除了在資料來源與記錄集的欄位資料成員之間交換資料之外，RFX 也會管理系結參數。 當記錄集開啟時，任何參數資料成員都會以結構之 SQL 語句中的 "？" 預留位置順序系結 `CRecordset::Open` 。 如需詳細資訊，請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

您的記錄集類別的覆寫 `DoFieldExchange` 會執行所有工作，並雙向移動資料。 如同對話方塊資料交換（DDX），RFX 需要類別的資料成員的相關資訊。 此 wizard `DoFieldExchange` 會根據您使用 wizard 指定的欄位資料成員名稱和資料類型，為您撰寫記錄集特有的執行，以提供必要的資訊。

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>記錄欄位交換進程

本節說明當記錄集物件開啟，以及您加入、更新和刪除記錄時，RFX 事件的順序。 在[記錄集開啟期間，Rfx 作業](#_core_sequence_of_rfx_operations_during_recordset_open)的資料表順序和在本主題中[滾動期間 rfx 作業](#_core_sequence_of_rfx_operations_during_scrolling)的資料表順序，會顯示 RFX 處理 `Move` 記錄集中的命令，而且 rfx 會管理更新。 在這些過程中，會呼叫[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)來執行許多不同的作業。 `m_nOperation` [CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的資料成員會判斷所要求的作業。 您可能會發現讀取記錄集很有説明：記錄集[如何選取記錄（odbc）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[記錄集：記錄集如何更新記錄（odbc）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) ，然後再讀取此資料。

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX：資料行和參數的初始系結

當您通話記錄集物件的[Open](../../mfc/reference/crecordset-class.md#open)成員函式時，會依顯示的循序執行下列 RFX 活動：

- 如果記錄集具有參數資料成員，則架構會呼叫， `DoFieldExchange` 將參數系結至記錄集的 SQL 語句字串中的參數預留位置。 參數值的資料類型相依標記法會用於**SELECT**語句中找到的每個預留位置。 這會在 SQL 語句準備好之後，但在執行之前發生。 如需語句準備的相關資訊，請參閱 ODBC 程式設計 `::SQLPrepare` *人員參考*中的函數。

- 架構會呼叫 `DoFieldExchange` 第二次，將所選資料行的值系結至記錄集內的對應欄位資料成員。 這會建立記錄集物件做為編輯緩衝區，其中包含第一筆記錄的資料行。

- 記錄集會執行 SQL 語句，而資料來源會選取第一筆記錄。 記錄的資料行會載入記錄集的欄位資料成員中。

下表顯示當您開啟記錄集時的 RFX 作業順序。

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>記錄集開啟期間的 RFX 作業順序

|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|
|--------------------|-------------------------------|-----------------------------|
|1. 開啟記錄集。|||
||2. 建立 SQL 語句。||
|||3. 傳送 SQL。|
||4. 系結參數資料成員。||
||5. 將欄位資料成員系結至資料行。||
|||6. ODBC 會執行移動並填入資料。|
||7. 修正 c + + 的資料。||

記錄集使用 ODBC 的備妥執行，以允許使用相同的 SQL 語句快速地重新查詢。 如需準備執行的詳細資訊，請參閱 ODBC 程式設計[人員參考](/sql/odbc/reference/odbc-programmer-s-reference)。

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX：滾動

當您從某一筆記錄滾動到另一個時，架構會呼叫 `DoFieldExchange` 來將先前儲存在欄位資料成員中的值取代為新記錄的值。

下表顯示當使用者從記錄移至記錄時，RFX 作業的順序。

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>在滾動期間的 RFX 作業順序

|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|
|--------------------|-------------------------------|-----------------------------|
|1. 呼叫 `MoveNext` 或其中一個移動函數。|||
|||2. ODBC 會執行移動並填入資料。|
||3. 修正 c + + 的資料。||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX：加入新記錄和編輯現有的記錄

如果您加入新的記錄，記錄集就會當做編輯緩衝區運作，以建立新記錄的內容。 如同加入記錄，編輯記錄牽涉到變更記錄集的欄位資料成員的值。 從 RFX 的角度來看，順序如下所示：

1. 您對記錄集之[AddNew](../../mfc/reference/crecordset-class.md#addnew)或[Edit](../../mfc/reference/crecordset-class.md#edit)成員函式的呼叫會導致 RFX 儲存目前的編輯緩衝區，讓它可以在稍後還原。

1. `AddNew`或 `Edit` 準備編輯緩衝區中的欄位，讓 RFX 能夠偵測到已變更的欄位資料成員。

   因為新的記錄沒有先前的值來比較新的記錄，所以會 `AddNew` 將每個欄位資料成員的值設定為 PSEUDO_Null 值。 之後，當您呼叫時 `Update` ，RFX 會將每個資料成員的值與 PSEUDO_Null 值進行比較。 如果有差異，則資料成員已設定。 （PSEUDO_Null 與具有 true Null 值的記錄資料行不同，也不會與 c + + Null 相同）。

   不同于的 `Update` 呼叫 `AddNew` ，的 `Update` 呼叫會 `Edit` 比較已更新的值與先前儲存的值，而不是使用 PSEUDO_Null。 差別在於， `AddNew` 先前沒有儲存值可供比較。

1. 您可以直接設定您想要編輯其值的欄位資料成員值，或您想要填入新記錄的值。 這可能包括呼叫 `SetFieldNull` 。

1. 您對[更新](../../mfc/reference/crecordset-class.md#update)的呼叫會檢查已變更的欄位資料成員（如步驟2中所述）（請參閱[滾動期間的 RFX 作業](#_core_sequence_of_rfx_operations_during_scrolling)的資料表順序）。 如果沒有變更，則會傳回 `Update` 0。 如果某些欄位資料成員已變更，請 `Update` 準備並執行 SQL **INSERT**語句，其中包含記錄中所有更新欄位的值。

1. 若為 `AddNew` ，則 `Update` 會在呼叫之前還原先前所儲存的記錄值來結束 `AddNew` 。 針對 `Edit` ，已編輯的新值會保留在原處。

下表顯示當您加入新的記錄或編輯現有的記錄時，RFX 作業的順序。

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>在 AddNew 和 Edit 期間的 RFX 作業順序

|您的作業|DoFieldExchange 作業|資料庫/SQL 作業|
|--------------------|-------------------------------|-----------------------------|
|1. 呼叫 `AddNew` 或 `Edit` 。|||
||2. 備份編輯緩衝區。||
||3. 針對 `AddNew` ，將欄位資料成員標示為「清除」和 Null。||
|4. 將值指派給記錄集欄位資料成員。|||
|5. 呼叫 `Update` 。|||
||6. 檢查已變更的欄位。||
||7. 為**INSERT** `AddNew` 或**UPDATE**語句建立 SQL INSERT 語句 `Edit` 。||
|||8. 傳送 SQL。|
||9. 若是 `AddNew` ，請將編輯緩衝區還原至其已備份的內容。 針對 `Edit` ，刪除備份。||

### <a name="rfx-deleting-existing-records"></a>RFX：刪除現有的記錄

當您刪除記錄時，RFX 會將所有欄位設定為 Null，提醒您刪除記錄，而且您必須將它移出。 您不需要任何其他 RFX 順序資訊。

## <a name="see-also"></a>另請參閱

[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)<br/>
[MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[巨集、全域函式和全域變數](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
