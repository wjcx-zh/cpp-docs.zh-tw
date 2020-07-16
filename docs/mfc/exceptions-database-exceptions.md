---
title: 例外狀況：資料庫例外狀況
ms.date: 09/17/2019
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
ms.openlocfilehash: 96f9e5f836205df71e03638858cb00b788d03c0b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403721"
---
# <a name="exceptions-database-exceptions"></a>例外狀況：資料庫例外狀況

本文說明如何處理資料庫例外狀況。 本文中的大部分資料都適用于您是否使用開放式資料庫連接（ODBC）的 MFC 類別或資料存取物件（DAO）的 MFC 類別。 其中一個或其他模型的特定材質會明確標示。 主題包括：

- [例外狀況處理的方法](#_core_approaches_to_exception_handling)

- [資料庫例外狀況處理範例](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>例外狀況處理的方法

無論您使用的是 DAO （已過時）還是 ODBC，方法都相同。

您應該一律撰寫例外狀況處理常式來處理例外狀況。

攔截資料庫例外狀況最實用的方法，就是在發生例外狀況的情況下測試您的應用程式。 判斷程式碼中某項作業可能會發生的例外狀況，並強制發生例外狀況。 然後檢查追蹤輸出以查看擲回的例外狀況，或在偵錯工具中檢查傳回的錯誤資訊。 這可讓您知道您所使用的例外狀況案例所看到的傳回碼。

### <a name="error-codes-used-for-odbc-exceptions"></a>ODBC 例外狀況所使用的錯誤碼

除了架構所定義的傳回碼（其名稱為**AFX_SQL_ERROR_XXX**的格式），有些[CDBExceptions](reference/cdbexception-class.md)是以[ODBC](../data/odbc/odbc-basics.md)傳回碼為基礎。 這類例外狀況的傳回碼具有格式**SQL_ERROR_XXX**的名稱。

資料庫類別可以傳回的傳回碼（架構定義和 ODBC 定義的）都會記錄在類別的[m_nRetCode](reference/cdbexception-class.md#m_nretcode)資料成員底下 `CDBException` 。 Odbc 程式設計[人員參考](/sql/odbc/reference/odbc-programmer-s-reference)中提供了 odbc 所定義之傳回碼的其他相關資訊。

### <a name="error-codes-used-for-dao-exceptions"></a>用於 DAO 例外狀況的錯誤碼

若為 DAO 例外狀況，通常會提供詳細資訊。 您可以透過所攔截[CDaoException](reference/cdaoexception-class.md)物件的三個資料成員存取錯誤資訊：

- [m_pErrorInfo](reference/cdaoexception-class.md#m_perrorinfo)包含[CDaoErrorInfo](reference/cdaoerrorinfo-structure.md)物件的指標，它會將錯誤資訊封裝在與資料庫相關聯之錯誤物件的 DAO 集合中。

- [m_nAfxDaoError](reference/cdaoexception-class.md#m_nafxdaoerror)包含 MFC DAO 類別的擴充錯誤碼。 這些錯誤碼（具有**AFX_DAO_ERROR_XXX**格式的名稱）會記錄在的資料成員底下 `CDaoException` 。

- [m_scode](reference/cdaoexception-class.md#m_scode)包含來自 DAO 的 OLE **scode** （如果適用的話）。 不過，您很少需要使用這個錯誤碼。 在其他兩個資料成員中，通常會有更多的資訊。 如需**SCODE**值的詳細資訊，請參閱資料成員。

如需有關 DAO 錯誤、DAO 錯誤物件類型和 DAO 錯誤集合的其他資訊，請在 [類別[CDaoException](reference/cdaoexception-class.md)] 下找到。

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>資料庫例外狀況處理範例

下列範例會嘗試使用**new**運算子來建立堆積上的[CRecordset](reference/crecordset-class.md)衍生物件，然後開啟記錄集（針對 ODBC 資料來源）。 如需 DAO 類別的類似範例，請參閱下面的「DAO 例外狀況範例」。

### <a name="odbc-exception-example"></a>ODBC 例外狀況範例

[Open](reference/crecordset-class.md#open)成員函式可能會擲回例外狀況（針對 ODBC 類別的類型為[CDBException](reference/cdbexception-class.md) ），因此此程式碼會 `Open` 以**try**區塊括住呼叫。 後續的**catch**區塊將會攔截 `CDBException` 。 您可以檢查例外狀況物件本身，稱為 `e` ，但在此情況下，您必須知道建立記錄集的嘗試失敗。 **Catch**區塊會顯示訊息方塊，並藉由刪除記錄集物件來進行清除。

[!code-cpp[NVC_MFCDatabase#36](codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 例外狀況範例

DAO 範例類似于 ODBC 的範例，但您通常可以取得更多類型的資訊。 下列程式碼也會嘗試開啟記錄集。 如果該嘗試擲回例外狀況，您可以檢查例外狀況物件的資料成員是否有錯誤資訊。 如同先前的 ODBC 範例，可能已經足以知道建立記錄集的嘗試失敗。

[!code-cpp[NVC_MFCDatabase#37](codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此程式碼會從 exception 物件的[m_pErrorInfo](reference/cdaoexception-class.md#m_perrorinfo)成員取得錯誤訊息字串。 當它擲回例外狀況時，MFC 會填入這個成員。

如需物件所傳回錯誤資訊的討論 `CDaoException` ，請參閱類別[CDaoException](reference/cdaoexception-class.md)和[CDaoErrorInfo](reference/cdaoerrorinfo-structure.md)。

當您使用 Microsoft Jet （.mdb）資料庫，而且在大部分情況下，當您使用 ODBC 時，只會有一個錯誤物件。 當您使用 ODBC 資料來源，而且有多個錯誤時，在罕見的情況下，您可以根據[CDaoException：： GetErrorCount](reference/cdaoexception-class.md#geterrorcount)傳回的錯誤數目，在 DAO 的錯誤集合中執行迴圈。 每次透過迴圈，呼叫[CDaoException：： GetErrorInfo](reference/cdaoexception-class.md#geterrorinfo)以重新填滿 `m_pErrorInfo` 資料成員。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
