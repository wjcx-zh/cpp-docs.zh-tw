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
ms.openlocfilehash: 94a3455324a52b789bcfcf192b698a3c42b37c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213156"
---
# <a name="odbc-and-mfc"></a>ODBC 和 MFC

> [!NOTE]
>  若要使用 MFC 資料庫類別，您必須擁有適用于資料來源的適當 ODBC 驅動程式。 最新 Microsoft ODBC driver for SQL Server 是[適用于 SQL Server 的 MICROSOFT Odbc driver 13](https://www.microsoft.com/download/details.aspx?id=50420)。 大部分的資料庫廠商都會提供適用于 Windows 的 ODBC 驅動程式。

本主題將介紹 Microsoft Foundation class （MFC）程式庫的 ODBC 資料庫類別的主要概念，並概述類別如何搭配使用。 如需 ODBC 和 MFC 的詳細資訊，請參閱下列主題：

- [連接至資料來源](connecting-to-a-data-source.md)

- [選取和操作資料錄](selecting-and-manipulating-records.md)

- [顯示和操作表單中的資料](displaying-and-manipulating-data-in-a-form.md)

- [使用檔和視圖](working-with-documents-and-views.md)

- [存取 ODBC 和 SQL](access-to-odbc-and-sql.md)

- [深入了解 MFC ODBC 類別](further-reading-about-the-mfc-odbc-classes.md)

以 ODBC 為基礎的 MFC 資料庫類別是設計用來提供 ODBC 驅動程式可供使用之任何資料庫的存取權。 因為類別使用 ODBC，所以您的應用程式可以存取許多不同資料格式的資料，以及不同的本機/遠端設定。 您不需要撰寫特殊案常式序代碼來處理不同的資料庫管理系統（Dbms）。 只要您的使用者具有適當的 ODBC 驅動程式來處理他們想要存取的資料，他們就可以使用您的程式來操作儲存在該處的資料表資料。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](open-database-connectivity-odbc.md)
