---
title: ODBC：直接呼叫 ODBC API 函式
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368660"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接呼叫 ODBC API 函式

與 ODBC 相比,資料庫類為[數據源](../../data/odbc/data-source-odbc.md)提供了更簡單的介面。 因此,類不封裝所有ODBC API。 對於任何超出類功能的功能,必須直接調用 ODBC API 函數。 例如,必須直接調用ODBC目錄函數(、、、`::SQLColumns``::SQLProcedures``::SQLTables`等函數)。

> [!NOTE]
> ODBC 資料來源可透過 MFC ODBC 類別(如本主題所述)或透過 MFC 資料存取物件 (DAO) 類別存取。

要直接調用 ODBC API 函數,必須執行與在沒有框架的情況下進行調用時相同的步驟。 它們的步驟是:

- 為呼叫返回的任何結果分配存儲。

- 傳遞 ODBC`HDBC``HSTMT`或句柄,具體取決於函數的參數簽名。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏檢索 ODBC 句柄。

   成員變數`CDatabase::m_hdbc`,`CRecordset::m_hstmt`並且可用,因此您無需自己分配和初始化這些變數。

- 可能調用其他 ODBC 功能來準備或跟進主呼叫。

- 完成後取消分配存儲。

有關這些步驟的詳細資訊,請參閱 MSDN 文件中[的開放資料庫連接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK。

除了這些步驟之外,還需要執行額外的步驟來檢查函數返回值,確保程式不等待非同步調用完成,等等。 可以使用AFX_SQL_ASYNC和AFX_SQL_SYNC宏來簡化最後的步驟。 有關詳細資訊,請參閱*MFC 參考*中的[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基礎知識](../../data/odbc/odbc-basics.md)
