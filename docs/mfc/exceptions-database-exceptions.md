---
title: '例外狀況: 資料庫例外狀況'
ms.date: 11/04/2016
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
ms.openlocfilehash: 2f7f3bff9f28968361ecfa7374a235a727443004
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285551"
---
# <a name="exceptions-database-exceptions"></a>例外狀況: 資料庫例外狀況

這篇文章說明如何處理資料庫例外狀況。 不論您使用 MFC 類別使用開放式資料庫連接 (ODBC) 或 MFC 類別的資料存取物件 (DAO)，適用於大部分的這篇文章中的資料。 其中一個或另一個模型特有的資料明確標記。 主題包括：

- [例外狀況處理的方法](#_core_approaches_to_exception_handling)

- [資料庫例外狀況處理範例](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a> 例外狀況處理的方法

無論您使用 DAO 或是 ODBC 方法都是相同的。

您應該一律撰寫例外狀況處理常式來處理例外狀況。

若要測試您的應用程式，使用例外狀況，是最實用的方法，以擷取資料庫例外狀況。 判斷可能的例外狀況，可能會發生在您的程式碼中的作業，並強制發生的例外狀況。 然後檢查追蹤輸出，以查看哪種例外狀況會擲回，或檢查偵錯工具中傳回的錯誤資訊。 這可讓您知道傳回的碼，您會看到您使用的例外狀況。

### <a name="error-codes-used-for-odbc-exceptions"></a>用於 ODBC 例外狀況的錯誤碼

架構所定義的傳回碼，除了具有名稱格式**AFX_SQL_ERROR_XXX**，部分[CDBExceptions](../mfc/reference/cdbexception-class.md)為基礎[ODBC](../data/odbc/odbc-basics.md)傳回碼。 這類例外狀況的傳回碼具有名稱格式**SQL_ERROR_XXX**。

傳回碼 — 架構定義和 ODBC 定義 — 資料庫類別可以傳回下記載[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)類別的資料成員`CDBException`。 傳回碼 ODBC 所定義的其他資訊可用於 ODBC SDK*程式設計人員參考*MSDN Library 中。

### <a name="error-codes-used-for-dao-exceptions"></a>用於 DAO 例外狀況的錯誤碼

DAO 例外狀況，也通常會顯示資訊。 您可以透過三個資料成員的已攔截存取錯誤資訊[CDaoException](../mfc/reference/cdaoexception-class.md)物件：

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含的指標[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)封裝與資料庫相關聯的錯誤物件的 DAO 的集合中的錯誤資訊的物件。

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含從 MFC DAO 類別的延伸的錯誤碼。 這些錯誤碼，具有名稱格式**AFX_DAO_ERROR_XXX**，會記錄在中的資料成員`CDaoException`。

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 OLE **SCODE**從 DAO，如果適用的話。 您很少必須具有此錯誤碼，不過運作。 通常的詳細資訊位於其他兩個資料成員。 了解更多的資料成員**SCODE**值。

類別底下可使用 DAO 錯誤、 DAO 錯誤物件類型和 DAO 錯誤集合的其他資訊[CDaoException](../mfc/reference/cdaoexception-class.md)。

##  <a name="_core_a_database_exception.2d.handling_example"></a> 資料庫例外狀況處理範例

下列範例嘗試建構[CRecordset](../mfc/reference/crecordset-class.md)-衍生的物件，使用堆積**新**運算子，然後開啟資料錄集 （適用於 ODBC 資料來源）。 DAO 類別的類似範例，請參閱下方的 < DAO 例外狀況範例 >。

### <a name="odbc-exception-example"></a>ODBC 例外狀況範例

[開放](../mfc/reference/crecordset-class.md#open)成員函式可能會擲回例外狀況 (型別的[CDBException](../mfc/reference/cdbexception-class.md)適用於 ODBC 類別)，因此這個程式碼括號`Open`呼叫**嘗試**區塊。 後續**攔截**區塊會攔截`CDBException`。 您可以檢查例外狀況呼叫的物件本身， `e`，但在此情況下就已足夠了解建立資料錄集的嘗試已失敗。 **攔截**區塊顯示訊息方塊，並清除刪除的資料錄集物件。

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 例外狀況範例

DAO 範例類似於 ODBC 的範例，但您通常可以擷取更多種類的資訊。 下列程式碼也會嘗試開啟資料錄集。 如果該嘗試擲回例外狀況，您可以檢查資訊時發生錯誤的例外狀況物件的資料成員。 因為先前的 ODBC 範例，它是可能不足以了解建立資料錄集的嘗試失敗。

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此程式碼會取得錯誤訊息字串從[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)例外狀況物件的成員。 它會擲回例外狀況時，MFC 會填入這個成員。

如需所傳回的錯誤資訊的討論`CDaoException`物件，請參閱類別[CDaoException](../mfc/reference/cdaoexception-class.md)並[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。

當您使用 Microsoft Jet (.mdb) 資料庫，且大部分情況下會使用 ODBC 時，會有只有一個物件時發生錯誤。 在罕見的情況下，當您使用 ODBC 資料來源，而且有多個錯誤，可以循環使用 DAO 的錯誤集合，根據所傳回的錯誤數目[CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 每次執行迴圈時，呼叫[CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)若要重新填滿`m_pErrorInfo`資料成員。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
