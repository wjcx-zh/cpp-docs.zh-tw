---
title: "存取 ODBC 和 SQL | Microsoft Docs"
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
  - "API 呼叫 [C++], 直接呼叫 DAO 或 ODBC"
  - "ODBC [C++], API 函式"
  - "ODBC API 函式 [C++]"
  - "ODBC API 函式 [C++], 從 MFC 呼叫"
  - "SQL [C++], 呼叫 ODBC API 函式"
  - "Windows API [C++], 從 MFC 呼叫"
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 存取 ODBC 和 SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫可以封裝許多 Windows API 呼叫，同時也可使您直接呼叫任何 Windows API 函式。  這種資料庫類別可提供給您在 ODBC API 上相同的使用彈性。  由於資料庫類別為您遮蓋了多數的 ODBC 複雜性，因此您可以從程式的任意位置直接呼叫 ODBC API 函式。  
  
 同樣地，資料庫類別會為您遮蔽掉大量地必須使用 [SQL](../../data/odbc/sql.md) 的情況，但是您仍可依照個人需要直接使用 SQL。  您可以在開啟資料錄集時，傳遞一個自訂的 SQL 陳述式 \(或是設定部分的預設陳述式\) 來自訂資料錄集物件。  您也可以使用 [CDatabase](../../mfc/reference/cdatabase-class.md) 類別的 [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 成員函式直接製作 SQL 呼叫。  
  
 如需詳細資訊，請參閱 [ODBC：直接呼叫 ODBC API 函式](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)和 [SQL：製作直接的 SQL 呼叫 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。  
  
## 請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)