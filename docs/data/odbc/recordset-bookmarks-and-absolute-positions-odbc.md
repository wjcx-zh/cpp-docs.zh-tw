---
title: "資料錄集： 書籤和絕對位置 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SetAbsolutePosition
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b206e5d09d86613af0585df7510b0f88397984a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>資料錄集：書籤和絕對位置 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 當巡覽資料錄集，您通常需要傳回至特定資料錄的方式。 資料錄的書籤和絕對位置提供兩個這類方法。  
  
 本主題說明：  
  
-   [如何使用書籤](#_core_bookmarks_in_mfc_odbc)。  
  
-   [如何設定為使用絕對位置的目前記錄](#_core_absolute_positions_in_mfc_odbc)。  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a>MFC ODBC 中的書籤  
 書籤記錄的唯一識別。 當您巡覽資料錄集時，您不能永遠依賴一筆記錄的絕對位置因為從資料錄集，可以刪除記錄。 可靠的方式來追蹤記錄的位置是使用它的書籤。 類別`CRecordset`提供成員函式：  
  
-   取得目前的記錄上的書籤，以便在變數中儲存 ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark))。  
  
-   藉由指定您稍早在變數中儲存的書籤，快速移動到指定的資料錄 ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark))。  
  
 下列範例將說明如何使用這些成員函式標示為目前的記錄，並於稍後返回：  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 您不需要擷取基礎資料類型從[CDBVariant 類別](../../mfc/reference/cdbvariant-class.md)物件。 指派的值與`GetBookmark`並返回與該書籤`SetBookmark`。  
  
> [!NOTE]
>  根據您的 ODBC 驅動程式和資料錄集類型，可能不支援書籤。 您可以輕易地判斷是否支援書籤，以藉由呼叫[CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark)。 此外，如果支援書籤，您必須明確地選擇實作它們藉由指定**CRecordset::useBookmarks**選項[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)成員函式。 您也應該檢查特定資料錄集作業之後的書籤的持續性。 例如，如果您**Requery**資料錄集，書籤可能不再有效。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)來檢查您是否能安全地呼叫`SetBookmark`。  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a>MFC ODBC 中的絕對位置  
 書籤，除了類別`CRecordset`可讓您藉由指定的序數位置設定為目前的記錄。 這稱為絕對位置。  
  
> [!NOTE]
>  絕對位置並不適用於使用順向資料錄集。 如需順向資料錄集的詳細資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。  
  
 若要移動使用絕對位置目前的記錄指標，呼叫[CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition)。 當您將值傳遞至`SetAbsolutePosition`、 對應到序數位置就會成為目前的記錄的記錄。  
  
> [!NOTE]
>  記錄的絕對位置是可能不可靠。 如果使用者刪除資料錄集的資料錄，任何後續的記錄變更的序數位置。 書籤是建議的方法來移動目前的記錄。 如需詳細資訊，請參閱[MFC ODBC 中的書籤](#_core_bookmarks_in_mfc_odbc)。  
  
 如需有關資料錄集瀏覽的詳細資訊，請參閱[資料錄集： 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)