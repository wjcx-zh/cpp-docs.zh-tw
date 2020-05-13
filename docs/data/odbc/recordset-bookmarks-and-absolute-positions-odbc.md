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
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367060"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>資料錄集：書籤和絕對位置 (ODBC)

本主題適用於 MFC ODBC 類別。

在記錄集中導航時,通常需要返回特定記錄的方法。 記錄的書籤和絕對位置提供了兩種這樣的方法。

本主題將說明：

- [如何使用書籤](#_core_bookmarks_in_mfc_odbc)。

- [如何使用絕對位置設定目前的紀錄](#_core_absolute_positions_in_mfc_odbc)。

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>MFC ODBC 中的書籤

書籤唯一標識記錄。 當您瀏覽記錄集時,不能始終依賴於記錄的絕對位置,因為可以從記錄集中刪除記錄。 跟蹤記錄位置的可靠方法是使用其書籤。 類別`CRecordset`為:

- 獲取當前記錄的書籤,以便將其保存在變數中[(GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark))。

- 通過指定其書籤快速移動到給定記錄,該書籤在變數[(SetBookmark)](../../mfc/reference/crecordset-class.md#setbookmark)中保存較早。

下面的範例展示如何使用這些成員函數來標記目前記錄,然後傳回到它:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

不需要從[CDBVariant 類](../../mfc/reference/cdbvariant-class.md)物件中提取基礎數據類型。 使用分配值`GetBookmark`,並返回`SetBookmark`該 書籤。

> [!NOTE]
> 根據您的 ODBC 驅動程式和記錄集類型,可能不支援書籤。 以呼叫[CRecordset::canBookmark,](../../mfc/reference/crecordset-class.md#canbookmark)您可以輕鬆地確定書籤是否受支援。 此外,如果支援書籤,則必須通過在[CRecordset::打開](../../mfc/reference/crecordset-class.md#open)成員函數`CRecordset::useBookmarks`中 指定選項來顯式選擇實現它們。 在某些記錄集操作后,還應檢查書籤的持久性。 例如,如果`Requery`記錄集,書籤可能不再有效。 呼叫[CDatabase:取得書籤持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence),以檢查是否可以安全地`SetBookmark`呼叫 。

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>MFC ODBC 中的絕對位置

除了書籤之外,類`CRecordset`還允許您通過指定一個位形位置來設置當前記錄。 這稱為絕對定位。

> [!NOTE]
> 絕對定位在僅轉發記錄集上不可用。 有關僅轉發記錄集的詳細資訊,請參閱[記錄集 (ODBC)。](../../data/odbc/recordset-odbc.md)

要使用絕對位置移動目前紀錄指標,請呼叫[CRecordset::set 絕對位置](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 將值傳遞給`SetAbsolutePosition`時,對應於該任位的記錄將成為當前記錄。

> [!NOTE]
> 記錄的絕對位置可能不可靠。 如果使用者從記錄集中刪除記錄,則任何後續記錄的任地位置將更改。 書籤是移動當前記錄的推薦方法。 有關詳細資訊,請參閱[MFC ODBC 中的書籤](#_core_bookmarks_in_mfc_odbc)。

有關記錄集導航的詳細資訊,請參閱[記錄集:滾動 (ODBC)。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)
