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
ms.openlocfilehash: e1cb5df4a93fc642ccf4d500a5eb93690b0b3d75
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403814"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接呼叫 ODBC API 函式

資料庫類別提供比 ODBC 更簡單的[資料來源](../../data/odbc/data-source-odbc.md)介面。 因此，類別不會封裝所有的 ODBC API。 對於超出類別能力的任何功能，您必須直接呼叫 ODBC API 函式。 例如，您必須直接呼叫 ODBC 目錄函式（ `::SQLColumns` 、 `::SQLProcedures` 、 `::SQLTables` 及其他函數）。

> [!NOTE]
> 您可以透過 MFC ODBC 類別存取 ODBC 資料來源，如本主題中所述，或透過 MFC 資料存取物件（DAO）類別。

若要直接呼叫 ODBC API 函式，當您在沒有架構的情況下進行呼叫時，您必須採取相同的步驟。 其步驟如下：

- 為呼叫傳回的任何結果配置儲存體。

- 根據函式 `HDBC` 的參數簽章，傳遞 ODBC 或 `HSTMT` 控制碼。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏來取出 ODBC 控制碼。

   成員變數 `CDatabase::m_hdbc` 和 `CRecordset::m_hstmt` 可供使用，因此您不需要自行配置和初始化這些變數。

- 可能呼叫其他 ODBC 函式來準備或跟進主要呼叫。

- 完成時解除配置儲存體。

如需這些步驟的詳細資訊，請參閱 ODBC 程式設計[人員參考](/sql/odbc/reference/odbc-programmer-s-reference)。

除了這些步驟之外，您還需要採取額外的步驟來檢查函式傳回值，確保您的程式不會等待非同步呼叫完成，依此類推。 您可以使用 AFX_SQL_ASYNC 和 AFX_SQL_SYNC 宏來簡化這些最後的步驟。 如需詳細資訊，請參閱[MFC 宏和 globals](../../mfc/reference/mfc-macros-and-globals.md)。

## <a name="see-also"></a>另請參閱

[ODBC 基本概念](../../data/odbc/odbc-basics.md)
