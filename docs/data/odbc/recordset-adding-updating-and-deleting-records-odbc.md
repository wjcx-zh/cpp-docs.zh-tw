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
ms.openlocfilehash: a13bffdc79f01c49c290b8b5d4388f06ce777105
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512368"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>資料錄集：加入、更新和刪除資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

> [!NOTE]
>  您現在可以更有效率地加入大量資料錄。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 新增錄大量 (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)。

> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

可更新的快照集和動態集可讓您加入、 編輯 (update)，和刪除記錄。 本主題說明：

- [如何判斷是否可更新資料錄集](#_core_determining_whether_your_recordset_is_updatable)。

- [如何加入新的記錄](#_core_adding_a_record_to_a_recordset)。

- [如何編輯現有的記錄](#_core_editing_a_record_in_a_recordset)。

- [如何刪除資料錄](#_core_deleting_a_record_from_a_recordset)。

如需有關如何執行更新 out 以及如何更新您的顯示給其他使用者，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。 一般來說，當您新增、 編輯或刪除記錄時，資料錄集的資料來源會立即變更。 您可以群組批次的相關更新成交易。 如果異動正在進行中，更新之前，不會最終認可交易。 這可讓您能取回或回復的變更。 交易的相關資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

下表摘要說明適用於具有不同的更新特性的資料錄集的選項。

### <a name="recordset-readupdate-options"></a>資料錄集 Read/Update 選項

|類型|讀取|編輯記錄|刪除記錄|加入新 （附加）|
|----------|----------|-----------------|-------------------|------------------------|
|唯讀|Y|N|N|N|
|僅附加|Y|N|N|Y|
|可完全更新|Y|Y|Y|Y|

##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> 決定是否資料錄集是可更新

如果資料來源是可更新，而您開啟為可更新資料錄集，可更新資料錄集物件。 其可更新性也取決於 SQL 陳述式使用時，ODBC 驅動程式的功能，以及 ODBC 資料指標程式庫是否在記憶體中。 您無法更新唯讀的資料錄集或資料來源。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>若要判斷是否可更新資料錄集

1. 呼叫資料錄集物件的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式。

   `CanUpdate` 如果資料錄集是可更新，則傳回非零值。

根據預設，會完全可更新資料錄集 (您可以執行`AddNew`， `Edit`，和`Delete`作業)。 您也可以使用，但[appendOnly](../../mfc/reference/crecordset-class.md#open)選項來開啟可更新資料錄集。 此方法來開啟資料錄集只允許使用新資料錄`AddNew`。 您無法編輯或刪除現有的記錄。 您可以測試是否資料錄集是開啟只能藉由呼叫附加[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函式。 `CanAppend` 如果資料錄集是完全可更新或開啟附加的只會傳回非零值。

下列程式碼示範如何使用`CanUpdate`對於資料錄集物件呼叫`rsStudentSet`:

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
>  當您準備好要呼叫來更新資料錄集`Update`，處理資料錄集，包含組成資料表 （或所有資料表上的任何唯一索引的資料行） 的主索引鍵的所有資料行。 在某些情況下，架構就可以使用只選取您的資料錄集中的資料行來識別您要更新的資料表中的記錄。 沒有所有必要的資料行，可能會在資料表中，而損害之資料表的參考完整性更新多筆記錄。 在此情況下，架構就會擲回例外狀況呼叫`Update`。

##  <a name="_core_adding_a_record_to_a_recordset"></a> 將記錄新增到資料錄集

您可以將新記錄新增至資料錄集，如果其[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函式傳回非零值。

#### <a name="to-add-a-new-record-to-a-recordset"></a>將新記錄新增至資料錄集

1. 請確定可附加資料錄集。

1. 呼叫資料錄集物件的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函式。

   `AddNew` 準備做為編輯緩衝區的資料錄集。 所有的欄位資料成員會設定為特殊值 Null，並標示為不變，因此當您呼叫只是變更 (dirty) 值會寫入至資料來源[更新](../../mfc/reference/crecordset-class.md#update)。

1. 設定新的記錄欄位資料成員的值。

   指派值給欄位資料成員。 這些未指派不會寫入至資料來源。

1. 呼叫資料錄集物件的`Update`成員函式。

   `Update` 完成新增新的記錄寫入的資料來源。 進行資訊後，如果您無法呼叫`Update`，請參閱 <<c2> [ 資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

如需加入資料錄的方式運作，以及新增的記錄時顯示在資料錄集的相關資訊，請參閱 <<c0> [ 資料錄集： 如何 AddNew、 Edit 和刪除工作 (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)。

下列範例示範如何加入新的記錄：

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
>  若要取消`AddNew`或`Edit`呼叫，只要呼叫另一個以`AddNew`或`Edit`或致電`Move`使用*AFX_MOVE_REFRESH*參數。 資料成員會重設為其先前的值，但仍處於`Edit`或`Add`模式。

##  <a name="_core_editing_a_record_in_a_recordset"></a> 編輯資料錄集中的資料錄集

您可以編輯現有的記錄，如果您的資料錄集[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式傳回非零值。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>若要編輯現有資料錄集中的資料錄

1. 請確定資料錄集是可更新。

1. 捲動至您想要更新的記錄。

1. 呼叫資料錄集物件的[編輯](../../mfc/reference/crecordset-class.md#edit)成員函式。

   `Edit` 準備做為編輯緩衝區的資料錄集。 因此，資料錄集就可以分辨之後是否已變更，就會標示所有欄位資料成員。 已變更的欄位資料成員的新值寫入至資料來源，當您呼叫[更新](../../mfc/reference/crecordset-class.md#update)。

1. 設定新的記錄欄位資料成員的值。

   指派值給欄位資料成員。 這些未指派的值維持不變。

1. 呼叫資料錄集物件的`Update`成員函式。

   `Update` 完成編輯已變更的記錄寫入的資料來源。 進行資訊後，如果您無法呼叫`Update`，請參閱 <<c2> [ 資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

編輯一筆記錄之後，請編輯的記錄會保留目前的記錄。

下列範例所示`Edit`作業。 它會假設使用者已移至他或她想要編輯的記錄。

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
> 若要取消`AddNew`或`Edit`呼叫，只要呼叫另一個以`AddNew`或`Edit`或致電`Move`使用*AFX_MOVE_REFRESH*參數。 資料成員會重設為其先前的值，但仍處於`Edit`或`Add`模式。

##  <a name="_core_deleting_a_record_from_a_recordset"></a> 刪除記錄，從資料錄集

您可以刪除記錄，如果您的資料錄集[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函式傳回非零值。

#### <a name="to-delete-a-record"></a>若要刪除的記錄

1. 請確定資料錄集是可更新。

1. 捲動至您想要更新的記錄。

1. 呼叫資料錄集物件的[刪除](../../mfc/reference/crecordset-class.md#delete)成員函式。

   `Delete` 立即將記錄標示為刪除，但在資料錄集和資料來源。

   不同於`AddNew`並`Edit`，`Delete`沒有對應的`Update`呼叫。

1. 捲動到另一筆記錄。

   > [!NOTE]
   >  當您移動到資料錄集，已刪除的記錄可能不會略過。 如需詳細資訊，請參閱 < [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成員函式。

下列範例所示`Delete`作業。 它會假設使用者已移至使用者想要刪除的記錄。 之後`Delete`是呼叫，請務必將移至新的記錄。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

如需詳細資訊，所帶來的影響`AddNew`， `Edit`，並`Delete`成員函式，請參閱[資料錄集： 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)