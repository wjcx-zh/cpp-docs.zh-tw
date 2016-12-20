---
title: "轉散發 ODBC 元件給您的客戶 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "元件 [C++]"
  - "元件 [C++], 散發"
  - "元件 [C++], 轉散發"
  - "ODBC 管理員"
  - "ODBC 元件, 轉散發"
  - "ODBC, 散發元件"
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 轉散發 ODBC 元件給您的客戶
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果您將 ODBC 管理員程式的功能結合至您的應用程式中，就必須也將這些執行程式的檔案散發給您的使用者。  這些 ODBC 檔案是位於 Visual C\+\+ CD\-ROM 中 \\OS\\System 的目錄中。  在相同目錄中的 Redistrb.wri 檔和授權合約包含您可以轉散發 \(Redistribute\) 的 ODBC 檔案清單。  
  
 請參閱任何您計劃附隨的 ODBC 驅動程式之相關文件。  您必須決定附隨哪些 DLL 和其他檔案。  
  
 如需 ODBC 元件和驅動程式的詳細資訊，請參閱[安裝資料庫支援](../../data/installing-database-support-mfc-atl.md)，以及說明如何轉散發 ActiveX 控制項的[轉散發控制項](../../data/ado-rdo/redistributing-controls.md)。  
  
 除此之外，您還必須在大多數情況中包括另外一個檔案。  Odbccr32.dll 是 ODBC 資料指標程式庫。  這個程式庫提供了層級 1 驅動程式向前和向後捲動的功能。  它也提供了支援快照集的功能。  如需 ODBC 資料指標程式庫的詳細資訊，請參閱 [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
 下列主題提供使用 ODBC 及資料庫類別的詳細資訊：  
  
-   [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC：設定 ODBC 資料來源](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## 請參閱  
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)   
 [ODBC 管理員](../../data/odbc/odbc-administrator.md)