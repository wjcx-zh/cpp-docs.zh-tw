---
title: "您可能對預設程式碼所做的變更 (MFC 資料存取) | Microsoft Docs"
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
  - "資料錄檢視 [C++], 自訂預設程式碼"
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 您可能對預設程式碼所做的變更 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)會為您撰寫資料錄集類別，可選取單一資料表中的所有資料錄。  您經常會想要以下列一種或多種方式修改該行為：  
  
-   設定資料錄集的篩選條件或排序順序。  請在建構資料錄集物件之後，但是在呼叫其 **Open** 成員函式之前，在 `OnInitialUpdate` 中執行這項操作。  如需詳細資訊，請參閱[資料錄集：篩選資料錄 \(ODBC\)](../data/odbc/recordset-filtering-records-odbc.md) 和[資料錄集：排序資料錄 \(ODBC\)](../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   參數化資料錄集。  請在篩選之後指定實際的執行階段參數值。  如需詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   將自訂的 SQL 字串傳遞至 [Open](../Topic/CRecordset::Open.md) 成員函式。  如需利用這項技術可以完成之作業的討論，請參閱 [SQL：自訂資料錄集的 SQL 陳述式 \(ODBC\)](../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
## 請參閱  
 [使用資料錄檢視](../data/using-a-record-view-mfc-data-access.md)