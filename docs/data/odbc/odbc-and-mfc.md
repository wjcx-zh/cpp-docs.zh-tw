---
title: ODBC 和 MFC |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9ab063bb44d9390442cbf5ad23a60f44f60b3c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089193"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC
> [!NOTE]
>  若要使用 MFC 資料庫類別，您必須適當的 ODBC 驅動程式的資料來源。 最新的 Microsoft ODBC driver for SQL Server 是[Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。 大部分的資料庫供應商提供 Windows ODBC 驅動程式。 
  
 本主題介紹 Microsoft Foundation Classes (MFC) 程式庫的 ODBC 資料庫類別的主要概念，並提供類別如何一起運作的概觀。 如需有關 ODBC 和 MFC 的詳細資訊，請參閱下列主題：  
  
-   [連接至資料來源](connecting-to-a-data-source.md)  
  
-   [選取和操作資料錄](selecting-and-manipulating-records.md)  
  
-   [顯示和操作表單中的資料](displaying-and-manipulating-data-in-a-form.md)  
  
-   [使用文件和檢視](working-with-documents-and-views.md)  
  
-   [存取 ODBC 和 SQL](access-to-odbc-and-sql.md)  
  
-   [深入了解 MFC ODBC 類別](further-reading-about-the-mfc-odbc-classes.md)  
  
 ODBC 為基礎之 MFC 資料庫類別被設計來提供的 ODBC 驅動程式有可用的任何資料庫的存取權。 類別會使用 ODBC，因為您的應用程式可以存取許多不同的資料格式和不同的本機/遠端組態中的資料。 您不必撰寫特殊的程式碼來處理不同的資料庫管理系統 (Dbms)。 只要您的使用者有適當的 ODBC 驅動程式要存取的資料，它們可以使用您的程式來管理儲存於該處的資料表中的資料。  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](open-database-connectivity-odbc.md)