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
ms.openlocfilehash: e41b526b86922bafd1d923fa5848a5ef8ed4825e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579584"
---
# <a name="recordset-scrolling-odbc"></a>資料錄集：捲動 (ODBC)

本主題適用於 MFC ODBC 類別。

開啟資料錄集之後，您需要存取記錄，來顯示值，執行計算、 產生報告，等等。 捲動可讓您將記錄間移動資料錄集內。

本主題說明：

- [如何從一個資料錄捲動到另一個資料錄集中](#_core_scrolling_from_one_record_to_another)。

- [在捲動的情況下是什麼，不支援](#_core_when_scrolling_is_supported)。

##  <a name="_core_scrolling_from_one_record_to_another"></a> 從一個資料錄捲動到另一個

類別`CRecordset`提供`Move`捲動資料錄集內的成員函式。 這些函式會移動目前的資料錄的資料列集。 如果您已實作大量資料列擷取`Move`作業重新置放的資料列集大小的資料錄集。 如果您未實作大量資料列擷取，呼叫`Move`函式重新定位資料錄集的一筆記錄的每一次。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!NOTE]
>  當您移動的資料錄集，可能不會略過已刪除的記錄。 如需詳細資訊，請參閱 < [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted)成員函式。

除了`Move`函式，`CRecordset`提供成員函式以檢查是否已捲動超出結尾或您的資料錄集的開頭之前。

若要判斷是否可捲動資料錄集，請呼叫`CanScroll`成員函式。

#### <a name="to-scroll"></a>若要捲動

1. 轉送一筆記錄或一個資料列集： 呼叫[MoveNext](../../mfc/reference/crecordset-class.md#movenext)成員函式。

1. 為了與舊版的一筆記錄或一個資料列集： 呼叫[MovePrev](../../mfc/reference/crecordset-class.md#moveprev)成員函式。

1. 第一個記錄中的資料錄集： 呼叫[MoveFirst](../../mfc/reference/crecordset-class.md#movefirst)成員函式。

1. 資料錄集的最後一筆記錄，或最後一個資料列集： 呼叫[MoveLast](../../mfc/reference/crecordset-class.md#movelast)成員函式。

1. *N*相對於目前位置的記錄： 呼叫[移動](../../mfc/reference/crecordset-class.md#move)成員函式。

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>若要測試結尾或開頭的資料錄集

1. 您有捲動過去的最後一筆記錄？ 呼叫[IsEOF](../../mfc/reference/crecordset-class.md#iseof)成員函式。

1. 您有捲動預先 （向後移動） 的第一個記錄？ 呼叫[IsBOF](../../mfc/reference/crecordset-class.md#isbof)成員函式。

下列程式碼範例會使用`IsBOF`和`IsEOF`任一方向捲動時偵測資料錄集的限制。

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

`IsEOF` 如果資料錄集位於過去的最後一筆記錄，則傳回非零值。 `IsBOF` 如果資料錄集位於第一筆記錄 （在之前的所有記錄） 之前，會傳回非零值。 在任一情況下，沒有要處理的目前記錄。 如果您呼叫`MovePrev`時`IsBOF`已經 TRUE，或呼叫`MoveNext`當`IsEOF`已經是 TRUE，架構就會擲回`CDBException`。 您也可以使用`IsBOF`和`IsEOF`檢查空的資料錄集。

如需有關資料錄集瀏覽的詳細資訊，請參閱[資料錄集： 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="_core_when_scrolling_is_supported"></a> 當支援捲動

為原始設計，SQL 提供只會順向捲動，但 ODBC 擴充了捲動功能。 可捲動的支援層級取決於您的應用程式的運作方式與您的驅動程式的 ODBC API 一致性層級，ODBC 驅動程式和 ODBC 資料指標程式庫會載入至記憶體。 如需詳細資訊，請參閱 < [ODBC](../../data/odbc/odbc-basics.md)並[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!TIP]
>  您可以控制是否要使用資料指標程式庫。 請參閱*bUseCursorLib*並*dwOptions*參數[Openex](../../mfc/reference/cdatabase-class.md#open)。

> [!NOTE]
>  不同於 MFC DAO 類別中，MFC ODBC 類別不會提供一組`Find`尋找下一個 （或先前） 記錄符合指定準則的函式。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)