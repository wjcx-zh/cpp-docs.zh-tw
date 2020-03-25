---
title: 資料來源 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: ed9eeb8f5ef0d53846761062cf2c6575d2eaf9e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213293"
---
# <a name="data-source-odbc"></a>資料來源 (ODBC)

本主題適用於 MFC ODBC 類別。

在資料庫詞彙中，資料來源是一組特定的資料、存取該資料所需的資訊，以及資料來源的位置，可以使用資料來源名稱加以描述。 若要使用類別[CDatabase](../../mfc/reference/cdatabase-class.md)，資料來源必須是您透過開放式資料庫連接（ODBC）系統管理員所設定的。 資料來源的範例包括在本機目錄中跨網路或 Microsoft Access 檔案執行的遠端資料庫 Microsoft SQL Server。 從您的應用程式，您可以存取具有 ODBC 驅動程式的任何資料來源。

您的應用程式一次可以有一個或多個作用中的資料來源，每個都由 `CDatabase` 物件表示。 您也可以有多個同時連接到任何資料來源。 根據您已安裝的驅動程式和 ODBC 驅動程式的功能而定，您可以連接到遠端和本機資料來源。 如需有關資料來源和 ODBC 管理員的詳細資訊，請參閱[odbc](../../data/odbc/odbc-basics.md)和[odbc 系統管理員](../../data/odbc/odbc-administrator.md)。

下列主題將詳細說明資料來源：

- [資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [資料來源：決定資料來源的結構描述 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
