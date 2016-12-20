---
title: "什麼是 DAO 和 ODBC？ | Microsoft Docs"
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
  - "DAO (資料存取物件), 與 ODBC"
  - "ODBC, 關於 ODBC"
ms.assetid: 22cc2f75-7ff6-47bc-ac56-56a40591104c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 什麼是 DAO 和 ODBC？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料存取物件 \(Data Access Object，DAO\) 和開放式資料庫連接 \(Open Database Connectivity，ODBC\) 都是可讓您撰寫獨立於任何特定資料庫管理系統 \(DBMS\) 的應用程式的 API。  
  
 DAO 對於使用 Microsoft Access Basic 或 Microsoft Visual Basic 的資料庫開發人員應該不陌生。  DAO 使用 Microsoft Jet 資料庫引擎以提供一組資料存取物件：資料庫物件、tabledef 和 querydef 物件、資料錄集物件和其他物件。  DAO 最適合處理 .mdb 檔，例如以 Microsoft Access 建立的檔案，但是您也可以透過 DAO 和 Microsoft Jet 資料庫引擎來存取 ODBC 資料來源。  
  
 ODBC 提供一個 API，不同的資料庫廠商都可透過特定 DBMS 的 ODBC 驅動程式來實作它。  您的程式使用此 API 來呼叫 ODBC 驅動程式管理員，它再將呼叫傳遞給適當的驅動程式。  驅動程式將依次使用 SQL 來與 DBMS 互動。  
  
> [!NOTE]
>  ODBC 是 Microsoft Windows Open Standards Architecture \(WOSA\) 的主要部分。  DAO 已針對 Microsoft Jet 資料庫引擎最佳化，不過您仍可使用該引擎來存取 ODBC 和其他的外部資料庫，並且個別的 ODBC API 以及依據它的 MFC 類別也還可使用，並仍在您選取資料庫工具時佔著一席之地。  
  
## 請參閱  
 [資料存取常見問題集](../data/data-access-frequently-asked-questions-mfc-data-access.md)