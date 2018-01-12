---
title: "ODBC： 直接呼叫 ODBC API 函數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51fde2bb7ea73a2655c0b771dabfe14d2c833fb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接呼叫 ODBC API 函式
資料庫類別提供更簡單的介面，以[資料來源](../../data/odbc/data-source-odbc.md)比 ODBC。 如此一來，這些類別不會封裝所有 ODBC API。 類別的功能之外的任何功能，您必須直接呼叫 ODBC API 函式。 例如，您必須呼叫 ODBC 目錄函數 (**:: SQLColumns**， **:: SQLProcedures**， **:: SQLTables**，等等) 直接。  
  
> [!NOTE]
>  ODBC 資料來源是透過 MFC ODBC 類別，如本主題中所述，或透過 MFC 資料存取物件 (DAO) 類別存取。  
  
 直接呼叫 ODBC API 函式您必須採取相同若您正在進行的呼叫沒有架構，您可以採取的步驟。 這些步驟：  
  
-   配置儲存空間，則呼叫會傳回任何結果。  
  
-   傳遞 ODBC **HDBC**或**HSTMT**處理，根據函式的參數簽章。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)巨集來擷取 ODBC 控制代碼。  
  
     成員變數**CDatabase::m_hdbc**和**CRecordset::m_hstmt**便可使用，因此您不需要配置及初始化這些自己。  
  
-   可能是呼叫其他的 ODBC 函數無法準備或待處理的主要的呼叫。  
  
-   當您完成時，取消配置儲存體。  
  
 如需這些步驟的詳細資訊，請參閱[開放式資料庫連接 (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) MSDN 文件中的 SDK。  
  
 除了這些步驟中，您需要採取額外步驟以檢查函式傳回值，請確定您的程式不等候非同步呼叫完成，然後依此類推。 您可以使用，以簡化這些最後幾個步驟`AFX_SQL_ASYNC`和`AFX_SQL_SYNC`巨集。 如需詳細資訊，請參閱[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 參考*。  

  
## <a name="see-also"></a>請參閱  
 [ODBC 基本概念](../../data/odbc/odbc-basics.md)
