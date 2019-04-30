---
title: 資料錄集：加入大量 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: a2c3eab8bb4c0e8db76fceb5a2dafd16a4a07079
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395660"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>資料錄集：加入大量 (ODBC)

本主題適用於 MFC ODBC 類別。

MFC [CRecordset](../../mfc/reference/crecordset-class.md)類別有一個新的最佳化，可改善效率，當您要大量新增新記錄資料表。

> [!NOTE]
> 本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

新的選項，如*dwOptions*參數來[crecordset:: Open](../../mfc/reference/crecordset-class.md#open)成員函式， `optimizeBulkAdd`，可以改善效能，當您要連續新增多筆記錄，而不需要呼叫`Requery`或`Close`。 只有在有錯誤之前，先的欄位`Update`呼叫會標示為已變更後續`AddNew` / `Update`呼叫。

如果您使用資料庫類別以善用`::SQLSetPos`ODBC API 函式加入、 編輯和刪除記錄，此最佳化是不必要。

如果載入 ODBC 資料指標程式庫或 ODBC 驅動程式不支援加入、 編輯和刪除透過`::SQLSetPos`，此最佳化會改善大量加入的效能。 若要開啟此最佳化，請設定*dwOptions*中的參數`Open`呼叫下列資料錄集：

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：新增、更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)