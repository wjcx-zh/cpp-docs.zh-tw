---
title: 資料來源 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39c017113d6f3da0041b5e460666af955c27b0fa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066145"
---
# <a name="data-source-odbc"></a>資料來源 (ODBC)

本主題適用於 MFC ODBC 類別。

在資料庫詞彙中，資料來源是一組特定的資料，來存取該資料，以及資料來源，可以使用資料來源名稱所描述的位置所需的資訊。 若要使用類別[CDatabase](../../mfc/reference/cdatabase-class.md)，資料來源必須是透過開放式資料庫連接 (ODBC) 系統管理員，您已設定的其中一個。 資料來源的範例包括跨網路或 Microsoft Access 檔案的本機目錄中執行 Microsoft SQL Server 上的遠端資料庫。 從您的應用程式中，您可以存取您的 ODBC 驅動程式的任何資料來源。

您可以在您的應用程式一次使用一或多個資料來源，每一個由`CDatabase`物件。 您也可以讓多個同時連線到任何資料來源。 您可以連線到遠端和本機資料來源，視您已安裝的驅動程式和功能的 ODBC 驅動程式而定。 如需有關資料來源和 ODBC 管理員的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)並[ODBC 管理員](../../data/odbc/odbc-administrator.md)。

下列主題詳細說明資料來源：

- [資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [資料來源：決定資料來源的結構描述 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)