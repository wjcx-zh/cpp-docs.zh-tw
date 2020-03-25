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
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212899"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>資料錄集：AddNew、Edit 和 Delete 的運作方式 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明類別 `CRecordset` 的 `AddNew`、`Edit`和 `Delete` 成員函式如何運作。 涵蓋的主題包括：

- [新增記錄的運作方式](#_core_adding_a_record)

- [已新增記錄的可見度](#_core_visibility_of_added_records)

- [編輯記錄的運作方式](#_core_editing_an_existing_record)

- [刪除記錄的運作方式](#_core_deleting_a_record)

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您使用大量資料列提取，請參閱[記錄集：提取大量的記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

做為補充，您可能會想要讀取[記錄欄位交換： rfx 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)，其中描述更新作業中 rfx 的對應角色。

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>新增記錄

將新記錄加入至記錄集時，需要通話記錄集的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函式、設定新記錄之欄位資料成員的值，以及呼叫[Update](../../mfc/reference/crecordset-class.md#update)成員函式，將記錄寫入至資料來源。

作為呼叫 `AddNew`的前置條件，記錄集不得以唯讀方式開啟。 `CanUpdate` 和 `CanAppend` 成員函式可讓您判斷這些條件。

當您呼叫 `AddNew`：

- 編輯緩衝區中的記錄會儲存，因此如果作業已取消，則可以還原其內容。

- 欄位資料成員會加上旗標，讓您稍後可以偵測到變更。 欄位資料成員也會標示為 [清除（未變更）]，並將設定為 Null。

在您呼叫 `AddNew`之後，編輯緩衝區代表新的空白記錄，準備好填入值。 若要這麼做，您可以指派給它們來手動設定值。 您可以呼叫 `SetFieldNull` 來指定 Null 值，而不是指定欄位的實際資料值。

若要認可您的變更，請呼叫 `Update`。 當您呼叫新記錄的 `Update`：

- 如果您的 ODBC 驅動程式支援 `::SQLSetPos` ODBC API 函式，MFC 會使用函數來加入資料來源上的記錄。 使用 `::SQLSetPos`，MFC 可以更有效率地新增記錄，因為它不需要建立和處理 SQL 語句。

- 如果無法使用 `::SQLSetPos`，MFC 會執行下列動作：

   1. 如果未偵測到任何變更，`Update` 不會執行任何操作，而且會傳回0。

   1. 如果有變更，`Update` 會構造 SQL **INSERT**語句。 所有中途欄位資料成員所代表的資料行都會列在**INSERT**語句中。 若要強制包含資料行，請呼叫[SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty)成員函式：

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` 認可新的記錄，則會執行**INSERT**語句，並將記錄認可至資料來源上的資料表（以及記錄集（如果不是快照集），除非交易正在進行中。

   1. 儲存的記錄會還原至編輯緩衝區。 不論**INSERT**語句是否已成功執行，目前在 `AddNew` 呼叫之前的記錄都是最新的。

   > [!TIP]
   > 若要完全控制新的記錄，請採取下列方法：設定將具有值之任何欄位的值，然後明確地設定任何將維持 Null 的欄位，方法是呼叫具有欄位指標和參數 TRUE （預設值）的 `SetFieldNull`。 如果您想要確保欄位不會寫入至資料來源，請使用欄位的指標呼叫 `SetFieldDirty`，並將參數設為 FALSE，而不要修改欄位的值。 若要判斷欄位是否允許為 Null，請呼叫 `IsFieldNullable`。

   > [!TIP]
   > 若要偵測記錄集資料成員何時變更值，MFC 會針對您可以儲存在記錄集中的每個資料類型，使用適當的 PSEUDO_Null 值。 如果您必須明確地將欄位設定為 PSEUDO_Null 值，而且該欄位已標記為 Null，則您也必須呼叫 `SetFieldNull`，傳遞第一個參數中的欄位位址和第二個參數中的 FALSE。

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>已新增記錄的可見度

當您的記錄集看到加入的記錄時？ 新增的記錄有時會顯示，有時看不到，視兩件事而定：

- 驅動程式的功能。

- 架構可利用的功能。

如果您的 ODBC 驅動程式支援 `::SQLSetPos` ODBC API 函式，MFC 會使用函數來加入記錄。 有了 `::SQLSetPos`，任何可更新的 MFC 記錄集都可以看到已加入的記錄。 若不支援函式，則不會顯示已新增的記錄，而且您必須呼叫 `Requery` 才能查看它們。 使用 `::SQLSetPos` 也會更有效率。

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>編輯現有的記錄

編輯記錄集中的現有記錄牽涉到記錄、通話記錄集的[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式、設定新記錄之欄位資料成員的值，以及呼叫[Update](../../mfc/reference/crecordset-class.md#update)成員函式，將已變更的記錄寫入至資料來源。

作為呼叫 `Edit`的前置條件，記錄集必須是可更新和記錄。 `CanUpdate` 和 `IsDeleted` 成員函式可讓您判斷這些條件。 目前的記錄也必須已經刪除，而且記錄集內必須有記錄（`IsBOF` 和 `IsEOF` 都傳回0）。

當您呼叫 `Edit`時，就會儲存編輯緩衝區（目前記錄）中的記錄。 儲存的記錄值稍後用來偵測是否有任何欄位變更。

在您呼叫 `Edit`之後，編輯緩衝區仍然會代表目前的記錄，但現在已準備好接受欄位資料成員的變更。 若要變更記錄，請手動設定您想要編輯之任何欄位資料成員的值。 您可以呼叫 `SetFieldNull` 來指定 Null 值，而不是指定欄位的實際資料值。 若要認可您的變更，請呼叫 `Update`。

> [!TIP]
> 若要離開 `AddNew` 或 `Edit` 模式，請使用參數*AFX_MOVE_REFRESH*來呼叫 `Move`。

作為呼叫 `Update`的前置條件，記錄集不得為空白，而且目前的記錄也不得被刪除。 `IsBOF`、`IsEOF`和 `IsDeleted` 都應該傳回0。

當您針對已編輯的記錄呼叫 `Update` 時：

- 如果您的 ODBC 驅動程式支援 `::SQLSetPos` ODBC API 函式，MFC 會使用函數來更新資料來源上的記錄。 使用 `::SQLSetPos`，驅動程式會比較您的編輯緩衝區與伺服器上的對應記錄，如果兩者不同，則補救伺服器上的記錄。 使用 `::SQLSetPos`，MFC 可以更有效率地更新記錄，因為它不需要建立和處理 SQL 語句。

   \- 或 -

- 如果無法使用 `::SQLSetPos`，MFC 會執行下列動作：

   1. 如果沒有任何變更，`Update` 不會執行任何操作，而且會傳回0。

   1. 如果有變更，`Update` 會構造 SQL **UPDATE**語句。 **UPDATE**語句中列出的資料行是以已變更的欄位資料成員為基礎。

   1. `Update` 認可變更（執行**UPDATE**語句），而且資料來源上的記錄會變更，但如果交易正在進行中，則不會認可（如需交易如何影響更新的詳細資訊，請參閱[交易：在記錄集內執行交易（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) ）。 ODBC 會保留一份記錄複本，這也會一併變更。

   1. 不同于 `AddNew`的程式，`Edit` 進程不會還原已儲存的記錄。 編輯過的記錄會保留在目前記錄的位置。

   > [!CAUTION]
   > 當您藉由呼叫 `Update`來準備更新記錄集時，請注意您的記錄集包括組成資料表主鍵的所有資料行（或資料表上任何唯一索引的所有資料行，或足以唯一識別資料列的資料行）。 在某些情況下，架構只能使用在您的記錄集中選取的資料行，來識別要更新的資料表中的哪一筆記錄。 如果沒有所有必要的資料行，資料表中可能會更新多筆記錄。 在此情況下，當您呼叫 `Update`時，架構會擲回例外狀況。

   > [!TIP]
   > 如果您在之前呼叫了任何一個函式，但在呼叫 `Update`之前呼叫 `AddNew` 或 `Edit`，則會使用預存的記錄來重新整理編輯緩衝區，並取代正在進行的新的或編輯過的記錄。 此行為可讓您中止 `AddNew` 或 `Edit`，並開始新的工作：如果您判斷記錄進行中的問題，只需再次呼叫 `Edit` 或 `AddNew`。

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>刪除記錄

從記錄集刪除記錄牽涉到要滾動到記錄，以及通話記錄集的[Delete](../../mfc/reference/crecordset-class.md#delete)成員函式。 不同于 `AddNew` 和 `Edit`，`Delete` 不需要對 `Update`進行相符的呼叫。

作為呼叫 `Delete`的前置條件，記錄集必須是可更新的，而且必須在記錄上。 `CanUpdate`、`IsBOF`、`IsEOF`和 `IsDeleted` 成員函式可讓您判斷這些條件。

當您呼叫 `Delete`：

- 如果您的 ODBC 驅動程式支援 `::SQLSetPos` ODBC API 函式，MFC 會使用函數來刪除資料來源上的記錄。 使用 `::SQLSetPos` 通常比使用 SQL 更有效率。

   \- 或 -

- 如果無法使用 `::SQLSetPos`，MFC 會執行下列動作：

   1. 編輯緩衝區中的目前記錄不會如 `AddNew` 和 `Edit`備份。

   1. `Delete` 會建立移除記錄的 SQL **DELETE**語句。

      編輯緩衝區中的目前記錄不會儲存為 `AddNew` 和 `Edit`中的。

   1. `Delete` 認可刪除作業時，會執行**DELETE**語句。 資料來源上的記錄會標示為 deleted，而如果記錄是快照集，則為 ODBC 中的。

   1. 已刪除記錄的值仍在記錄集的欄位資料成員中，但是欄位資料成員會標記為 Null，而記錄集的 `IsDeleted` 成員函式會傳回非零值。

   > [!NOTE]
   > 刪除記錄之後，您應該滾動到另一筆記錄，以使用新的記錄資料來重新填滿編輯緩衝區。 再次呼叫 `Delete` 或呼叫 `Edit`時發生錯誤。

如需更新作業中使用之 SQL 語句的詳細資訊，請參閱[sql](../../data/odbc/sql.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：更多更新的詳細資訊 (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
