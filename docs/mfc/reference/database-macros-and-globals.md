---
title: 資料庫巨集和全域
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 0dc53bce8b43677e7fe0aa1787d1adcc16a560c4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837523"
---
# <a name="database-macros-and-globals"></a>資料庫巨集和全域

以下所列的巨集和全域資料適用於採用 ODBC 的資料庫應用程式。 它們不適用於採用 DAO 的應用程式。

在 MFC 4.2 之前，巨集 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 為非同步作業提供一個產生時間給其他處理序的機會。 從 MFC 4.2 開始，因為 MFC ODBC 類別只使用同步作業，因此已變更這些巨集的實作。 巨集 `AFX_ODBC_CALL` 是 MFC 4.2 的新增功能。

### <a name="database-macros"></a>資料庫巨集

|名稱|描述|
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|呼叫傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。 `AFX_ODBC_CALL` 將會重複呼叫函式，直到它不再傳回 `SQL_STILL_EXECUTING`。|
|[AFX_SQL_ASYNC](#afx_sql_async)|呼叫 `AFX_ODBC_CALL`。|
|[AFX_SQL_SYNC](#afx_sql_sync)|呼叫不傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。|

### <a name="database-globals"></a>資料庫全域

|名稱|描述|
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|新增動態連結至 MFC 之一般 MFC DLL 的資料庫支援。|
|[AfxGetHENV](#afxgethenv)|擷取目前正在由 MFC 使用的 ODBC 環境控制代碼。 您可以直接呼叫 ODBC 時使用這個控制代碼。|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a> AfxDbInitModule

若為 MFC 資料庫 (或 DAO) 支援從動態連結至 MFC 的標準 MFC DLL，請在您的一般 MFC DLL 函式中加入此函數的呼叫， `CWinApp::InitInstance` 以初始化 MFC 資料庫 DLL。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>備註

請確定此呼叫是在任何基類呼叫之前發生，或是任何可存取 MFC 資料庫 DLL 的已加入程式碼之前。 MFC 資料庫 DLL 是 MFC 擴充 DLL;為了讓 MFC 擴充 DLL 能夠進入 `CDynLinkLibrary` 鏈中，它必須 `CDynLinkLibrary` 在將使用它的每個模組的內容中建立物件。 `AfxDbInitModule``CDynLinkLibrary`在您的一般 MFC dll 內容中建立物件，使其成為 `CDynLinkLibrary` 一般 mfc dll 的物件鏈。

### <a name="requirements"></a>規格需求

**標頭：**\<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a> AFX_ODBC_CALL

使用這個宏來呼叫任何可能會傳回的 ODBC API 函數 `SQL_STILL_EXECUTING` 。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 如需 ODBC API 函式的詳細資訊，請參閱 Windows SDK。

### <a name="remarks"></a>備註

`AFX_ODBC_CALL` 重複呼叫函數，直到它不再傳回為止 `SQL_STILL_EXECUTING` 。

在叫 `AFX_ODBC_CALL` 用之前，您必須宣告 `nRetCode` 類型為 RETCODE 的變數。

請注意，MFC ODBC 類別現在只會使用同步處理。 您必須呼叫 ODBC API 函數，才能執行非同步作業 `SQLSetConnectOption` 。 如需詳細資訊，請參閱 Windows SDK 中的「以非同步方式執行函數」主題。

### <a name="example"></a>範例

這個範例會使用來呼叫 ODBC API 函式，此函式會傳回 `AFX_ODBC_CALL` `SQLColumns` 以命名之資料表中的資料行清單 `strTableName` 。 請注意的宣告 `nRetCode` ，以及使用記錄集資料成員將參數傳遞給函式的功能。 此範例也會說明如何使用類別的成員函式來檢查呼叫的結果 `Check` `CRecordset` 。 變數 `prs` 是物件的指標，其宣告于 `CRecordset` 其他位置。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afxdb.h。h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a> AFX_SQL_ASYNC

在 MFC 4.2 變更這個巨集實作。

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>參數

*pr*<br/>
`CRecordset` 物件或 `CDatabase` 物件指標。 從 MFC 4.2 開始略過這個參數值。

*SQLFunc*<br/>
ODBC API 函式。 如需 ODBC API 函式的詳細資訊，請參閱 Windows SDK。

### <a name="remarks"></a>備註

`AFX_SQL_ASYNC` 只要呼叫宏 [AFX_ODBC_CALL](#afx_odbc_call) ，就會忽略 *pr* 參數。 在 MFC 4.2 之前的版本中，`AFX_SQL_ASYNC` 是用來呼叫可能傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。 如果 ODBC API 函式確實傳回 `SQL_STILL_EXECUTING`，則 `AFX_SQL_ASYNC` 會呼叫 `prs->OnWaitForDataSource`。

> [!NOTE]
> MFC ODBC 類別現在只會使用同步處理。 您必須呼叫 ODBC API 函數，才能執行非同步作業 `SQLSetConnectOption` 。 如需詳細資訊，請參閱 Windows SDK 中的「以非同步方式執行函數」主題。

### <a name="requirements"></a>規格需求

  **標頭** afxdb.h。h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a> AFX_SQL_SYNC

`AFX_SQL_SYNC`宏只會呼叫函數 `SQLFunc` 。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 如需這些函數的詳細資訊，請參閱 Windows SDK。

### <a name="remarks"></a>備註

使用這個宏來呼叫不會傳回的 ODBC API 函數 `SQL_STILL_EXECUTING` 。

在呼叫之前 `AFX_SQL_SYNC` ，您必須宣告類型為 `nRetCode` RETCODE 的變數。 您可以在 `nRetCode` 宏呼叫之後檢查的值。

請注意，在 `AFX_SQL_SYNC` MFC 4.2 中的實作為變更。 因為不再需要檢查伺服器狀態， `AFX_SQL_SYNC` 只要將值指派給 `nRetCode` 。 例如，而不是進行呼叫

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

您可以直接進行指派

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxdb.h。h

## <a name="afxgethenv"></a><a name="afxgethenv"></a> AfxGetHENV

您可以在直接 ODBC 呼叫中使用傳回的控制碼，但您不能關閉控制碼，或假設控制碼仍然有效，而且在終結任何現有或衍生的物件之後，就可以使用此控制碼 `CDatabase` `CRecordset` 。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>傳回值

MFC 目前正在使用的 ODBC 環境控制碼。 如果沒有 `SQL_HENV_NULL` [CDatabase](../../mfc/reference/cdatabase-class.md) 物件，且沒有 [CRecordset](../../mfc/reference/crecordset-class.md) 物件正在使用中，則可以是。

### <a name="requirements"></a>規格需求

  **標頭** afxdb.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
