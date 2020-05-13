---
title: 資料錄集：捲動 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366932"
---
# <a name="recordset-scrolling-odbc"></a>資料錄集：捲動 (ODBC)

本主題適用於 MFC ODBC 類別。

打開記錄集后,需要訪問記錄以顯示值、執行計算、生成報告等。 通過滾動,您可以在記錄集中從記錄移動到記錄。

本主題將說明：

- [如何在紀錄集中從一個紀錄捲軸到另一個紀錄](#_core_scrolling_from_one_record_to_another)。

- [在什麼情況下滾動是,不支援](#_core_when_scrolling_is_supported)。

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>從一個紀錄捲軸到另一個紀錄

類`CRecordset`提供`Move`用於在記錄集中滾動的成員函數。 這些函數按行集移動當前記錄。 如果已實現批量行提取,`Move`則操作按行集的大小重新定位記錄集。 如果尚未實現批量行提取,則對`Move`函數的調用會每次都將記錄集重新定位一條記錄。 有關批量行提取的詳細資訊,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> 在記錄集中移動時,可能不會跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](../../mfc/reference/crecordset-class.md#isdeleted)函數。

除了`Move`函數之外,`CRecordset`還提供成員函數,用於檢查您是否在記錄集的末尾或之前滾動過。

要確定記錄集中是否可以滾動,請調用`CanScroll`成員函數。

#### <a name="to-scroll"></a>滾動

1. 轉發一條記錄或一個行集:調用[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成員函數。

1. 向後一個記錄或一個行集:調用[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成員函數。

1. 到記錄集中的第一個記錄:調用[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成員函數。

1. 到記錄集中或最後一個行集中的最後一個記錄:調用[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成員函數。

1. *N*條記錄相對於當前位置:調用[移動](../../mfc/reference/crecordset-class.md#move)成員函數。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>測試記錄集的結束或開頭

1. 你滾動過最後一條記錄了嗎? 調用[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成員函數。

1. 您是否在第一條記錄之前滾動(向後移動)? 調用[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成員函數。

以下代碼示例使用`IsBOF``IsEOF`並檢測記錄集在任一方向滾動時的限制。

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF`如果記錄集位於最後一條記錄的過去,則返回非零值。 `IsBOF`如果記錄集位於第一條記錄之前(在所有記錄之前),則返回非零值。 在這兩種情況下,都沒有要操作的當前記錄。 如果在已為`MovePrev``IsBOF`TRUE 時呼`MoveNext`叫`IsEOF`, 或是呼叫時已為`CDBException`TRUE,則框架將引發 。 您還可以使用`IsBOF`和`IsEOF`檢查空記錄集。

有關記錄集導航的詳細資訊,請參閱[記錄集:書籤和絕對位置 (ODBC)。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>支援捲動時

按照最初設計,SQL 僅提供前進滾動,但 ODBC 擴展滾動功能。 對捲動的可用支援等級取決於應用程式使用的 ODBC 驅動程式、驅動程式的 ODBC API 符合性等級以及 ODBC 游標庫是否載入到記憶體中。 有關詳細資訊,請參閱[ODBC](../../data/odbc/odbc-basics.md)和[ODBC:ODBC 游標庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
> 您可以控制是否使用游標庫。 請參考*bUseCursorLib*與*dwOptions*參數到[CDatabase::開啟](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
> 與 MFC DAO 類不同,MFC ODBC 類不提供`Find`一組函數來定位滿足指定條件的下一個(或上一個)記錄。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[C記錄集::檢查羅塞特錯誤](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
