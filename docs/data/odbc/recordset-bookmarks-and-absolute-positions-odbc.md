---
title: 資料錄集：書籤和絕對位置 (ODBC)
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: c4a223f01b25b4c321ccfb4f4c03c3c5241381ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395608"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>資料錄集：書籤和絕對位置 (ODBC)

本主題適用於 MFC ODBC 類別。

瀏覽時的資料錄集，您通常需要一種將傳回給特定的記錄。 資料錄的書籤和絕對位置提供兩個這類方法。

本主題說明：

- [如何使用書籤](#_core_bookmarks_in_mfc_odbc)。

- [如何設定使用絕對位置的目前記錄](#_core_absolute_positions_in_mfc_odbc)。

##  <a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC 中的書籤

書籤可唯一識別一筆記錄。 當您瀏覽資料錄集時，您不能永遠依賴一筆記錄的絕對位置因為可以從資料錄集刪除資料錄。 可靠的方式，來追蹤記錄的位置是使用它的書籤。 類別`CRecordset`提供成員函式：

- 取得目前資料錄，書籤，因此您可以將它儲存在變數 ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark))。

- 藉由指定您稍早在變數中儲存的書籤，快速地移動到指定的記錄 ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark))。

下列範例說明如何使用這些成員函式標示目前的記錄，並於稍後返回：

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

您不需要解壓縮基礎資料類型從[CDBVariant 類別](../../mfc/reference/cdbvariant-class.md)物件。 指派的值與`GetBookmark`，然後返回具有該書籤`SetBookmark`。

> [!NOTE]
>  根據您的 ODBC 驅動程式和資料錄集類型，可能不支援書籤。 您可以輕鬆判斷是否支援書籤，以藉由呼叫[CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)。 此外，如果支援書籤，您必須明確選擇實作它們藉由指定`CRecordset::useBookmarks`選項[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)成員函式。 您也應該檢查書籤之後特定資料錄集作業的持續的性。 例如，如果您`Requery`資料錄集，書籤可能不再有效。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要檢查您是否能安全地呼叫`SetBookmark`。

##  <a name="_core_absolute_positions_in_mfc_odbc"></a> MFC ODBC 中的絕對位置

書籤，除了類別`CRecordset`可讓您指定的序數位置來設定目前的記錄。 這稱為絕對位置。

> [!NOTE]
>  絕對位置不適用於順向資料錄集。 如需有關順向資料錄集的詳細資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。

若要移動使用絕對位置的目前記錄指標，呼叫[CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 當您將值傳遞到`SetAbsolutePosition`、 對應到序數位置就會成為目前的記錄的記錄。

> [!NOTE]
>  一筆記錄的絕對位置是可能不可靠。 如果使用者刪除記錄集的資料錄，任何後續的記錄變更的序數位置。 書籤是移動目前的資料錄的建議的方法。 如需詳細資訊，請參閱 < [MFC ODBC 中的書籤](#_core_bookmarks_in_mfc_odbc)。

如需有關資料錄集瀏覽的詳細資訊，請參閱[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)