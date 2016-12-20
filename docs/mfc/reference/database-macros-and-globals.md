---
title: "資料庫巨集和全域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫全域 [C++]"
  - "資料庫巨集 [C++]"
  - "全域資料庫函式 [C++]"
  - "全域函式 [C++], 資料庫函式"
  - "巨集 [C++], MFC 資料庫"
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料庫巨集和全域
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

巨集和全域在套用至 ODBC\-based 資料庫應用程式底下列出。  它們不適用於以 DAO\-base 的應用程式。  
  
 在 MFC 4.2 之前，巨集 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 提供非同步作業一個可能產生時間到其他處理序的機會。  從 MFC 4.2 開始，因為 MFC ODBC 類別只使用了同步作業，因此這些巨集的實作變更。  巨集 `AFX_ODBC_CALL` 不熟悉 MFC 4.2。  
  
### 資料庫巨集  
  
|||  
|-|-|  
|[AFX\_ODBC\_CALL](../Topic/AFX_ODBC_CALL.md)|呼叫傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。  `AFX_ODBC_CALL` 將重複呼叫函式，直到它不再傳回 `SQL_STILL_EXECUTING`。|  
|[AFX\_SQL\_ASYNC](../Topic/AFX_SQL_ASYNC.md)|呼叫 `AFX_ODBC_CALL`。|  
|[AFX\_SQL\_SYNC](../Topic/AFX_SQL_SYNC.md)|呼叫不傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。|  
  
### 資料庫全域  
  
|||  
|-|-|  
|[AfxGetHENV](../Topic/AfxGetHENV.md)|擷取 ODBC 環境的控制代碼目前正在由 MFC 使用。  您可以直接在呼叫 ODBC 中使用這個控制代碼。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)