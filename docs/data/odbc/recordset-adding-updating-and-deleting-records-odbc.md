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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367099"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>資料錄集：加入、更新和刪除資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

> [!NOTE]
> 現在,您可以更高效地批量添加記錄。 有關詳細資訊,請參閱[記錄集:批量添加記錄 (ODBC)。](../../data/odbc/recordset-adding-records-in-bulk-odbc.md)

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果使用批量行提取,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

可更新的快照和動態集允許您添加、編輯(更新)和刪除記錄。 本主題將說明：

- [如何確定您的紀錄集是否可更新](#_core_determining_whether_your_recordset_is_updatable)。

- [如何新增新紀錄](#_core_adding_a_record_to_a_recordset)。

- [如何編輯現有紀錄](#_core_editing_a_record_in_a_recordset)。

- [如何刪除紀錄](#_core_deleting_a_record_from_a_recordset)。

有關如何執行更新以及更新如何向其他用戶顯示的詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) 通常,當您添加、編輯或刪除記錄時,記錄集會立即更改數據源。 您可以將相關更新組批處理到事務中。 如果事務正在進行,則在提交事務之前,更新不會成為最終更新。 這允許您收回或回滾更改。 有關交易記錄的資訊,請參閱[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

下表總結了具有不同更新特徵的記錄集可用的選項。

### <a name="recordset-readupdate-options"></a>記錄集讀取/更新選項

|類型|讀取|編輯記錄|刪除記錄|新增新增(附加)|
|----------|----------|-----------------|-------------------|------------------------|
|唯讀|Y|N|N|N|
|只附加|Y|N|N|Y|
|完全可上|Y|Y|Y|Y|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>確定記錄集是否可更新

如果數據源是可更新的,並且將記錄集打開為可更新的,則記錄集對像是可更新的。 其可更新性還取決於您使用的 SQL 語句、ODBC 驅動程式的功能以及 ODBC 游標庫是否位於記憶體中。 不能更新唯讀記錄集或數據源。

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>確定記錄集是否可更新

1. 調用記錄集物件的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函數。

   `CanUpdate`如果記錄集是可更新的,則返回非零值。

預設情況下,記錄集是完全可更新的(您可以執行`AddNew`和`Edit``Delete`操作)。 但是,您也可以使用[「僅追加」](../../mfc/reference/crecordset-class.md#open)選項打開可更新的記錄集。 以這種方式打開的記錄集只允許使用`AddNew`添加新記錄。 您不能編輯或刪除現有記錄。 您可以通過調用[CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函數來測試記錄集是否僅打開以進行追加。 `CanAppend`如果記錄集是完全可更新的,或者僅打開以追加,則返回非零值。

以下代碼顯示如何使用`CanUpdate`名為的紀錄集物件: `rsStudentSet`

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
> 當您準備通過調用`Update`更新記錄集時,請注意,記錄集包含組成表主鍵的所有列(或表上任何唯一索引的所有列)。 在某些情況下,框架只能使用記錄集中選擇的列來標識要更新的表中的記錄。 如果沒有所有必要的列,則表中可能會更新多個記錄,從而可能損壞表的引用完整性。 在這種情況下,框架在調用`Update`時會引發異常。

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>新增記錄到記錄集

如果記錄集[的 CanAppend](../../mfc/reference/crecordset-class.md#canappend)成員函數返回非零值,則可以向記錄集添加新記錄集。

#### <a name="to-add-a-new-record-to-a-recordset"></a>新增新紀錄到紀錄集

1. 確保記錄集是可追加的。

1. 調用記錄集物件的[AddNew](../../mfc/reference/crecordset-class.md#addnew)成員函數。

   `AddNew`準備記錄集以充當編輯緩衝區。 所有欄位資料成員都設置為特殊值 Null,並標記為"無",因此僅在調用[Update](../../mfc/reference/crecordset-class.md#update)時將更改(髒)值寫入數據來源。

1. 設置新記錄的欄位數據成員的值。

   將值分配給欄位數據成員。 您未分配的那些不會寫入資料來源。

1. 調用記錄集對`Update`象的成員函數。

   `Update`通過將新記錄寫入數據源來完成添加。 有關未能調用`Update`時發生的情況的資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

有關添加記錄的工作原理以及添加記錄在記錄集中何時可見的資訊,請參閱[記錄集:如何添加新、編輯和刪除工作 (ODBC)。](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)

下面的範例展示如何新增新紀錄:

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
> 要取消`AddNew``Edit`或呼叫,只需*AFX_MOVE_REFRESH*使用`AddNew`AFX_MOVE_REFRESH參數`Edit`撥打`Move`或呼叫 即可。 數據成員將重置為其以前的值,您仍處於`Edit`或`Add`模式下。

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>紀錄集中編輯記錄

如果記錄集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函數返回非零值,則可以編輯現有記錄。

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>編輯記錄集中的現有記錄

1. 確保記錄集是可更新的。

1. 滾動到要更新的記錄。

1. 呼叫記錄集物件的[「編輯](../../mfc/reference/crecordset-class.md#edit)」成員函數。

   `Edit`準備記錄集以充當編輯緩衝區。 標記所有欄位數據成員,以便記錄集可以稍後判斷它們是否已更改。 當您調用[Update](../../mfc/reference/crecordset-class.md#update)時,更改欄位數據成員的新值將寫入數據來源。

1. 設置新記錄的欄位數據成員的值。

   將值分配給欄位數據成員。 不分配值的值保持不變。

1. 調用記錄集對`Update`象的成員函數。

   `Update`通過將更改的記錄寫入數據源來完成編輯。 有關未能調用`Update`時發生的情況的資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

編輯記錄後,編輯的記錄將保留當前記錄。

下面的示例顯示一個`Edit`操作。 它假定使用者已移動到他或她要編輯的記錄。

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
> 要取消`AddNew``Edit`或呼叫,只需*AFX_MOVE_REFRESH*使用`AddNew`AFX_MOVE_REFRESH參數`Edit`撥打`Move`或呼叫 即可。 數據成員將重置為其以前的值,您仍處於`Edit`或`Add`模式下。

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>從紀錄集中移除記錄

如果記錄集的[CanUpdate](../../mfc/reference/crecordset-class.md#canupdate)成員函數返回非零值,則可以刪除記錄。

#### <a name="to-delete-a-record"></a>刪除記錄

1. 確保記錄集是可更新的。

1. 滾動到要更新的記錄。

1. 呼叫記錄集物件的[「刪除](../../mfc/reference/crecordset-class.md#delete)」成員函數。

   `Delete`立即將記錄標記為已刪除,無論是在記錄集中還是在數據源上。

   與`AddNew``Edit``Delete`和`Update`不同 ,沒有相應的呼叫。

1. 滾動到另一條記錄。

   > [!NOTE]
   >  在記錄集中移動時,可能不會跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](../../mfc/reference/crecordset-class.md#isdeleted)函數。

下面的示例顯示一個`Delete`操作。 它假定使用者已移動到使用者要刪除的記錄。 調用`Delete`後,請務必移動到新記錄。

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

`AddNew`有關`Edit``Delete`和成員函數的效果的詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
