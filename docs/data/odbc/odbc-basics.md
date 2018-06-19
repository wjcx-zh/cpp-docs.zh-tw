---
title: ODBC 基本概念 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69b3694292171f00e03cdb941def27fd9e8ffc84
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090295"
---
# <a name="odbc-basics"></a>ODBC 的基本概念
本主題提供開放式資料庫連接 (ODBC) 的基本概念：  
  
-   [ODBC 資料庫類別中的運作方式](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [ODBC 驅動程式搭配動態集的運作方式](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [您需要與您的應用程式轉散發 ODBC 元件](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 您也會想要讀取的相關的主題[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。  
  
> [!NOTE]
>  MFC ODBC 類別支援 Unicode 和多執行緒。 如需多執行緒支援的詳細資訊，請參閱[ODBC 類別和執行緒](../../data/odbc/odbc-classes-and-threads.md)  
  
 ODBC 是在呼叫層級的介面，可讓應用程式存取 ODBC 驅動程式是任何資料庫中的資料。 使用 ODBC，您可以建立資料庫應用程式具有存取權的任何資料庫使用者具有 ODBC 驅動程式。 ODBC 提供的 API，可讓您為獨立於來源資料庫管理系統 (DBMS) 的應用程式。  
  
 ODBC 是中的資料庫部分的 Microsoft Windows 開啟服務架構 (WOSA)，可讓 windows 桌面應用程式連接到多個運算環境不需要重寫的每個平台應用程式的介面。  
  
 以下是 ODBC 的元件：  
  
-   ODBC API  
  
     呼叫函式的程式庫、 一組錯誤代碼，以及標準[SQL](../../data/odbc/sql.md)語法來存取 Dbms 資料。  
  
-   ODBC 驅動程式管理員  
  
     動態連結程式庫 (Odbc32.dll) 代表應用程式會載入 ODBC 資料庫驅動程式。 這個 DLL 是您的應用程式以透明的。  
  
-   ODBC 資料庫驅動程式  
  
     處理特定 Dbms ODBC 函數呼叫的一或多個 Dll。 如需提供的驅動程式的清單，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
-   [ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     動態連結程式庫 (Odbccr32.dll) 位於 ODBC 驅動程式管理員與驅動程式之間，而且處理資料中捲動。  
  
-   [ODBC 管理員](../../data/odbc/odbc-administrator.md)  
  
     用來設定 DBMS，使其可為應用程式的資料來源的工具。  
  
 應用程式達到透過 ODBC 驅動程式，特別是針對 DBMS 所撰寫的工作，而不是直接使用 DBMS Dbms 獨立性。 驅動程式會將轉譯成 DBMS 可以使用，以簡化開發人員的工作，並且讓它成為可供各種不同的資料來源的命令呼叫。  
  
 資料庫類別支援具有 ODBC 驅動程式的任何資料來源。 這可能，比方說，包括關聯式資料庫、 編製索引循序存取方法 (ISAM) 資料庫、 Microsoft Excel 試算表或文字檔。 ODBC 驅動程式管理資料來源的連接，SQL 用來從資料庫選取記錄。  
  
 包含在這個版本的 Visual c + + 中的 ODBC 驅動程式清單以及取得其他驅動程式的相關資訊，請參閱[ODBC 驅動程式清單](../../data/odbc/odbc-driver-list.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開放式資料庫連接 (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)