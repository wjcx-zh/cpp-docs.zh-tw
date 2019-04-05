---
title: 連接資料來源
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
ms.openlocfilehash: 1740a34036798dac69ffc8b486e03bf6439845a5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024552"
---
# <a name="connecting-to-a-data-source"></a>連接資料來源

ODBC 資料來源是一組特定的資料，來存取該資料，以及資料來源，可以使用資料來源名稱所描述的位置所需的資訊。 從您的程式觀點來看，資料來源包括資料、 DBMS、 網路 （如果有的話） 和 ODBC。

若要存取資料來源所提供的資料，您的程式必須先建立資料來源的連接。 所有的資料存取是透過該連線管理。

資料來源連接由類別封裝[CDatabase](../../mfc/reference/cdatabase-class.md)。 當`CDatabase`物件連接到資料來源，您可以：

- 建構[資料錄集](../../mfc/reference/crecordset-class.md)，從資料表或查詢的選取資料錄。

- 管理[交易](../../data/odbc/transaction-odbc.md)，因此，所有的批次更新一次會認可至資料來源 （或資料來源會保持不變，復原整個交易），如果資料來源支援所需的層級的交易。

- 直接執行[SQL](../../data/odbc/sql.md)陳述式。

當您完成使用的資料來源連接時，關閉`CDatabase`物件，然後終結它或它重複用於新的連接。 如需有關資料來源連接的詳細資訊，請參閱[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。

## <a name="see-also"></a>另請參閱

[ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)