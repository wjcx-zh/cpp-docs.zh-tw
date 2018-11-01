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
ms.openlocfilehash: 81b1f6d06d909b5b046703b97c4574270efbdd46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591720"
---
# <a name="odbc-basics"></a>ODBC 的基本概念

本主題提供的基本概念的開放式資料庫連接 (ODBC):

- [ODBC 資料庫類別的運作方式](../../data/odbc/odbc-and-the-database-classes.md)

- [ODBC 驅動程式搭配動態集的運作方式](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [您需要使用您的應用程式轉散發 ODBC 元件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

您也會想要閱讀相關的主題[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。

> [!NOTE]
> ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。

> [!NOTE]
> MFC ODBC 類別都支援 Unicode 和多執行緒。 如需多執行緒支援的詳細資訊，請參閱[ODBC 類別和執行緒](../../data/odbc/odbc-classes-and-threads.md)

ODBC 是呼叫層級的介面，可讓應用程式存取的 ODBC 驅動程式是任何資料庫中的資料。 使用 ODBC，您可以建立資料庫應用程式存取任何資料庫，您的使用者具有 ODBC 驅動程式。 ODBC 會提供一個 API，可讓您的應用程式是獨立於來源資料庫管理系統 (DBMS)。

ODBC 是資料庫部分的 Microsoft Windows 開啟服務架構 (WOSA)，這是可讓 Windows 桌面應用程式，以連接到多個計算環境而不重寫每個平台應用程式的介面。

以下是 ODBC 的元件：

- ODBC API

   函式的程式庫呼叫，一組錯誤代碼和標準[SQL](../../data/odbc/sql.md)來存取 Dbms 資料的語法。

- ODBC 驅動程式管理員

   動態連結程式庫 (Odbc32.dll) 代表應用程式會載入 ODBC 資料庫驅動程式。 這個 DLL 是向您的應用程式。

- ODBC 資料庫驅動程式

   處理特定 Dbms 的 ODBC 函數呼叫的一或多個 Dll。 如需提供的驅動程式的清單，請參閱 < [ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

- [ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)

   動態連結程式庫 (Odbccr32.dll) 間 ODBC 驅動程式管理員和驅動程式，並處理並且捲動瀏覽資料。

- [ODBC 管理員](../../data/odbc/odbc-administrator.md)

   工具，用於設定 DBMS，以使其可做為應用程式的資料來源。

應用程式可達到 Dbms 透過 ODBC 驅動程式，特別是針對 DBMS 所撰寫的工作，而不是直接使用 DBMS 的獨立性。 驅動程式會轉譯成命令可以使用其 DBMS，簡化開發人員的工作，並讓它可用於各種不同的資料來源的呼叫。

資料庫類別支援的 ODBC 驅動程式的任何資料來源。 這可能，比方說，包括關聯式資料庫、 編製索引循序存取方法 (ISAM) 資料庫、 Microsoft Excel 試算表或文字檔案。 ODBC 驅動程式管理資料來源連接和 SQL 用來從資料庫選取記錄。

如需包含在這個版本的 Visual c + + 中的 ODBC 驅動程式的清單，以及取得額外的驅動程式的相關資訊，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。

## <a name="see-also"></a>另請參閱

[開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)