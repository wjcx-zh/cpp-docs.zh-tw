---
title: CDBException 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
dev_langs:
- C++
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e67dec2474d89e3daccf0bc0e59332c79080cc99
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538416"
---
# <a name="cdbexception-class"></a>CDBException 類別
表示資料庫類別引發的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
class CDBException : public CException  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDBException::m_nRetCode](#m_nretcode)|包含開放式資料庫連接 (ODBC) 傳回碼，型別 RETCODE。|  
|[CDBException::m_strError](#m_strerror)|包含在英數字元的詞彙描述錯誤的字串。|  
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|包含描述錯誤方面 ODBC 所傳回的錯誤碼字串。|  
  
## <a name="remarks"></a>備註  
 類別包含兩個公用資料成員，您可以使用以判斷造成例外狀況，或顯示描述例外狀況的文字訊息。 `CDBException` 物件是建構，而且資料庫類別的成員函式所擲回。  
  
> [!NOTE]
>  這個類別是其中一個 MFC 的開放式資料庫連接 (ODBC) 類別。 如果您改為使用較新的資料存取物件 (DAO) 類別，使用[CDaoException](../../mfc/reference/cdaoexception-class.md)改。 所有的 DAO 類別名稱有"CDao 」 做為前置詞。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 例外狀況會涉及外部程式的控制項，例如資料來源的條件不正常執行的情況下，或網路 I/O 錯誤。 您可能會在執行程式的正常過程中看到的錯誤通常不考慮例外狀況。  
  
 您可以存取這些物件的範圍內**攔截**運算式。 您也可以擲回`CDBException`從您自己的程式碼的物件`AfxThrowDBException`全域函式。  
  
 如需詳細資訊，在一般情況下，或將處理的例外狀況的相關`CDBException`物件，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)並[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDBException`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdb.h  
  
##  <a name="m_nretcode"></a>  CDBException::m_nRetCode  
 包含 ODBC 錯誤碼 RETCODE ODBC 應用程式設計介面 (API) 函數所傳回的型別。  
  
### <a name="remarks"></a>備註  
 這種類型包括 ODBC 所定義的 SQL 前置碼和資料庫類別所定義的 AFX_SQL 前置碼。 針對`CDBException`，這個成員會包含下列值之一：  
  
- AFX_SQL_ERROR_API_CONFORMANCE 驅動程式針對`CDatabase::OpenEx`或`CDatabase::Open`呼叫不符合必要的 ODBC API 一致性層級 1 (SQL_OAC_LEVEL1)。  
  
- 資料來源的 AFX_SQL_ERROR_CONNECT_FAIL 連接失敗。 傳遞 NULL`CDatabase`指標資料錄集建構函式和建立連接的後續嘗試根據`GetDefaultConnect`失敗。  
  
- AFX_SQL_ERROR_DATA_TRUNCATED 您要求超過您所提供的儲存體的資料。 如需增加提供的資料儲存體`CString`或`CByteArray`資料類型，請參閱`nMaxLength`引數[RFX_Text](record-field-exchange-functions.md#rfx_text)並[RFX_Binary](record-field-exchange-functions.md#rfx_binary)下 」 巨集和全域變數。 」  
  
- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED A 呼叫`CRecordset::Open`要求動態集失敗。 動態集不支援驅動程式。  
  
- AFX_SQL_ERROR_EMPTY_COLUMN_LIST 您嘗試開啟資料表 (或您提供給無法辨識為程序呼叫或**選取**陳述式)，但沒有資料錄欄位交換 (RFX) 函式呼叫中所識別的資料行您`DoFieldExchange`覆寫。  
  
- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH RFX 的型別仍可在您`DoFieldExchange`覆寫與不相容的資料錄集中的資料行資料類型。  
  
- AFX_SQL_ERROR_ILLEGAL_MODE 您呼叫`CRecordset::Update`而不需要先前呼叫`CRecordset::AddNew`或`CRecordset::Edit`。  
  
- 無法完成 AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED 更新鎖定記錄的要求，因為您的 ODBC 驅動程式不支援鎖定。  
  
- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED 您呼叫`CRecordset::Update`或`Delete`沒有唯一的索引鍵的資料表和變更多筆記錄。  
  
- AFX_SQL_ERROR_NO_CURRENT_RECORD 您嘗試編輯或刪除先前刪除的記錄。 在刪除後，您必須捲動至新的目前資料錄。  
  
- 無法完成您要求的動態集，因為您的 ODBC 驅動程式不支援的 AFX_SQL_ERROR_NO_POSITIONED_UPDATES 定點更新。  
  
- AFX_SQL_ERROR_NO_ROWS_AFFECTED 您呼叫`CRecordset::Update`或`Delete`，但作業開始時找不到記錄。  
  
- AFX_SQL_ERROR_ODBC_LOAD_FAILED 嘗試載入 ODBC。DLL 失敗;Windows 找不到或無法載入此 DLL。 此錯誤是嚴重威脅。  
  
- AFX_SQL_ERROR_ODBC_V2_REQUIRED 無法完成您要求的動態集，因為的層級 2 相容的 ODBC 驅動程式為必要項。  
  
- 因為資料來源不支援向後捲動 AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY 捲動嘗試不成功。  
  
- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED A 呼叫`CRecordset::Open`要求快照集失敗。 快照集不支援驅動程式。 (這應該只會發生時的 ODBC 資料指標程式庫 ODBCCURS。DLL 不存在）。  
  
- AFX_SQL_ERROR_SQL_CONFORMANCE 驅動程式針對`CDatabase::OpenEx`或`CDatabase::Open`呼叫不符合必要的 「 最低 」 (SQL_OSC_MINIMUM) 的 ODBC SQL 一致性層級。  
  
- AFX_SQL_ERROR_SQL_NO_TOTAL ODBC 驅動程式找不到指定的大小總計`CLongBinary`資料值。 作業可能失敗，因為預先不配置全域記憶體區塊。  
  
- AFX_SQL_ERROR_RECORDSET_READONLY 您嘗試更新唯讀的資料錄集或資料來源是唯讀的。 資料錄集可以執行任何更新作業或`CDatabase`與其相關聯的物件。  
  
- SQL_ERROR 函式失敗。 ODBC 函式所傳回的錯誤訊息`SQLError`會儲存在`m_strError`資料成員。  
  
- SQL_INVALID_HANDLE 函式失敗，因為無效的環境控制代碼、 連接控制代碼或陳述式控制代碼。 這會指出程式設計錯誤。 沒有其他資訊可從 ODBC 函數`SQLError`。  
  
 ODBC 所定義的 SQL 前置碼。 AFX 前面的程式碼會定義在 AFXDB。H、 MFC\INCLUDE 中找到。  
  
##  <a name="m_strerror"></a>  CDBException::m_strError  
 包含字串，描述造成例外狀況的錯誤。  
  
### <a name="remarks"></a>備註  
 字串會描述錯誤以英數字元的表示。 如需詳細資訊和範例，請參閱`m_strStateNativeOrigin`。  
  
##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin  
 包含字串，描述造成例外狀況的錯誤。  
  
### <a name="remarks"></a>備註  
 字串為形式 」 狀態: %s，原生: %ld，來源: %s"，其中的格式化程式碼，依序會取代的值，描述：  
  
-   在傳回的 SQLSTATE、 null 結束的字串，包含五個字元的錯誤碼*szSqlState*參數的 ODBC 函數`SQLError`。 SQLSTATE 值會列在附錄 A [ODBC 錯誤碼](/previous-versions/windows/desktop/ms714687\(v=vs.85\))，請在*ODBC 程式設計人員參考*。 範例:"S0022 」。  
  
-   中的原生錯誤特有的程式碼，資料來源，傳回*pfNativeError*參數`SQLError`函式。 範例： 207。  
  
-   傳回的錯誤訊息文字*szErrorMsg*參數`SQLError`函式。 此訊息是由數個以括弧括住的名稱所組成。 因為錯誤從其來源傳遞給使用者，每個 ODBC 元件 （驅動程式、 驅動程式管理員中的 資料來源） 將附加自己的名稱。 這項資訊可協助找出錯誤的來源。 範例: [Microsoft] [SQL Server Driver] [SQL Server]  
  
 架構會將錯誤字串解譯，並將其元件`m_strStateNativeOrigin`; 如果`m_strStateNativeOrigin`包含資訊的多個錯誤，錯誤會以換行符號分隔。 架構對英數字元的錯誤文字`m_strError`。  
  
 如需用來構成這個字串的程式碼的詳細資訊，請參閱[SQLError](/previous-versions/windows/desktop/ms716312\(v=vs.85\))函式中*ODBC 程式設計人員參考*。  
  
### <a name="example"></a>範例  
  從 ODBC: 「 狀態： S0022，原生： 207，來源: [Microsoft] [SQL Server Driver] [SQL Server] 資料行名稱無效 'ColName' 」  
  
 在`m_strStateNativeOrigin`: 「 狀態： S0022，原生： 207，來源: [Microsoft] [SQL Server Driver] [SQL Server] 」  
  
 在  `m_strError`: 「 無效的資料行名稱 'ColName' 」  
  
## <a name="see-also"></a>另請參閱  
 [CException 類別](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::Update](../../mfc/reference/crecordset-class.md#update)   
 [CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)   
 [CException 類別](../../mfc/reference/cexception-class.md)
