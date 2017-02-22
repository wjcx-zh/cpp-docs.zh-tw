---
title: "ODBC：直接呼叫 ODBC API 函式 | Microsoft Docs"
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
  - "API [C++], 呼叫"
  - "目錄函式 (ODBC)"
  - "目錄函式 (ODBC), 呼叫"
  - "直接 ODBC API 呼叫"
  - "ODBC [C++], API 函式"
  - "ODBC [C++], 目錄函式"
  - "ODBC API 函式 [C++]"
  - "ODBC API 函式 [C++], 呼叫"
  - "ODBC 類別 [C++], 與 ODBC API 的比較"
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ODBC：直接呼叫 ODBC API 函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

資料庫類別提供了一個比 ODBC 簡單的[資料來源](../../data/odbc/data-source-odbc.md)介面。  因此這個類別不會封裝所有 ODBC API。  如果您需要使用任何超出類別功能之外的功能，便必須直接呼叫 ODBC API 函式。  例如，您必須直接呼叫 ODBC 資料庫目錄函式 \(**::SQLColumns**、**::SQLProcedures**、**::SQLTables** 和其他函式\)。  
  
> [!NOTE]
>  ODBC 資料來源可透過 MFC ODBC 類別存取 \(如本主題所述\)，或透過 MFC 資料存取物件 \(DAO\) 類別存取。  
  
 若要直接呼叫一個 ODBC API 函式，您必須採用在不使用架構情況下製作呼叫時的相同步驟。  這些步驟為：  
  
-   配置任何呼叫傳回結果之儲存體。  
  
-   根據函式的參數簽章，傳遞一個 ODBC **HDBC** 或 **HSTMT** 控制代碼。  使用 [AFXGetHENV](../Topic/AfxGetHENV.md) 巨集來擷取 ODBC 控制代碼。  
  
     成員變數 \(Member Variable\) **CDatabase::m\_hdbc** 和 **CRecordset::m\_hstmt** 是可使用的，因此您不需自行配置及初始化這些變數。  
  
-   也許需要呼叫其他 ODBC 函式來為主要函式呼叫預備或待處理。  
  
-   完成時解除儲存體配置。  
  
 如需這些步驟的詳細資訊，請參閱 MSDN 文件中的[開放式資料庫連接 \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK。  
  
 除了這些步驟，您還需要採取其他步驟來檢查函式傳回值，以確定您的程式沒有在等待非同步的函式呼叫結束等等。  您可以使用 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 巨集，簡化最後的步驟。  如需詳細資訊，請參閱《MFC 參考》中的[巨集和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)。  
  
## 請參閱  
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)