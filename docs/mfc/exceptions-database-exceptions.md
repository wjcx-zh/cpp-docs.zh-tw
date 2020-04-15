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
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366619"
---
# <a name="exceptions-database-exceptions"></a>例外狀況：資料庫例外狀況

本文介紹如何處理資料庫異常。 無論使用開放資料庫連接 (ODBC) 的 MFC 類還是數據訪問物件 (DAO) 的 MFC 類,本文中的大多數材料都適用。 特定於一個或另一個模型的材料被顯式標記。 主題包括：

- [例外處理方法](#_core_approaches_to_exception_handling)

- [資料庫例外處理範例](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>例外處理方法

無論您是使用 DAO(過時)還是 ODBC,這種方法都是一樣的。

應始終編寫異常處理程序來處理異常條件。

捕獲資料庫異常的最實用方法是使用異常方案測試應用程式。 確定代碼中操作可能發生的異常,並強制發生異常。 然後檢查跟蹤輸出以查看引發哪些異常,或檢查調試器中返回的錯誤資訊。 這樣,您就可以知道您將為正在使用的異常方案看到哪些返回代碼。

### <a name="error-codes-used-for-odbc-exceptions"></a>用於 ODBC 例外的錯誤程式碼

除了框架定義的返回代碼(其中**具有AFX_SQL_ERROR_XXX表單**的名稱外,某些[CDB例外](../mfc/reference/cdbexception-class.md)代碼基於[ODBC](../data/odbc/odbc-basics.md)回郵代碼。 此類異常的返回代碼**具有SQL_ERROR_XXX窗體**的名稱。

資料庫類可以返回的返回代碼(無論是框架定義的代碼還是定義ODBC的代碼)都記錄在`CDBException`類[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)資料成員下。 有關 ODBC 定義的傳回程式的其他資訊,請參考 MSDN 函式庫中的 ODBC SDK*程式者參考*。

### <a name="error-codes-used-for-dao-exceptions"></a>用於 DAO 例外的錯誤代碼

對於 DAO 異常,詳細資訊通常可用。 您可以透過擷取的[CDaoException](../mfc/reference/cdaoexception-class.md)物件的三個資料成員存取錯誤資訊:

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含指向[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)物件的指標,該物件將錯誤資訊封裝在 DAO 與資料庫關聯的錯誤物件集合中。

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含來自 MFC DAO 類的擴充錯誤代碼。 這些錯誤代碼**AFX_DAO_ERROR_XXX窗體的名稱**,`CDaoException`在 中 的數據成員下記錄。

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 DAO 的 OLE **SCODE(** 如果適用)。 但是,您很少需要使用此錯誤代碼。 通常,其他兩個數據成員中提供了更多資訊。 有關**SCODE**值的更多,請參閱數據成員。

有關 DAO 錯誤、DAO 錯誤物件類型和 DAO 錯誤集合的其他資訊可在類[CDaoException](../mfc/reference/cdaoexception-class.md)下提供。

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>資料庫例外處理範例

下面的範例嘗試使用**新**運算元在堆上建構[CRecordset](../mfc/reference/crecordset-class.md)派生物件,然後打開記錄集(對於 ODBC 資料源)。 有關 DAO 類的類似範例,請參閱下面的「DAO 異常示例」。

### <a name="odbc-exception-example"></a>ODBC 例外樣範例

[Open](../mfc/reference/crecordset-class.md#open)成員函數可能會引發異常(ODBC 類的[CDBException](../mfc/reference/cdbexception-class.md)類型),`Open`因此此代碼使用**try**塊將調用括在一起。 後續**catch**區塊`CDBException`將擷取 。 您可以檢查名為`e`的異常物件本身,但在這種情況下,它足以知道創建記錄集的嘗試已失敗。 **catch**塊顯示一個消息框,並通過刪除記錄集物件進行清理。

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 例外樣範例

DAO 範例與 ODBC 的範例類似,但通常可以檢索更多類型的資訊。 以下代碼還嘗試打開記錄集。 如果該嘗試引發異常,則可以檢查異常對象的數據成員以查找錯誤資訊。 與前面的 ODBC 示例一樣,可能足以知道創建記錄集的嘗試失敗。

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此代碼從異常物件的[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)成員獲取錯誤訊息字串。 MFC 在引發異常時填充此成員。

有關`CDaoException`物件傳回的錯誤資訊的討論,請參閱[類別 CDaoexception](../mfc/reference/cdaoexception-class.md)和[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。

當您使用 Microsoft Jet (.mdb) 資料庫時,在大多數情況下,當您使用 ODBC 時,將只有一個錯誤物件。 在極少數情況下,當您使用 ODBC 資料來源且存在多個錯誤時,您可以根據 CDaoException 傳回的錯誤數循環存取 DAO 的錯誤集合[:::getErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 每次通過迴圈時,調用[CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)以重新`m_pErrorInfo`填充 數據成員。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
