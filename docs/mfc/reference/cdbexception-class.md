---
title: CDBException 類別
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 1ab7daeb3af55c92985c951c632b1d4050681474
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321898"
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
|[國開行例外:m_nRetCode](#m_nretcode)|包含 OPEN 資料庫連接 (ODBC) 傳回代碼,類型為 RETCODE。|
|[國開行例外:m_strError](#m_strerror)|包含用字母數位描述錯誤的字串。|
|[國開行例外::m_strStateNativeOrigin](#m_strstatenativeorigin)|包含一個字串,描述 ODBC 傳回的錯誤代碼方面的錯誤。|

## <a name="remarks"></a>備註

該類包括兩個公共數據成員,可用於確定異常的原因或顯示描述異常的文本消息。 `CDBException`對象由資料庫類的成員函數構造和引發。

> [!NOTE]
> 此類是 MFC 的開放資料庫連接 (ODBC) 類之一。 如果您改用較新的資料存取物件 (DAO) 類別,請使用[CDaoException。](../../mfc/reference/cdaoexception-class.md) 所有 DAO 類名稱都以「CDao」為首碼。 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

例外情況是涉及程式控制之外的條件(如數據源或網路 I/O 錯誤)的異常執行情況。 在程式執行的正常過程中,您可能期望看到的錯誤通常不被視為例外。

您可以在**CATCH**表達式的範圍內訪問這些物件。 還可以使用`AfxThrowDBException`全域函數`CDBException`從您自己的代碼中引發物件。

有關常規異常處理或`CDBException`對象的詳細資訊,請參閱[文章"異常處理 "(MFC)](../../mfc/exception-handling-in-mfc.md)和["例外:資料庫例外](../../mfc/exceptions-database-exceptions.md)"。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a>國開行例外:m_nRetCode

包含由 ODBC 應用程式編程介面 (API) 函數傳回的 RETCODE 類型的 ODBC 錯誤代碼。

### <a name="remarks"></a>備註

此類型包括由 ODBC 定義的 SQL 首碼和資料庫類定義的AFX_SQL預碼碼。 對於`CDBException`,此成員將包含以下值之一:

- AFX_SQL_ERROR_API_CONFORMANCE`CDatabase::OpenEx``CDatabase::Open`或呼叫的驅動程式不符合所需的 ODBC API 符合性級別 1(SQL_OAC_LEVEL1)。

- AFX_SQL_ERROR_CONNECT_FAIL連接到數據源失敗。 您將 NULL`CDatabase`指標傳遞給記錄集建構函數,並隨後嘗試`GetDefaultConnect`基於 失敗建立連接。

- AFX_SQL_ERROR_DATA_TRUNCATED您請求的數據多於您提供的存儲。 有關`CString`增加為`CByteArray`或類型提供的數據存儲的資訊,請參閱`nMaxLength`"宏和全域"下[RFX_Text](record-field-exchange-functions.md#rfx_text)和[RFX_Binary](record-field-exchange-functions.md#rfx_binary)的參數。

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED請求`CRecordset::Open`發電機的呼叫失敗。 驅動程式不支援動態集。

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST您嘗試打開表(或您提供的內容無法標識為過程調用或**SELECT**語句),但在`DoFieldExchange`重寫中記錄欄位交換 (RFX) 函數調用中未標識列。

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH`DoFieldExchange`重寫中的 RFX 函數的類型與記錄集中的列數據類型不相容。

- AFX_SQL_ERROR_ILLEGAL_MODE您之前`CRecordset::Update`沒有`CRecordset::AddNew`打電話`CRecordset::Edit`或 。

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED無法滿足鎖定更新記錄的請求,因為 ODBC 驅動程式不支援鎖定。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED您調用`CRecordset::Update``Delete`的 表或沒有唯一鍵並更改了多個記錄的表。

- AFX_SQL_ERROR_NO_CURRENT_RECORD您嘗試編輯或刪除以前刪除的記錄。 刪除後,必須滾動到新的當前記錄。

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES無法滿足您對動態集的請求,因為 ODBC 驅動程式不支援定位更新。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED您調用`CRecordset::Update``Delete`或 ,但操作開始時,找不到記錄。

- AFX_SQL_ERROR_ODBC_LOAD_FAILED嘗試載入 ODBC。DLL 失敗;Windows 找不到或無法載入此 DLL。 此錯誤是致命的。

- AFX_SQL_ERROR_ODBC_V2_REQUIRED由於需要符合 2 級的 ODBC 驅動程式,因此無法滿足對動態集的請求。

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY 嘗試滾動失敗,因為數據源不支援向後滾動。

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED請求`CRecordset::Open`快照的調用失敗。 驅動程式不支援快照。 (僅當 ODBC 游標庫 ODBCCURS 時,才應發生這種情況。DLL 不存在。

- AFX_SQL_ERROR_SQL_CONFORMANCE`CDatabase::OpenEx``CDatabase::Open`或調用的驅動程式不符合所需的 ODBC SQL 符合性級別"最小值"(SQL_OSC_MINIMUM)。

- AFX_SQL_ERROR_SQL_NO_TOTAL ODBC 驅動程式`CLongBinary`無法指定 資料值的總大小。 操作可能失敗,因為無法預分配全域記憶體區塊。

- AFX_SQL_ERROR_RECORDSET_READONLY您嘗試更新唯讀記錄集,或者資料源是唯讀的。 不能對記錄集或其關聯的`CDatabase`物件執行更新操作。

- SQL_ERROR 功能失敗。 ODBC 函`SQLError`數傳回的錯誤訊息儲存在資料`m_strError`成員中 。

- SQL_INVALID_HANDLE功能由於環境句柄、連接句柄或語句句柄無效而失敗。 這表示程式設計錯誤。 ODBC 函`SQLError`數 沒有其他資訊。

SQL 預置碼由 ODBC 定義。 AFX 首碼在 AFXDB 中定義。H,在 MFC_INCLUDE 中找到。

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a>國開行例外:m_strError

包含描述導致異常的錯誤的字串。

### <a name="remarks"></a>備註

字串用字母數字術語描述錯誤。 有關詳細資訊和範例,請參閱`m_strStateNativeOrigin`。

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a>國開行例外::m_strStateNativeOrigin

包含描述導致異常的錯誤的字串。

### <a name="remarks"></a>備註

字串的形式是「狀態:%s,本機:%ld,原點:%s」,其中格式代碼按順序替換為描述:

- SQLSTATE,一個空端端字串,其中包含在 ODBC 函`SQLError`數 的*szSqlState*參數中返回的五個字元錯誤代碼。 SQLSTATE 值列在附錄[A,ODBC 錯誤代碼](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes),在*ODBC 程式設計師的參考*中。 示例:「S0022」。。

- 特定於數據源的本機錯誤代碼在`SQLError`函數的*pfNativeError*參數中返回。 例如:207。

- 在`SQLError`函數的*szErrorMsg*參數中傳回的錯誤訊息文本。 此消息由多個括弧內的名稱組成。 當錯誤從源傳遞給使用者時,每個 ODBC 元件(數據源、驅動程式、驅動程式管理員)都會追加其自己的名字。 此資訊有助於確定錯誤的來源。 範例: [微軟][ODBC SQL 伺服器驅動程式][SQL 伺服器]

框架解釋錯誤字串並將其元件放入`m_strStateNativeOrigin`中。如果`m_strStateNativeOrigin`包含多個錯誤的資訊,則錯誤由換行分隔。 框架將字母數字錯誤文字移`m_strError`入 。

有關用於組成此字串的代碼的其他資訊,請參閱*ODBC 程式員參考*中的[SQLError](/sql/odbc/reference/syntax/sqlerror-function)函數。

### <a name="example"></a>範例

從 ODBC:"狀態:S0022,本機:207,原\[點\[:微軟 ] ODBC SQL\[伺服器驅動程式* SQL 伺服器* 無效列名稱"ColName"

在`m_strStateNativeOrigin`: "狀態:S0022,本機\[:207,\[原點 :\[微軟] ODBC SQL 伺服器驅動程式* SQL 伺服器*"

在`m_strError`: "無效列名稱 'ColName'"

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange 類別](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::更新](../../mfc/reference/crecordset-class.md#update)<br/>
[C記錄集::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
