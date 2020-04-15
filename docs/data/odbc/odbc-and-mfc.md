---
title: ODBC 和 MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 38a625c73a17ecae4d8adc61e8c56bc4bdda67f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320078"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
> 要使用 MFC 資料庫類,必須為資料來源具有適當的 ODBC 驅動程式。 SQL 伺服器的最後一個微軟 ODBC 驅動程式是[SQL Server 的 Microsoft ODBC 驅動程式 13。](https://www.microsoft.com/download/details.aspx?id=50420) 大多數資料庫供應商為 Windows 提供 ODBC 驅動程式。

本主題介紹 Microsoft 基礎類 (MFC) 庫基於 ODBC 的資料庫類的主要概念,並概述了這些類如何協同工作。 有關 ODBC 和 MFC 的詳細資訊,請參閱以下主題:

- [連接到資料來源](connecting-to-a-data-source.md)

- [選取和操作資料錄](selecting-and-manipulating-records.md)

- [顯示表單資料](displaying-and-manipulating-data-in-a-form.md)

- [使用文件與檢視](working-with-documents-and-views.md)

- [存取 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [深入了解 MFC ODBC 類別](further-reading-about-the-mfc-odbc-classes.md)

基於 ODBC 的 MFC 資料庫類旨在提供對可用 ODBC 驅動程式的任何資料庫的訪問。 由於類使用 ODBC,您的應用程式可以造訪許多不同的資料格式和不同的本地/遠端配置的資料。 您不必編寫特殊情況代碼來處理不同的資料庫管理系統 (DBMS)。 只要使用者具有他們想要訪問的數據的適當 ODBC 驅動程式,他們就可以使用您的程式操作存儲在其中的表中的數據。

## <a name="see-also"></a>另請參閱

[開放資料庫連線 (ODBC)](open-database-connectivity-odbc.md)
