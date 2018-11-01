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
ms.openlocfilehash: 7c7540528bed2499ed9dfb09ed39658914c81e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560624"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
>  若要使用 MFC 資料庫類別，您必須具有適當的 ODBC 驅動程式資料來源。 最新 Microsoft ODBC driver for SQL Server 已[Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)。 大部分的資料庫廠商都提供 Windows ODBC 驅動程式。

本主題介紹 Microsoft Foundation Classes (MFC) 程式庫的 ODBC 為基礎的資料庫類別的主要概念，並提供類別如何一起運作的概觀。 如需有關 ODBC 和 MFC 的詳細資訊，請參閱下列主題：

- [連接至資料來源](connecting-to-a-data-source.md)

- [選取和操作資料錄](selecting-and-manipulating-records.md)

- [顯示和操作表單中的資料](displaying-and-manipulating-data-in-a-form.md)

- [使用文件和檢視](working-with-documents-and-views.md)

- [存取 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [深入了解 MFC ODBC 類別](further-reading-about-the-mfc-odbc-classes.md)

ODBC 為基礎之 MFC 資料庫類別專為提供的 ODBC 驅動程式還是可以使用任何資料庫的存取權。 類別會使用 ODBC，因為您的應用程式可以存取許多不同的資料格式和不同的本機/遠端組態中的資料。 您不必撰寫特殊的程式碼來處理不同的資料庫管理系統 (Dbms)。 只要您的使用者有適當的 ODBC 驅動程式，他們想要存取的資料，他們可以使用您的程式來管理儲存在其中的資料表中的資料。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](open-database-connectivity-odbc.md)