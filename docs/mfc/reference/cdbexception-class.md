---
title: "CDBException 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBException
dev_langs:
- C++
helpviewer_keywords:
- CDBException class
- exceptions [C++], database
- database exceptions [C++]
- ODBC classes [C++], exceptions
- errors [C++], database
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fc3bf7be273bf509dd1ee79fb42e69050070e830
ms.lasthandoff: 02/24/2017

---
# <a name="cdbexception-class"></a>CDBException 類別
表示資料庫類別引發的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|包含開放式資料庫連接 (ODBC) 傳回碼，型別的**RETCODE**。|  
|[CDBException::m_strError](#m_strerror)|包含在英數字元的詞彙描述錯誤的字串。|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|包含描述錯誤方面 ODBC 所傳回的錯誤碼的字串。|  
  
## <a name="remarks"></a>備註  
 類別包含兩個公用資料成員，您可以使用以判斷造成例外狀況，或顯示文字訊息，說明例外狀況。 `CDBException`物件的建構與資料庫類別的成員函式所擲回。  
  
> [!NOTE]
>  這個類別是其中一個 MFC 的開放式資料庫連接 (ODBC) 類別。 如果您改為使用較新的資料存取物件 (DAO) 類別，使用[CDaoException](../../mfc/reference/cdaoexception-class.md)改。 所有的 DAO 類別名稱有"CDao"做為前置詞。 如需詳細資訊，請參閱文章[概觀︰ 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 例外狀況會涉及外部程式的控制項，例如資料來源的狀況不正常執行的情況下，或網路 I/O 錯誤。 您可能會執行您的程式的正常過程中看到的錯誤通常不會視為例外狀況。  
  
 您可以存取這些物件的範圍內**攔截**運算式。 您也可以擲回`CDBException`物件從自己的程式碼與`AfxThrowDBException`全域函式。  
  
 如需有關的一般情況下，或將例外狀況處理`CDBException`物件，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[例外狀況︰ 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
##  <a name="a-namemnretcodea--cdbexceptionmnretcode"></a><a name="m_nretcode"></a>CDBException::m_nRetCode  
 包含型別的 ODBC 錯誤碼**RETCODE** ODBC 應用程式發展介面 (API) 函數所傳回。  
  
### <a name="remarks"></a>備註  
 這種類型包括 ODBC 所定義的固定 SQL、 錯誤碼和資料庫類別所定義的前置詞 AFX_SQL 為錯誤碼。 如`CDBException`，這個成員會包含下列值之一︰  
  
- **AFX_SQL_ERROR_API_CONFORMANCE**的驅動程式`CDatabase::OpenEx`或`CDatabase::Open`呼叫不符合必要的 ODBC API 的一致性層級 1 ( **SQL_OAC_LEVEL1**)。  
  
- **AFX_SQL_ERROR_CONNECT_FAIL**無法連線到資料來源。 您傳遞**NULL** `CDatabase`指標資料錄集建構函式和建立連接的後續嘗試根據`GetDefaultConnect`失敗。  
  
- **AFX_SQL_ERROR_DATA_TRUNCATED**要求超過您所提供的儲存體的資料。 如需增加提供的資料儲存體`CString`或`CByteArray`資料類型，請參閱`nMaxLength`引數[RFX_Text](http://msdn.microsoft.com/library/de3c7581-d26c-40cb-81f3-c492ef4809f6)和[RFX_Binary](http://msdn.microsoft.com/library/908ff945-3ad0-43a1-9932-cdcdc8b14915) 》 」 巨集和全域變數 」。  
  
- **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**呼叫`CRecordset::Open`要求動態集失敗。 動態集不支援驅動程式。  
  
- **AFX_SQL_ERROR_EMPTY_COLUMN_LIST**您嘗試開啟資料表 (或您提供給無法識別為程序呼叫或**選取**陳述式)，但沒有資料行中的資料錄欄位交換 (RFX) 函式呼叫中識別您`DoFieldExchange`覆寫。  
  
- **AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH** RFX 函式中的型別您`DoFieldExchange`覆寫與不相容資料錄集中的資料行資料類型。  
  
- **AFX_SQL_ERROR_ILLEGAL_MODE**您呼叫`CRecordset::Update`而無需先前呼叫`CRecordset::AddNew`或`CRecordset::Edit`。  
  
- **AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED**因為 ODBC 驅動程式不支援鎖定，無法完成您的要求鎖定記錄進行更新。  
  
- **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**您呼叫`CRecordset::Update`或**刪除**沒有唯一索引鍵的資料表和變更的多個資料錄。  
  
- **AFX_SQL_ERROR_NO_CURRENT_RECORD**您嘗試編輯或刪除先前刪除的記錄。 您必須在刪除後，捲動到新的目前記錄。  
  
- **AFX_SQL_ERROR_NO_POSITIONED_UPDATES**您的要求無法執行動態集，因為 ODBC 驅動程式不支援的定位更新。  
  
- **AFX_SQL_ERROR_NO_ROWS_AFFECTED**您呼叫`CRecordset::Update`或**刪除**，但操作開始時找不到記錄。  
  
- **AFX_SQL_ERROR_ODBC_LOAD_FAILED**嘗試載入 ODBC。DLL 失敗;Windows 找不到或無法載入此 DLL。 此錯誤是嚴重威脅。  
  
- **AFX_SQL_ERROR_ODBC_V2_REQUIRED**無法完成您要求的動態集，因為有需要的層級 2 相容 ODBC 驅動程式。  
  
- **AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY**捲動的嘗試失敗，因為資料來源不支援向後捲動。  
  
- **AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED**呼叫`CRecordset::Open`要求快照集失敗。 驅動程式不支援快照集。 (這應該只會發生時 ODBC 資料指標程式庫 â €"ODBCCURS。DLL â €"不存在）。  
  
- **AFX_SQL_ERROR_SQL_CONFORMANCE**的驅動程式`CDatabase::OpenEx`或`CDatabase::Open`呼叫不符合必要的 「 最低 」 的 ODBC SQL 一致性層級 ( **SQL_OSC_MINIMUM**)。  
  
- **AFX_SQL_ERROR_SQL_NO_TOTAL** ODBC 驅動程式無法將指定的大小總計`CLongBinary`資料值。 作業可能失敗，因為預先未配置全域記憶體區塊。  
  
- **AFX_SQL_ERROR_RECORDSET_READONLY**您嘗試更新唯讀的資料錄集或資料來源為唯讀。 資料錄集可以執行任何更新作業或`CDatabase`相關聯的物件。  
  
- **SQL_ERROR**函式失敗。 ODBC 函數所傳回的錯誤訊息**SQLError**會儲存在**m_strError**資料成員。  
  
- **SQL_INVALID_HANDLE**函式失敗，因為無效的環境控制代碼、 連接控制代碼或陳述式控制代碼。 這會指出程式設計錯誤。 沒有其他資訊可從 ODBC 函數**SQLError**。  
  
 ODBC 所定義的 SQL 前置碼。 AFX 前置詞的程式碼會定義在 AFXDB。H、 MFC\INCLUDE 中找到。  
  
##  <a name="a-namemstrerrora--cdbexceptionmstrerror"></a><a name="m_strerror"></a>CDBException::m_strError  
 包含字串，描述造成例外狀況的錯誤。  
  
### <a name="remarks"></a>備註  
 字串會描述錯誤以英數字元表示。 如需詳細資訊和範例，請參閱**m_strStateNativeOrigin**。  
  
##  <a name="a-namemstrstatenativeorigina--cdbexceptionmstrstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>CDBException::m_strStateNativeOrigin  
 包含字串，描述造成例外狀況的錯誤。  
  
### <a name="remarks"></a>備註  
 字串為表單 」 狀態: %s，原生: %ld，來源: %s"，其中描述的值來取代的格式化程式碼，依序︰  
  
-   **SQLSTATE**、 以 null 結束的字串，包含五個字元碼傳回於*szSqlState* ODBC 函式參數的**SQLError**。 **SQLSTATE**值會列在 < 附錄 A， [ODBC 錯誤碼](https://msdn.microsoft.com/library/ms714687.aspx)，請在*ODBC 程式設計人員參考*。 範例: 「 S0022 」。  
  
-   原生錯誤特定的程式碼，資料來源，傳回*pfNativeError*參數**SQLError**函式。 範例︰ 207。  
  
-   錯誤訊息文字中傳回*szErrorMsg*參數**SQLError**函式。 此訊息包含數個括號括住的名稱。 當錯誤從其來源傳遞給使用者時，每個 ODBC 元件 （驅動程式、 驅動程式管理員中的 資料來源） 將附加自己的名稱。 這項資訊有助於找出錯誤的來源。 範例: [Microsoft] [ODBC SQL Server Driver] [SQL Server]  
  
 架構會將錯誤字串解譯，並放入其元件**m_strStateNativeOrigin**; 如果**m_strStateNativeOrigin**包含的資訊對於多個錯誤，錯誤會以換行分隔。 架構英數字元的錯誤將文字放入**m_strError**。  
  
 如需用來構成這個字串的程式碼的詳細資訊，請參閱[SQLError](https://msdn.microsoft.com/library/ms716312.aspx)函式中*ODBC 程式設計人員參考*。  
  
### <a name="example"></a>範例  
  從 ODBC: 「 狀態︰ S0022，原生︰&207;，原始: [Microsoft] [ODBC SQL Server Driver] [SQL Server] 無效的資料行名稱 'ColName' 」  
  
 在**m_strStateNativeOrigin**: 「 狀態︰ S0022，原生︰&207;，原始: [Microsoft] [ODBC SQL Server Driver] [SQL Server] 」  
  
 在**m_strError**: 「 無效的資料行名稱 'ColName' 」  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [CException 類別](../../mfc/reference/cexception-class.md)

