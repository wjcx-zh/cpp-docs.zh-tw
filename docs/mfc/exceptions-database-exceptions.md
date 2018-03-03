---
title: "例外狀況： 資料庫例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e853f2bd6f57c7ccc63e802f013661efb85d9796
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-database-exceptions"></a>例外狀況：資料庫例外狀況
本文說明如何處理資料庫例外狀況。 是否使用 MFC 類別開放式資料庫連接 (ODBC) 或 MFC 類別的資料存取物件 (DAO)，適用於大部分的這篇文章中的資料。 明確地標示為只適用於一個或其他模型。 主題包括：  
  
-   [例外狀況處理的方法](#_core_approaches_to_exception_handling)  
  
-   [資料庫例外狀況處理範例](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a>例外狀況處理的方法  
 是否正在使用 DAO 或是 ODBC 方法都是相同的。  
  
 您應該撰寫例外狀況處理常式來處理例外狀況。  
  
 捕捉資料庫例外狀況最實用的方法是測試您的應用程式例外狀況。 判斷可能的例外狀況，可能會發生在您的程式碼中的作業，並強制發生例外狀況。 接著檢查以查看擲回例外狀況時，追蹤輸出，或檢查偵錯工具中傳回的錯誤資訊。 這可讓您知道的傳回的碼，您會看到您要使用的例外狀況。  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>用於 ODBC 例外狀況的錯誤碼  
 除了由 framework 定義的傳回碼，其具有的名稱格式**AFX_SQL_ERROR_XXX**，部分[CDBExceptions](../mfc/reference/cdbexception-class.md)根據[ODBC](../data/odbc/odbc-basics.md)傳回碼。 具有表單的名稱，這類例外狀況的傳回碼**SQL_ERROR_XXX**。  
  
 傳回碼-架構定義和 ODBC 定義 — 資料庫類別可以傳回下記載[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)類別資料成員`CDBException`。 ODBC 所定義的傳回碼的其他資訊適用於 ODBC SDK*程式設計人員參考*MSDN Library 中。  
  
### <a name="error-codes-used-for-dao-exceptions"></a>所使用的 DAO 例外狀況的錯誤碼  
 DAO 的例外狀況的詳細資訊通常可使用。 您可以透過三個資料成員的已攔截存取錯誤資訊[CDaoException](../mfc/reference/cdaoexception-class.md)物件：  
  
-   [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含指標[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)物件會封裝與資料庫相關聯的錯誤物件 DAO 的集合中的錯誤資訊。  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含從 MFC DAO 類別中的延伸的錯誤碼。 這些錯誤碼，具有的名稱格式**AFX_DAO_ERROR_XXX**，記錄中的資料成員底下`CDaoException`。  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 OLE`SCODE`從 DAO，如果適用的話。 您很少必須具有此錯誤碼，不過工作。 通常的詳細資訊可在其他兩個資料成員中。 資料成員，如需詳細資訊請參閱關於`SCODE`值。  
  
 DAO 錯誤、 DAO 錯誤物件類型和 DAO 錯誤集合的其他資訊時才可使用類別[CDaoException](../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a>資料庫例外狀況處理範例  
 下列範例嘗試建構[CRecordset](../mfc/reference/crecordset-class.md)-衍生的堆積上物件**新**運算子，然後再開啟資料錄集 （適用於 ODBC 資料來源）。 適用於 DAO 類別中的類似範例，請參閱以下的 < DAO 例外狀況範例 >。  
  
### <a name="odbc-exception-example"></a>ODBC 例外狀況範例  
 [開啟](../mfc/reference/crecordset-class.md#open)成員函式可能會擲回例外狀況 (型別[CDBException](../mfc/reference/cdbexception-class.md)適用於 ODBC 類別)，因此這個程式碼括號**開啟**呼叫**再試一次**區塊。 後續**攔截**區塊將會攔截`CDBException`。 您可以檢查例外狀況呼叫的物件本身， `e`，但在此情況下就足夠了知道嘗試建立資料錄集失敗。 **攔截**區塊顯示訊息方塊，並清除刪除的資料錄集物件。  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>DAO 例外狀況範例  
 DAO 範例是類似於 odbc 中，但您通常可以擷取更多類型的資訊。 下列程式碼也會嘗試開啟資料錄集。 如果該嘗試擲回例外狀況，您可以檢查取得錯誤資訊的例外狀況物件的資料成員。 因為先前的 ODBC 範例，它是可能不足，無法知道嘗試建立資料錄集失敗。  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 這個程式碼取得錯誤訊息字串從[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)例外狀況物件的成員。 就會擲回例外狀況時，MFC 會填入這個成員。  
  
 如需所傳回的錯誤資訊的討論`CDaoException`物件，請參閱 < 類別[CDaoException](../mfc/reference/cdaoexception-class.md)和[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。  
  
 當您使用 Microsoft Jet (.mdb) 資料庫，且大部分情況下會使用 ODBC 時，會有一個物件時發生錯誤。 在極少數的情況下，當您使用 ODBC 資料來源，而且有多個錯誤，您可以逐一 DAO 的錯誤集合為基礎所傳回的錯誤數目[CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 迴圈時，每次呼叫[CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)以重新填滿`m_pErrorInfo`資料成員。  
  
## <a name="see-also"></a>請參閱  
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)

