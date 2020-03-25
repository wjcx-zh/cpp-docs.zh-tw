---
title: 連接到資料來源
ms.date: 11/04/2016
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
ms.openlocfilehash: 712910aca2622f2678b8b9d06b18a2fdbf9157e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213339"
---
# <a name="connecting-to-a-data-source"></a>連接到資料來源

ODBC 資料來源是一組特定的資料、存取該資料所需的資訊，以及資料來源的位置，可以使用資料來源名稱加以描述。 從您的程式觀點來看，資料來源包含資料、DBMS、網路（如果有的話）和 ODBC。

若要存取資料來源所提供的資料，您的程式必須先建立資料來源的連接。 所有資料存取都是透過該連接來管理。

資料來源連接是由類別[CDatabase](../../mfc/reference/cdatabase-class.md)所封裝。 當 `CDatabase` 物件連接至資料來源時，您可以：

- 結構化[記錄集](../../mfc/reference/crecordset-class.md)，可選取資料表或查詢中的記錄。

- 管理[交易](../../data/odbc/transaction-odbc.md)、批次處理更新，讓所有動作一次認可至資料來源（如果資料來源支援所需的交易層級，則會回復整個交易，讓資料來源保持不變）。

- 直接執行[SQL](../../data/odbc/sql.md)語句。

當您完成使用資料來源連接時，請關閉 `CDatabase` 物件，並將它終結或重複使用於新的連接。 如需有關資料來源連接的詳細資訊，請參閱[資料來源（ODBC）](../../data/odbc/data-source-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)
