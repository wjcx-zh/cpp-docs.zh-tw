---
title: "動態集的 ODBC 驅動程式需求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c444cd8e8d13cca7d891dba92e881b8ca167bbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-driver-requirements-for-dynasets"></a>動態集的 ODBC 驅動程式需求
在 MFC ODBC 資料庫類別中，動態集是資料錄集與動態屬性。它們會維持已同步處理與資料來源所規定的方式。 MFC 動態集 （但不是順向資料錄集） 需要層級 2 API 的一致性與 ODBC 驅動程式。 如果驅動程式您[資料來源](../../data/odbc/data-source-odbc.md)符合層級 1 應用程式開發介面設定，您仍然可以使用可更新和唯讀快照集和順向資料錄集，但不是使用動態集。 不過，如果支援擴充的擷取和索引鍵集驅動資料指標層級 1 驅動程式可以支援 dynaset。  
  
 在 ODBC 術語中，動態集和快照集被指資料指標。 資料指標是一種機制，用於追蹤的資料錄集中的位置。 如需動態集的驅動程式需求的詳細資訊，請參閱[動態](../../data/odbc/dynaset.md)。 如需資料指標的詳細資訊，請參閱[開放式資料庫連接 (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) MSDN 文件中的 SDK。  
  
> [!NOTE]
>  可更新資料錄集時，ODBC 驅動程式必須支援任一定位的 update 陳述式或**:: SQLSetPos** ODBC API 函式。 如果兩者都有支援，MFC 會使用**:: SQLSetPos**為了提高效率。 或者，快照集，您可以使用資料指標程式庫，可提供所需的支援可更新的快照集 （靜態資料指標和定位的 update 陳述式）。  
  
## <a name="see-also"></a>請參閱  
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)