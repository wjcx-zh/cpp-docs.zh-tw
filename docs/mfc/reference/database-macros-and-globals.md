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
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420838"
---
# <a name="database-macros-and-globals"></a>資料庫巨集和全域

以下所列的巨集和全域資料適用於採用 ODBC 的資料庫應用程式。 它們不適用於採用 DAO 的應用程式。

在 MFC 4.2 之前，巨集 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 為非同步作業提供一個產生時間給其他處理序的機會。 從 MFC 4.2 開始，因為 MFC ODBC 類別只使用同步作業，因此已變更這些巨集的實作。 巨集 `AFX_ODBC_CALL` 是 MFC 4.2 的新增功能。

### <a name="database-macros"></a>資料庫巨集

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|呼叫傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。 `AFX_ODBC_CALL` 將會重複呼叫函式，直到它不再傳回 `SQL_STILL_EXECUTING`。|
|[AFX_SQL_ASYNC](#afx_sql_async)|呼叫 `AFX_ODBC_CALL`。|
|[AFX_SQL_SYNC](#afx_sql_sync)|呼叫不傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。|

### <a name="database-globals"></a>資料庫全域

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|針對動態連結至 MFC 的一般 MFC DLL，加入資料庫支援。|
|[AfxGetHENV](#afxgethenv)|擷取目前正在由 MFC 使用的 ODBC 環境控制代碼。 您可以直接呼叫 ODBC 時使用這個控制代碼。|

## <a name="afxdbinitmodule"></a>AfxDbInitModule

若為 MFC 資料庫（或 DAO）支援來自動態連結至 MFC 的標準 MFC DLL，請在您的一般 MFC DLL 的 `CWinApp::InitInstance` 函式中新增對此函式的呼叫，以初始化 MFC 資料庫 DLL。

### <a name="syntax"></a>語法

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>備註

請確定這個呼叫發生在任何基類呼叫之前，或任何存取 MFC 資料庫 DLL 的已加入程式碼之前。 MFC 資料庫 DLL 是 MFC 延伸 DLL;為了讓 MFC 延伸模組 DLL 可以連接到 `CDynLinkLibrary` 鏈，它必須在每個將使用它的模組內容中，建立一個 `CDynLinkLibrary` 物件。 `AfxDbInitModule` 會在您的一般 MFC DLL 內容中建立 `CDynLinkLibrary` 物件，讓它能夠連接到正則 MFC DLL 的 `CDynLinkLibrary` 物件鏈。

### <a name="requirements"></a>需求

**標頭：** \<afxdll_ .h >

##  <a name="afx_odbc_call"></a>AFX_ODBC_CALL

使用此宏呼叫可能會傳回 `SQL_STILL_EXECUTING`的任何 ODBC API 函式。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 如需 ODBC API 函式的詳細資訊，請參閱 Windows SDK。

### <a name="remarks"></a>備註

`AFX_ODBC_CALL` 重複呼叫函式，直到不再傳回 `SQL_STILL_EXECUTING`為止。

叫用 `AFX_ODBC_CALL`之前，您必須宣告 RETCODE 類型的變數 `nRetCode`。

請注意，MFC ODBC 類別現在只會使用同步處理。 若要執行非同步作業，您必須呼叫 ODBC API 函數 `SQLSetConnectOption`。 如需詳細資訊，請參閱 Windows SDK 中的「非同步執行函式」主題。

### <a name="example"></a>範例

這個範例會使用 `AFX_ODBC_CALL` 來呼叫 `SQLColumns` ODBC API 函式，此函式會傳回資料表中的資料行清單（由 `strTableName`命名）。 請注意 `nRetCode` 的宣告和記錄集資料成員的使用，以將參數傳遞至函式。 此範例也說明如何使用 `Check`（`CRecordset`類別的成員函式）來檢查呼叫的結果。 變數 `prs` 是 `CRecordset` 物件的指標，在其他地方宣告。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>需求

**標頭：** afxdb。h

##  <a name="afx_sql_async"></a>AFX_SQL_ASYNC

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

`AFX_SQL_ASYNC` 只會呼叫宏[AFX_ODBC_CALL](#afx_odbc_call)並忽略*pr*參數。 在 MFC 4.2 之前的版本中，`AFX_SQL_ASYNC` 是用來呼叫可能傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。 如果 ODBC API 函式確實傳回 `SQL_STILL_EXECUTING`，則 `AFX_SQL_ASYNC` 會呼叫 `prs->OnWaitForDataSource`。

> [!NOTE]
>  MFC ODBC 類別現在只會使用同步處理。 若要執行非同步作業，您必須呼叫 ODBC API 函數 `SQLSetConnectOption`。 如需詳細資訊，請參閱 Windows SDK 中的「非同步執行函式」主題。

### <a name="requirements"></a>需求

  **標頭**afxdb。h

##  <a name="afx_sql_sync"></a>AFX_SQL_SYNC

`AFX_SQL_SYNC` 宏只會 `SQLFunc`呼叫函數。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 如需這些函數的詳細資訊，請參閱 Windows SDK。

### <a name="remarks"></a>備註

使用此宏呼叫將不會傳回 `SQL_STILL_EXECUTING`的 ODBC API 函式。

在呼叫 `AFX_SQL_SYNC`之前，您必須宣告 RETCODE 類型的變數 `nRetCode`。 您可以在宏呼叫之後檢查 `nRetCode` 的值。

請注意，在 MFC 4.2 中，`AFX_SQL_SYNC` 的執行已變更。 因為已不再需要檢查伺服器狀態，所以 `AFX_SQL_SYNC` 只需指派 `nRetCode`的值。 例如，而不是進行呼叫

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

您可以直接進行指派

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxdb。h

##  <a name="afxgethenv"></a>AfxGetHENV

您可以在直接 ODBC 呼叫中使用傳回的控制碼，但是您不能關閉控制碼，或假設控制碼仍然有效，而且在終結任何現有的 `CDatabase`或 `CRecordset`衍生的物件之後可使用。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>傳回值

MFC 目前正在使用之 ODBC 環境的控制碼。 如果沒有[CDatabase](../../mfc/reference/cdatabase-class.md)物件，而且沒有任何[CRecordset](../../mfc/reference/crecordset-class.md)物件正在使用中，就可以 `SQL_HENV_NULL`。

### <a name="requirements"></a>需求

  **標頭**afxdb。h

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
