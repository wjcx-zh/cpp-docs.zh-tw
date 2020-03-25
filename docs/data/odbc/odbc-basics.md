---
title: ODBC 的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
ms.openlocfilehash: 042b1ce6d12e4f4a2be57c0e2e8e01d9750f5357
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213198"
---
# <a name="odbc-basics"></a>ODBC 的基本概念

本主題提供開放式資料庫連接（ODBC）的基本概念：

- [ODBC 如何與資料庫類別搭配運作](../../data/odbc/odbc-and-the-database-classes.md)

- [ODBC 驅動程式如何與動態集搭配使用](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [您需要隨著應用程式轉散發哪些 ODBC 元件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

您也會想要閱讀相關主題[odbc： odbc 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> 您可以透過 MFC ODBC 類別存取 ODBC 資料來源，如本主題中所述，或透過 MFC 資料存取物件（DAO）類別。

> [!NOTE]
> MFC ODBC 類別支援 Unicode 和多執行緒。 如需多執行緒支援的詳細資訊，請參閱[ODBC 類別和執行緒](../../data/odbc/odbc-classes-and-threads.md)

ODBC 是一個呼叫層級介面，可讓應用程式存取任何資料庫中有 ODBC 驅動程式的資料。 您可以使用 ODBC 來建立資料庫應用程式，以存取您的終端使用者具有 ODBC 驅動程式的任何資料庫。 ODBC 提供的 API 可讓您的應用程式獨立于源資料庫管理系統（DBMS）。

ODBC 是 Microsoft Windows 開放式服務架構（WOSA）的資料庫部分，它是一種介面，可讓 Windows 桌面應用程式連接到多個運算環境，而不需要為每個平臺重寫應用程式。

以下是 ODBC 的元件：

- ODBC API

   函式呼叫的程式庫、一組錯誤代碼，以及用來存取 Dbms 資料的標準[SQL](../../data/odbc/sql.md)語法。

- ODBC 驅動程式管理員

   代表應用程式載入 ODBC 資料庫驅動程式的動態連結程式庫（Odbc32.lib .dll）。 此 DLL 對您的應用程式而言是透明的。

- ODBC 資料庫驅動程式

   針對特定 Dbms 處理 ODBC 函數呼叫的一或多個 Dll。 如需提供的驅動程式清單，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

- [ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)

   位於 ODBC 驅動程式管理員和驅動程式之間的動態連結程式庫（Odbccr32），可處理資料的滾動。

- [ODBC 管理員](../../data/odbc/odbc-administrator.md)

   用來設定 DBMS 以當做應用程式資料來源使用的工具。

應用程式會透過專為 DBMS 撰寫的 ODBC 驅動程式，而不是直接使用 DBMS，來達到 Dbms 的獨立性。 驅動程式會將呼叫轉譯成 DBMS 可以使用的命令，簡化開發人員的工作，並讓它可用於各種不同的資料來源。

資料庫類別支援您有 ODBC 驅動程式的任何資料來源。 例如，這可能包含關係資料庫、索引循序存取方法（ISAM）資料庫、Microsoft Excel 試算表或文字檔。 ODBC 驅動程式會管理與資料來源的連接，而 SQL 則是用來從資料庫中選取記錄。

如需此版本 Visual C++ 隨附之 ODBC 驅動程式的清單，以及取得其他驅動程式的相關資訊，請參閱 [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
