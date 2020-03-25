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
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212767"
---
# <a name="recordset-scrolling-odbc"></a>資料錄集：捲動 (ODBC)

本主題適用於 MFC ODBC 類別。

開啟記錄集之後，您必須存取記錄以顯示值、計算、產生報告等等。 「滾動」可讓您從記錄移至記錄集內的記錄。

本主題將說明：

- [如何在記錄集中從一筆記錄滾動到另](#_core_scrolling_from_one_record_to_another)一個。

- [在何種情況下，「滾動」是和不受支援](#_core_when_scrolling_is_supported)。

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>從一筆記錄滾動到另一筆

類別 `CRecordset` 會提供 `Move` 成員函式，以便在記錄集內進行滾動。 這些函數會依資料列集移動目前的記錄。 如果您已執行大量資料列提取，`Move` 作業會根據資料列集的大小將記錄集重新置放。 如果您尚未執行大量資料列提取，則每次呼叫 `Move` 函式會將記錄集重新調整為一筆記錄。 如需大量資料列提取的詳細資訊，請參閱[記錄集：大量提取記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  在記錄集之間移動時，可能不會略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成員函式。

除了 `Move` 函式以外，`CRecordset` 提供成員函式，以檢查您是否已在記錄集開頭或之前結束。

若要判斷您的記錄集是否可以滾動，請呼叫 `CanScroll` 成員函式。

#### <a name="to-scroll"></a>若要滾動

1. 轉送一筆記錄或一個資料列集：呼叫[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成員函式。

1. 後一筆記錄或一個資料列集：呼叫[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成員函式。

1. 至記錄集內的第一筆記錄：呼叫[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成員函式。

1. 至記錄集的最後一筆記錄或最後一個資料列集：呼叫[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成員函式。

1. 相對於目前位置的*N*筆記錄：呼叫[Move](../../mfc/reference/crecordset-class.md#move)成員函式。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>若要測試記錄集的結尾或開頭

1. 您是否已滾動過最後一筆記錄？ 呼叫[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成員函式。

1. 您是否要在第一筆記錄（向後移動）之前向前滾動？ 呼叫[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成員函式。

下列程式碼範例會使用 `IsBOF` 和 `IsEOF`，在以任一方向進行滾動時，偵測記錄集的限制。

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

如果記錄集位於最後一筆記錄之後，`IsEOF` 會傳回非零值。 如果記錄集位於第一筆記錄（所有記錄之前）的前面，`IsBOF` 會傳回非零值。 不論是哪一種情況，目前都不會有可操作的記錄。 如果您在 `IsBOF` 已為 TRUE 時呼叫 `MovePrev`，或在 `IsEOF` 已經為 TRUE 時呼叫 `MoveNext`，則架構會擲回 `CDBException`。 您也可以使用 `IsBOF` 和 `IsEOF` 來檢查是否有空的記錄集。

如需記錄集導覽的詳細資訊，請參閱[記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>支援滾動時

如同原本所設計，SQL 只提供向前滾動，但是 ODBC 會擴充滾動功能。 可用的滾動支援層級取決於您的應用程式所使用的 ODBC 驅動程式、驅動程式的 ODBC API 一致性層級，以及 ODBC 資料指標程式庫是否載入記憶體中。 如需詳細資訊，請參閱[odbc](../../data/odbc/odbc-basics.md)和[odbc： odbc 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
>  您可以控制是否使用資料指標程式庫。 請參閱*bUseCursorLib*和*DwOptions*參數到[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
>  不同于 MFC DAO 類別，MFC ODBC 類別不會提供一組 `Find` 函數來尋找符合指定準則的下一個（或上一個）記錄。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset：： CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset：： CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
