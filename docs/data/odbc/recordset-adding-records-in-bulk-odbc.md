---
title: 資料錄集：加入大量資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213014"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>資料錄集：加入大量資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

MFC [CRecordset](../../mfc/reference/crecordset-class.md)類別具有新的優化功能，可在您將大量新記錄加入至資料表時提升效率。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果您使用大量資料列提取，請參閱[記錄集：提取大量的記錄（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

[CRecordset：： Open](../../mfc/reference/crecordset-class.md#open)成員函式的*dwOptions*參數的新選項，`optimizeBulkAdd`，會在您連續新增多個記錄而不呼叫 `Requery` 或 `Close`時，改善效能。 只有在第一個 `Update` 呼叫之前已變更的欄位，才會在後續的 `AddNew`/`Update` 呼叫中標示為「中途」。

如果您使用資料庫類別來利用 `::SQLSetPos` ODBC API 函式來新增、編輯和刪除記錄，則不需要進行這項優化。

如果已載入 ODBC 資料指標程式庫，或 ODBC 驅動程式不支援透過 `::SQLSetPos`來加入、編輯和刪除，則此優化應可改善大量加入效能。 若要開啟此優化，請在記錄集的 `Open` 呼叫中，將*dwOptions*參數設定為下列內容：

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
