---
title: 選取和操作資料錄
ms.date: 11/04/2016
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: fa8b63dab24c921804c474df73f6b6da192a4cd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329942"
---
# <a name="selecting-and-manipulating-records"></a>選取和操作資料錄

通常當您選取的記錄從資料來源，使用 SQL**選取**陳述式中，您取得結果集，也就是一組從資料表或查詢的記錄。 資料庫類別中，使用中，您可以使用資料錄集物件選取並存取該結果集。 這是您從類別衍生應用程式特定類別的物件[CRecordset](../../mfc/reference/crecordset-class.md)。 當您定義的資料錄集類別時，您可以指定其關聯的資料來源、 要使用時，資料表和資料表的資料行。 MFC 應用程式精靈或**加入類別**(如中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 與特定資料來源的連接，建立一個類別。 精靈寫入[GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)類別成員函式`CRecordset`来傳回的資料表名稱。 如需使用精靈來建立資料錄集類別的詳細資訊，請參閱[MFC 應用程式精靈、 資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)並[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。

使用[CRecordset](../../mfc/reference/crecordset-class.md)物件在執行階段，您可以：

- 檢查目前的資料錄的資料欄位。

- 篩選或排序資料錄集。

- 自訂預設 SQL**選取**陳述式。

- 捲動以查看所選的記錄。

- 新增、 更新或刪除記錄 （如果在資料來源和資料錄集是可更新）。

- 測試是否資料錄集可讓重新查詢並重新整理資料錄集的內容。

當您完成使用資料錄集物件時，您會關閉，然後終結它。 如需有關資料錄集的詳細資訊，請參閱 <<c0> [ 資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)