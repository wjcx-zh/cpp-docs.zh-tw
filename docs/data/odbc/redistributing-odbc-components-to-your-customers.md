---
title: "轉散發 ODBC 元件給您的客戶 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 861eceef234b77b96179c51979cb7d1c0d09eeeb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="redistributing-odbc-components-to-your-customers"></a>轉散發 ODBC 元件給您的客戶
如果您將 ODBC 管理員程式的功能併入您的應用程式時，必須也要散發給您的使用者執行這些程式的檔案。 這些 ODBC 檔案位於 \OS\System 的目錄中的 Visual c + + CD-ROM。 Redistrb.wri 檔案和相同的目錄中的授權合約包含一份您可以重新發佈的 ODBC 檔案。  
  
 任何想要出貨的 ODBC 驅動程式，請參閱文件。 您需要決定哪些 Dll 和其他檔案，出貨。 您也應該閱讀[轉散發 ODBC 元件給您的客戶](../../data/odbc/redistributing-odbc-components-to-your-customers.md)，其中說明如何轉散發 ODBC 元件。  
  
 此外，您需要在大部分情況下包含一個其他檔案。 Odbccr32.dll 是 ODBC 資料指標程式庫。 這個程式庫提供的驅動程式層級 1 向前及向後捲動的功能。 它也提供支援快照集的功能。 如需有關 ODBC 資料指標程式庫的詳細資訊，請參閱[ODBC: ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
 下列主題提供使用 ODBC 資料庫類別的詳細資訊：  
  
-   [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC：設定 ODBC 資料來源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)   
 [ODBC 管理員](../../data/odbc/odbc-administrator.md)