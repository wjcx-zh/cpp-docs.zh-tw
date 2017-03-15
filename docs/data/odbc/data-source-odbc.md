---
title: "資料來源 (ODBC) | Microsoft Docs"
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
  - "CDatabase 類別, 資料來源連接"
  - "設定 ODBC 資料來源"
  - "ODBC 資料來源"
  - "ODBC 資料來源, 設定"
  - "ODBC 資料來源, 由 CDatabase 表示"
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料來源 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 在資料庫詞彙中，資料來源是一組特定的資料，即存取該資料的所需資訊，和一個可使用資料來源名稱來說明的資料來源位置。  若要使用 [CDatabase](../../mfc/reference/cdatabase-class.md) 類別，資料來源必須是您透過開放式資料庫連接 \(ODBC\) 管理員所設定的其中之一。  資料來源範例包括透過網路在 Microsoft SQL Server 上的遠端資料庫，或在本機目錄中的 Microsoft Access 檔案。  您可以從您的應用程式存取任何您擁有 ODBC 驅動程式的資料來源。  
  
 您也可以在您的應用程式中同時擁有一或多個作用中的資料來源，每個資料來源都可以一個 `CDatabase` 物件表示。  您也可以擁有任何資料來源的多個同時連接。  您可以根據所安裝的驅動程式和您的 ODBC 驅動程式功能，來連接遠端和本機資料來源。  如需資料來源和 ODBC 管理員的詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md) 和 [ODBC 管理員](../../data/odbc/odbc-administrator.md)。  
  
 下列主題將進一步說明資料來源：  
  
-   [資料來源：管理連接 \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [資料來源：決定資料來源的結構描述 \(ODBC\)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)