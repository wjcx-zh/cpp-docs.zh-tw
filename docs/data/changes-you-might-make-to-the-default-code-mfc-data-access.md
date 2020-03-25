---
title: 您可能對預設程式碼所做的變更 (MFC 資料存取)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 7ea616caf176cd1e9e2f26bee1339640067b4e3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213457"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>您可能對預設程式碼所做的變更 (MFC 資料存取)

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)會為您撰寫記錄集類別，以選取單一資料表中的所有記錄。 您經常會想要以下列一種或多種方式修改該行為：

- 設定資料錄集的篩選條件或排序順序。 請在建立記錄集物件之後，但是在呼叫其 `Open` 成員函式之前，于 `OnInitialUpdate` 中執行此動作。 如需詳細資訊，請參閱[記錄集：篩選記錄（odbc）](../data/odbc/recordset-filtering-records-odbc.md)和[記錄集：排序記錄（odbc）](../data/odbc/recordset-sorting-records-odbc.md)。

- 參數化資料錄集。 請在篩選之後指定實際的執行階段參數值。 如需詳細資訊，請參閱[記錄集：參數化記錄集（ODBC）](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- 將自訂的 SQL 字串傳遞至[Open](../mfc/reference/crecordset-class.md#open)成員函式。 如需使用這項技術可以完成之工作的討論，請參閱[SQL：自訂記錄集的 SQL 語句（ODBC）](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

## <a name="see-also"></a>另請參閱

[使用記錄視圖](../data/using-a-record-view-mfc-data-access.md)
