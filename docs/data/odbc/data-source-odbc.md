---
title: "資料來源 (ODBC) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e4276c997069e69d6e84dd4426af4b82c2a839b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-odbc"></a>資料來源 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 在資料庫詞彙中，資料來源是一組特定的資料，以存取該資料，以及可以使用資料來源名稱所描述的資料來源中的位置所需的資訊。 若要使用類別[CDatabase](../../mfc/reference/cdatabase-class.md)，資料來源必須是透過開放式資料庫連接 (ODBC) 系統管理員，您已設定的其中一個。 資料來源的範例包括執行 Microsoft SQL Server 上透過網路或 Microsoft Access 檔案的本機目錄中的遠端資料庫。 從您的應用程式，您可以存取具有 ODBC 驅動程式的任何資料來源。  
  
 您可以有作用中應用程式一次一個或多個資料來源，分別由`CDatabase`物件。 您也可以有多個同時連線到任何資料來源。 您可以連接到遠端和本機資料來源，視您已安裝的驅動程式和功能的 ODBC 驅動程式而定。 如需有關資料來源和 ODBC 管理員的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)和[ODBC 管理員](../../data/odbc/odbc-administrator.md)。  
  
 下列主題說明更多有關資料來源：  
  
-   [資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [資料來源：決定資料來源的結構描述 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)