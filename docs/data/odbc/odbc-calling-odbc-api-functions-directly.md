---
title: ODBC:直接呼叫 ODBC API 函式
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
ms.openlocfilehash: 435df301ad54c7ff5b2f0e46190e3dad7e9c07f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395803"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC:直接呼叫 ODBC API 函式

資料庫類別提供更簡單的介面，以[資料來源](../../data/odbc/data-source-odbc.md)比 ODBC。 如此一來，類別不會封裝所有的 ODBC API。 任何超出之類別的執行能力的功能，您必須直接呼叫 ODBC API 函式。 例如，您必須呼叫 ODBC 目錄函數 (`::SQLColumns`， `::SQLProcedures`， `::SQLTables`，和其他人) 直接。

> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。

直接呼叫 ODBC API 函式，您必須採取相同的步驟，您可以採取若您正在進行的呼叫不含在 framework。 其步驟如下：

- 配置的儲存體的呼叫會傳回任何結果。

- 傳遞 ODBC`HDBC`或`HSTMT`處理，根據函式的參數簽章。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)巨集來擷取 ODBC 控制代碼。

   成員變數`CDatabase::m_hdbc`和`CRecordset::m_hstmt`便可使用，因此您不需要配置並初始化這些自己。

- 可能是呼叫其他的 ODBC 函式，來準備或待處理的主要呼叫。

- 當您完成時，取消配置儲存區。

如需有關這些步驟的詳細資訊，請參閱 <<c0> [ 開放式資料庫連接 (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) MSDN 文件中的 SDK。

除了這些步驟中，您需要採取額外步驟以檢查函式傳回值，請確定您的程式不等候非同步呼叫完成，然後依此類推。 您可以使用 AFX_SQL_ASYNC 和 AFX_SQL_SYNC 巨集，以簡化最後一個步驟執行。 如需詳細資訊，請參閱 <<c0> [ 巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 參考 》*。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)
