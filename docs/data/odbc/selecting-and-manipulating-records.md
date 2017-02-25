---
title: "選取和操作資料錄 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料錄集, 選取資料錄"
  - "資料錄選取, MFC ODBC 類別"
  - "資料錄, 選取"
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 選取和操作資料錄
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通常在使用 SQL **SELECT** 陳述式選取資料來源中的資料錄時，會取得結果集 \(Result Set\)，這是一個資料表或是查詢的資料錄集。  在資料庫類別中，您可以使用資料錄集物件選取或存取該結果集。  這是一個衍生自 [CRecordset](../../mfc/reference/crecordset-class.md) 類別的應用程式特定類別的物件。  您可以在定義資料錄集類別時，指定將與該類別關聯的資料來源、要使用的資料表，和資料表的資料行。  MFC 應用程式精靈或是 \[加入類別\] \(詳述於[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)\) 會以特定資料來源連接建立一個類別。  精靈會撰寫 `CRecordset` 類別的 [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 成員函式來傳回資料表名稱。  如需使用精靈建立資料錄集類別的詳細資訊，請參閱 [MFC 應用程式精靈、資料庫支援](../../mfc/reference/database-support-mfc-application-wizard.md)和[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 在 Run Time 使用一個 [CRecordset](../../mfc/reference/crecordset-class.md) 物件，您可以：  
  
-   檢查目前資料錄的資料欄位  
  
-   篩選或是排序資料錄集  
  
-   自訂預設的 SQL **SELECT** 陳述式  
  
-   在選取的資料錄中捲動  
  
-   加入、更新或是刪除資料錄 \(若資料來源和資料錄集都是可更新的\)  
  
-   測試資料錄集是否允許重新查詢，並重新整理資料錄集的內容  
  
 結束使用資料錄集物件時，請將其關閉並終止。  如需資料錄集的詳細資訊，請參閱[資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md) 文件。  
  
## 請參閱  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)