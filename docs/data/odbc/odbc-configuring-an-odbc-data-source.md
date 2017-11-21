---
title: "ODBC： 設定 ODBC 資料來源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e347683a079227226513ce82f9623860e826228
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC：設定 ODBC 資料來源
若要使用[資料來源](../../data/odbc/data-source-odbc.md)所開發的應用程式，您必須使用 ODBC 管理員來設定它。 ODBC 管理員記錄的可用資料來源，其在 Windows 登錄中的連接資訊。 使用 ODBC 管理員來新增、 修改和刪除資料來源中的**資料來源**對話方塊中，可以新增或刪除 ODBC 驅動程式。  
  
> [!NOTE]
>  當您使用 MFC 資料存取物件 (DAO) 類別來 ODBC 存取，以及當您使用 MFC ODBC 類別，適用於這項資訊。  
  
 ODBC 管理員會自動隨 Microsoft Foundation Classes (MFC) 程式庫資料庫的支援。 如需 ODBC 管理員程式的詳細資訊，請參閱[ODBC 管理員](../../data/odbc/odbc-administrator.md)和線上的 ODBC 應用程式開發介面參考說明系統。  
  
 如需如何撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式[技術提示 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)   
 [ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)