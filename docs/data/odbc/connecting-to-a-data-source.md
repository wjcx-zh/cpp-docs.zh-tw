---
title: "連接資料來源 | Microsoft Docs"
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
  - "連接 [C++], 資料來源"
  - "資料來源 [C++], 連接至"
  - "資料庫連接 [C++], MFC ODBC 類別"
  - "資料庫連接 [C++], ODBC"
  - "資料庫 [C++], 連接至"
  - "ODBC 連接 [C++], 使用"
  - "ODBC 資料來源 [C++], 連接"
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 連接資料來源
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 資料來源是一組特定資料，即存取該資料時的所需資訊，和使用一個資料來源名稱來說明的資料來源位置。  若是從程式觀點來看，資料來源包括了資料、DBMS、網路 \(若有的話\) 和 ODBC。  
  
 若要存取資料來源所提供的資料，您的程式必須先建立一個資料來源連接。  所有的資料存取都是透過該連接進行管理。  
  
 資料來源連接由 [CDatabase](../../mfc/reference/cdatabase-class.md) 類別進行封裝。  當 `CDatabase` 物件已連接至資料來源，您就可以：  
  
-   建構可選取資料表或是查詢資料錄的[資料錄集](../../mfc/reference/crecordset-class.md)。  
  
-   如果資料來源支援所需的交易層級，可管理[交易](../../data/odbc/transaction-odbc.md)來進行批次更新，使得所有交易可以一次認可至資料來源 \(或復原整筆交易，如此就不會變更資料來源\)。  
  
-   直接執行 [SQL](../../data/odbc/sql.md) 陳述式。  
  
 您可以在完成資料來源連接時關閉或終止該 `CDatabase` 物件，或在一個新連接中使用這個物件。  如需資料來源連接的詳細資訊，請參閱[資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)。  
  
## 請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)