---
title: 連接到資料來源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b6a33f1e2421c56f89184d26185903b4ec7859e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088387"
---
# <a name="connecting-to-a-data-source"></a>連接資料來源
ODBC 資料來源是一組特定的資料，以存取該資料，以及可以使用資料來源名稱所描述的資料來源中的位置所需的資訊。 從您程式的觀點來看，資料來源包括資料、 DBMS、 網路 （如果有的話） 和 ODBC。  
  
 若要存取資料來源所提供的資料，您的程式必須先建立資料來源的連接。 所有資料存取是透過該連線都管理。  
  
 資料來源連接由類別封裝[CDatabase](../../mfc/reference/cdatabase-class.md)。 當`CDatabase`物件連接到資料來源，您可以：  
  
-   建構[資料錄集](../../mfc/reference/crecordset-class.md)，其中選取資料表或查詢中的記錄。  
  
-   管理[交易](../../data/odbc/transaction-odbc.md)，讓所有的批次更新一次被認可至資料來源 （或整個異動會復原資料來源是不變，如此），如果資料來源支援所需的等級的交易。  
  
-   直接執行[SQL](../../data/odbc/sql.md)陳述式。  
  
 您可以在完成資料來源連接時關閉`CDatabase`物件，然後終結或新的連接中使用。 如需有關資料來源連接的詳細資訊，請參閱[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)