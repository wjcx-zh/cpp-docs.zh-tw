---
title: "資料來源： 決定資料來源 (ODBC) 的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fc425cf767db6939223288ebe74dcbc7fd4cf5b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>資料來源：決定資料來源的結構描述 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 若要設定資料成員中您`CRecordset`物件，您需要知道所連接的資料來源的結構描述。 決定資料來源的結構描述會牽涉到取得的資料來源中的資料表清單，每個資料表中的資料行、 資料類型的每個資料行的清單，以及任何存在的索引。  
  
## <a name="see-also"></a>請參閱  
 [資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)   
 [資料來源：管理連接 (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)