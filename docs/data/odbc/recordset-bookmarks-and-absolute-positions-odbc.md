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
ms.openlocfilehash: 9a25c0fe4c1f08d376824fbc02211d22c7c14435
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212962"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>資料錄集：書籤和絕對位置 (ODBC)

本主題適用於 MFC ODBC 類別。

流覽記錄集時，您通常需要一種方法來返回特定記錄。 記錄的書簽和絕對位置會提供兩種這類方法。

本主題將說明：

- [如何使用書簽](#_core_bookmarks_in_mfc_odbc)。

- [如何使用絕對位置來設定目前的記錄](#_core_absolute_positions_in_mfc_odbc)。

##  <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>MFC ODBC 中的書簽

書簽可唯一識別記錄。 當您流覽記錄集時，您不能一律依賴記錄的絕對位置，因為記錄可以從記錄集刪除。 追蹤記錄位置的可靠方法是使用其書簽。 類別 `CRecordset` 提供的成員函式：

- 取得目前記錄的書簽，讓您可以將它儲存在變數（[GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)）中。

- 藉由指定書簽（您稍早在變數（[SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)）中儲存）來快速移動至指定的記錄。

下列範例說明如何使用這些成員函式來標記目前的記錄，並于稍後返回它：

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

您不需要從[CDBVariant 類別](../../mfc/reference/cdbvariant-class.md)物件中解壓縮基礎資料類型。 使用 `GetBookmark` 指派值，並使用 `SetBookmark`返回該書簽。

> [!NOTE]
>  根據您的 ODBC 驅動程式和記錄集類型而定，可能不支援書簽。 您可以藉由呼叫[CRecordset：： CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)，輕鬆地判斷是否支援書簽。 此外，如果支援書簽，您必須在[CRecordset：： Open](../../mfc/reference/crecordset-class.md#open)成員函式中指定 `CRecordset::useBookmarks` 選項，以明確地選擇要執行。 您也應該在特定記錄集作業之後檢查書簽的持續性。 例如，如果您 `Requery` 記錄集，書簽可能不再有效。 呼叫[CDatabase：： GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ，以檢查您是否可以安全地呼叫 `SetBookmark`。

##  <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>MFC ODBC 中的絕對位置

除了書簽以外，類別 `CRecordset` 可讓您藉由指定序數位置來設定目前的記錄。 這稱為絕對位置。

> [!NOTE]
>  在順向記錄集上無法使用絕對位置。 如需順向記錄集的詳細資訊，請參閱[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)。

若要使用絕對位置移動目前的記錄指標，請呼叫[CRecordset：： SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 當您將值傳遞至 `SetAbsolutePosition`時，對應到該序數位置的記錄會變成目前的記錄。

> [!NOTE]
>  記錄的絕對位置可能不可靠。 如果使用者刪除記錄集的記錄，任何後續記錄的序數位置就會變更。 書簽是移動目前記錄的建議方法。 如需詳細資訊，請參閱[MFC ODBC 中的書簽](#_core_bookmarks_in_mfc_odbc)。

如需記錄集導覽的詳細資訊，請參閱[記錄集：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)
