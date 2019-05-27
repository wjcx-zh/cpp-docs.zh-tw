---
title: 選取和操作資料錄
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 745c0c35e42426242d92d720d5dcd3de631fb17b
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707796"
---
# <a name="selecting-and-manipulating-records"></a>選取和操作資料錄

> [!NOTE] 
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

通常當您使用 SQL **SELECT** 陳述式從資料來源選取記錄時，會取得結果集，這是來自某個資料表或查詢的一組記錄。 使用資料庫類別時，您會使用資料錄集物件來選取和存取結果集。 這是您從 [CRecordset](../../mfc/reference/crecordset-class.md) 類別衍生之應用程式特定類別的物件。 當您定義資料錄集類別時，會指定要與其關聯的資料來源、要使用的資料表，以及該資料表的資料行。 「MFC 應用程式精靈」或 [新增類別] (如[新增 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述) 會建立一個具有特定資料來源連線的類別。 精靈會撰寫 `CRecordset` 類別的 [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) 成員函式來傳回資料表名稱。

藉由在執行階段使用 [CRecordset](../../mfc/reference/crecordset-class.md) 物件，您可以：

- 檢查目前記錄的資料欄位。

- 篩選或排序資料錄集。

- 自訂預設的 SQL **SELECT** 陳述式。

- 捲動瀏覽選取的記錄。

- 新增、更新或刪除記錄 (如果資料來源和資料錄集都可更新)。

- 測試資料錄集是否允許重新查詢和重新整理資料錄集的內容。

當您使用完資料錄集物件時，需關閉並終結它。 如需有關資料錄集的詳細資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)