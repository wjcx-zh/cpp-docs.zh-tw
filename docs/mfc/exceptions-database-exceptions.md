---
title: "例外狀況：資料庫例外狀況 | Microsoft Docs"
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
  - "DAO [C++], 例外狀況"
  - "資料庫例外狀況 [C++]"
  - "資料庫 [C++], 例外狀況處理"
  - "錯誤碼 [C++], 資料庫例外狀況處理"
  - "例外狀況處理 [C++], 資料庫"
  - "例外狀況 [C++], 資料庫"
  - "ODBC [C++], 例外狀況"
  - "ODBC 例外狀況 [C++]"
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 例外狀況：資料庫例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何處理資料庫例外狀況。  大部分的本文套用您是否使用開放式資料庫連接 \(Open Database Connectivity，ODBC\) MFC 類別或資料存取物件 \(DAO\) MFC 類別一起使用。  為或其他模型的材質特定明確標記。  主題包括：  
  
-   [對例外狀況處理的方法](#_core_approaches_to_exception_handling)  
  
-   [資料庫例外狀況處理範例](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> 對例外狀況處理的方法  
 這個方法等於您是否使用 DAO 或 ODBC 一起使用。  
  
 您應該在處理例外狀況會固定寫入例外處理常式。  
  
 對攔截資料庫例外狀況最 Pragmatic 的方法將測試與例外狀況案例中的應用程式。  判斷可能為一個作業發生在程式碼中可能的例外狀況，並強制發生例外狀況。  然後檢查追蹤輸出查看例外狀況，或檢查在偵錯工具中傳回的錯誤資訊。  這會告訴您要傳回碼針對您所使用的例外狀況案例會看到。  
  
### 用於 ODBC 例外狀況的錯誤碼  
 除了架構所定義的傳回碼以外，還有表單 **AFX\_SQL\_ERROR\_XXX**的名稱，某些 [CDBExceptions](../mfc/reference/cdbexception-class.md) 根據 [ODBC](../data/odbc/odbc-basics.md) 傳回碼。  這類例外狀況的傳回碼有表單 **SQL\_ERROR\_XXX**的名稱。  
  
 傳回碼— Framework 定義和 ODBC 定義—類別資料庫可能傳回記錄在類別下 `CDBException`[m\_nRetCode](../Topic/CDBException::m_nRetCode.md) 的資料成員。  如需 ODBC 定義的傳回碼的其他資訊可在 ODBC SDK *程式設計人員參考* MSDN Library。  
  
### 用於 DAO 例外狀況的錯誤碼  
 如需 DAO 例外狀況，詳細資訊通常是可用的。  您可以攔截的 [CDaoException](../mfc/reference/cdaoexception-class.md) 物件的三個資料成員存取錯誤訊息:  
  
-   [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 包含指標對 [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md) 物件在錯誤物件的 DAO 的集合的封裝錯誤資訊與資料庫。  
  
-   [m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md) 包含從 MFC DAO 類別的延伸錯誤碼。  這些錯誤碼，有表單 **AFX\_DAO\_ERROR\_XXX**的名稱，記錄在 `CDaoException`資料成員中。  
  
-   [m\_scode](../Topic/CDaoException::m_scode.md) 包含從 DAO 的 OLE `SCODE` 的話，  不過您很少需要此錯誤碼。  通常詳細資訊可以在其他兩個資料成員。  為多個參閱資料成員相關的 `SCODE` 值。  
  
 如需 DAO 錯誤、DAO 錯誤物件型別和 DAO 錯誤集合的其他資訊可在類別 [CDaoException](../mfc/reference/cdaoexception-class.md)下。  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> 資料庫例外狀況處理範例  
 下列範例嘗試建構 [CRecordset](../mfc/reference/crecordset-class.md)\-在堆積中衍生物件與 **new** 運算子，然後開啟資料錄集 \(為 ODBC 資料來源\)。  如需 DAO 類別的類似範例，請參閱「DAO 例外狀況範例」。  
  
### ODBC 例外狀況範例  
 [開啟](../Topic/CRecordset::Open.md) 成員函式可以擲回例外狀況 \(ODBC 類別的 [CDBException](../mfc/reference/cdbexception-class.md) 型別\)，因此，這個括號碼與 **try** 區塊的 **Open** 呼叫。  後續的  **catch** 區塊會攔截 `CDBException`。  您可以檢查例外狀況物件，呼叫 `e`，但在這種情況下就知道足夠嘗試建立資料錄集失敗。  **catch** 區塊顯示訊息方塊並將刪除資料錄集物件清除。  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/CPP/exceptions-database-exceptions_1.cpp)]  
  
### DAO 例外狀況範例  
 DAO 範例類似 ODBC 的範例，不過您通常可以擷取更多的資訊。  下列程式碼會嘗試開啟資料錄集。  如果該嘗試擲回例外狀況，您可以檢查例外狀況物件的資料成員錯誤資訊的。  與目前 ODBC 範例，它有可能知道嘗試建立資料錄集失敗。  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/CPP/exceptions-database-exceptions_2.cpp)]  
  
 這個程式碼會從例外狀況物件的 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 成員取得錯誤訊息字串。  會擲回例外狀況時， MFC 會填入這個成員。  
  
 如需錯誤資訊的討論由 `CDaoException` 物件傳回，參閱 [CDaoException](../mfc/reference/cdaoexception-class.md) 和 [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。  
  
 當您使用 Microsoft Jet \(.mdb\) 資料庫一起使用，因此，在大部分情況下，當您使用 ODBC 時，只會包含錯誤物件。  在少數情況下，當您使用 ODBC 資料來源，而且有多個錯誤，您可以透過 DAO 的根據 [CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md)傳回的錯誤數目的錯誤集合執行迴圈。  每次迴圈，呼叫重新填滿 `m_pErrorInfo` 資料成員的 [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 。  
  
## 請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)