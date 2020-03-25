---
title: 資料錄集：加入、更新和刪除資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 14fc26709541135e80a2e0fe4de872cc75221874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213001"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>資料錄集：加入、更新和刪除資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

> [!NOTE]
>  您現在可以更有效率地新增記錄。 如需詳細資訊，請參閱[記錄集：加入大量記錄（ODBC）](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您使用大量資料列提取，請參閱[記錄集：提取大量的記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

可更新的快照和動態集可以讓您加入、編輯（更新）和刪除記錄。 本主題將說明：

- [如何判斷您的記錄集是否可更新](#_core_determining_whether_your_recordset_is_updatable)。

- [如何新增記錄](#_core_adding_a_record_to_a_recordset)。

- [如何編輯現有的記錄](#_core_editing_a_record_in_a_recordset)。

- [如何刪除記錄](#_core_deleting_a_record_from_a_recordset)。

如需如何執行更新以及如何對其他使用者顯示更新的詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。 一般來說，當您加入、編輯或刪除記錄時，記錄集會立即變更資料來源。 您可以改為將相關更新的群組批次處理成交易。 如果交易正在進行中，則在您認可交易之前，更新不會變成最終狀態。 這可讓您取回或復原變更。 如需交易的詳細資訊，請參閱[Transaction （ODBC）](../../data/odbc/transaction-odbc.md)。

下表摘要說明具有不同更新特性之記錄集的可用選項。

### <a name="recordset-readupdate-options"></a>記錄集讀取/更新選項

|類型|讀取|編輯記錄|刪除記錄|加入新的（附加）|
|----------|----------|-----------------|-------------------|------------------------|
|唯讀|Y|N|N|N|
|僅附加|Y|N|N|Y|
|完全可更新|Y|Y|Y|Y|

##  <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>判斷您的記錄集是否可更新

如果資料來源可更新，而且您已將記錄集開啟為可更新，則記錄集物件可更新。 其可更新性也取決於您所使用的 SQL 語句、ODBC 驅動程式的功能，以及 ODBC 資料指標程式庫是否在記憶體中。 您無法更新唯讀的記錄集或資料來源。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>判斷您的記錄集是否可更新

1. 通話記錄集物件的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式。

   如果記錄集是可更新的，`CanUpdate` 會傳回非零值。

根據預設，記錄集是完全可更新的（您可以執行 `AddNew`、`Edit`和 `Delete` 作業）。 但是您也可以使用[appendOnly](../../mfc/reference/crecordset-class.md#open)選項來開啟可更新的記錄集。 以這種方式開啟的記錄集會只允許使用 `AddNew`加入新記錄。 您無法編輯或刪除現有的記錄。 您可以藉由呼叫[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函式，測試記錄集是否只開啟以供附加。 如果記錄集可以完全更新，或只針對附加而開啟，`CanAppend` 會傳回非零值。

下列程式碼會示範如何將 `CanUpdate` 用於名為 `rsStudentSet`的記錄集物件：

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
>  當您藉由呼叫 `Update`來準備更新記錄集時，請注意您的記錄集包含組成資料表主鍵的所有資料行（或資料表上任何唯一索引的所有資料行）。 在某些情況下，架構只能使用在您的記錄集中選取的資料行，來識別要更新的資料表中的哪一筆記錄。 如果沒有所有必要的資料行，資料表中的多筆記錄可能會更新，可能會破壞資料表的參考完整性。 在此情況下，當您呼叫 `Update`時，架構會擲回例外狀況。

##  <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>將記錄加入至記錄集

如果記錄集的[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函式傳回非零值，您可以將新記錄加入至記錄集。

#### <a name="to-add-a-new-record-to-a-recordset"></a>若要將新記錄加入至記錄集

1. 請確定記錄集是可附加的。

1. 通話記錄集物件的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函式。

   `AddNew` 準備要做為編輯緩衝區的記錄集。 所有欄位資料成員都會設定為特殊值 Null，並將其標示為未變更，因此當您呼叫[Update](../../mfc/reference/crecordset-class.md#update)時，只會將變更的（變更的）值寫入至資料來源。

1. 設定新記錄之欄位資料成員的值。

   將值指派給欄位資料成員。 您未指派的使用者不會寫入至資料來源。

1. 通話記錄集物件的 `Update` 成員函式。

   `Update` 藉由將新記錄寫入資料來源來完成新增。 如需當您無法呼叫 `Update`時所發生的詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

如需如何加入記錄的詳細資訊，以及在記錄集內顯示加入記錄的時機，請參閱[記錄集： AddNew、Edit 和 Delete Work （ODBC）](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。

下列範例顯示如何新增記錄：

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
>  若要取消 `AddNew` 或 `Edit` 呼叫，請直接對 `AddNew` 或 `Edit` 進行另一個呼叫，或使用 *`Move`* 參數呼叫 AFX_MOVE_REFRESH。 資料成員會重設為先前的值，而您仍處於 `Edit` 或 `Add` 模式。

##  <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>編輯記錄集中的記錄

如果您的記錄集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式傳回非零值，您可以編輯現有的記錄。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>若要編輯記錄集中的現有記錄

1. 請確定記錄集是可更新的。

1. 流覽至您想要更新的記錄。

1. 通話記錄集物件的[Edit](../../mfc/reference/crecordset-class.md#edit)成員函式。

   `Edit` 準備要做為編輯緩衝區的記錄集。 所有欄位資料成員都會標示，讓記錄集能夠在稍後知道是否已變更。 當您呼叫[Update](../../mfc/reference/crecordset-class.md#update)時，已變更欄位資料成員的新值會寫入至資料來源。

1. 設定新記錄之欄位資料成員的值。

   將值指派給欄位資料成員。 您未指派值的資料會維持不變。

1. 通話記錄集物件的 `Update` 成員函式。

   `Update` 將已變更的記錄寫入至資料來源，以完成編輯。 如需當您無法呼叫 `Update`時所發生的詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

編輯記錄之後，編輯過的記錄仍會保留目前的記錄。

下列範例顯示 `Edit` 作業。 它會假設使用者已移至他想要編輯的記錄。

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> 若要取消 `AddNew` 或 `Edit` 呼叫，請直接對 `AddNew` 或 `Edit` 進行另一個呼叫，或使用 *`Move`* 參數呼叫 AFX_MOVE_REFRESH。 資料成員會重設為先前的值，而您仍處於 `Edit` 或 `Add` 模式。

##  <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>從記錄集刪除記錄

如果您的記錄集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式傳回非零值，您可以刪除記錄。

#### <a name="to-delete-a-record"></a>若要刪除記錄

1. 請確定記錄集是可更新的。

1. 流覽至您想要更新的記錄。

1. 通話記錄集物件的[Delete](../../mfc/reference/crecordset-class.md#delete)成員函式。

   `Delete` 會立即將記錄標示為已刪除，這兩者都在記錄集和資料來源上。

   不同于 `AddNew` 和 `Edit`，`Delete` 沒有對應的 `Update` 呼叫。

1. 流覽至另一筆記錄。

   > [!NOTE]
   >  在記錄集之間移動時，可能不會略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成員函式。

下列範例顯示 `Delete` 作業。 它會假設使用者已移至使用者想要刪除的記錄。 呼叫 `Delete` 之後，請務必移至新的記錄。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

如需 `AddNew`、`Edit`和 `Delete` 成員函式之效果的詳細資訊，請參閱[記錄集：記錄集更新記錄的方式（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
