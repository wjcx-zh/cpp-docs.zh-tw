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
ms.openlocfilehash: 6d8bd56c0bfe4f9b35e34d067dd1042ed11066d5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751666"
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
|[AfxDbInitModule](#afxdbinitmodule)|添加對動態連結到 MFC 的常規 MFC DLL 的資料庫支援。|
|[AfxGetHENV](#afxgethenv)|擷取目前正在由 MFC 使用的 ODBC 環境控制代碼。 您可以直接呼叫 ODBC 時使用這個控制代碼。|

## <a name="afxdbinitmodule"></a><a name="afxdbinitmodule"></a>AfxDbinit 模組

對於動態連結到 MFC 的常規 MFC DLL 的 MFC 資料庫(或 DAO)支援,在常規`CWinApp::InitInstance`MFC DLL 函數中添加對此函數的調用,以初始化 MFC資料庫 DLL。

### <a name="syntax"></a>語法

```cpp
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>備註

請確保此調用發生在任何基類調用或訪問 MFC 資料庫 DLL 的任何添加代碼之前。 MFC 資料庫 DLL 是 MFC 擴展 DLL;為了使 MFC 擴展 DLL 連接到`CDynLinkLibrary`鏈中,它必須在`CDynLinkLibrary`將使用它的每個模組 的上下文中創建一個物件。 `AfxDbInitModule`在`CDynLinkLibrary`常規 MFC DLL 的上下文中創建物件,以便將其連接到常規`CDynLinkLibrary`MFC DLL 的物件鏈中。

### <a name="requirements"></a>需求

**標題:** \<afxdll_.h>

## <a name="afx_odbc_call"></a><a name="afx_odbc_call"></a>AFX_ODBC_CALL

使用此宏可以調用任何可能返回`SQL_STILL_EXECUTING`的ODBC API函數。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 有關 ODBC API 功能的詳細資訊,請參閱 Windows SDK。

### <a name="remarks"></a>備註

`AFX_ODBC_CALL`重複呼叫函數,直到它不再傳`SQL_STILL_EXECUTING`回 。

在調用`AFX_ODBC_CALL`之前,必須聲明類型 RETCODE`nRetCode`的變數 ,

請注意,MFC ODBC 類現在僅使用同步處理。 為了執行非同步操作,必須呼叫 ODBC API`SQLSetConnectOption`函數 。 有關詳細資訊,請參閱 Windows SDK 中的主題「非同步執行函數」。

### <a name="example"></a>範例

此範例用於`AFX_ODBC_CALL`呼叫`SQLColumns`ODBC API函數,該函數傳`strTableName`回由命名的表中的列的清單。 請注意記錄集數據`nRetCode`成員的聲明和使用,以將參數傳遞給函數。 該示例還演示了使用`Check`檢查調用的結果,該函數是`CRecordset`類的成員函數。 變數`prs`是指向`CRecordset`物件的指標,聲明在其他地方。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="afx_sql_async"></a><a name="afx_sql_async"></a>AFX_SQL_ASYNC

在 MFC 4.2 變更這個巨集實作。

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>參數

*prs*<br/>
`CRecordset` 物件或 `CDatabase` 物件指標。 從 MFC 4.2 開始略過這個參數值。

*SQLFunc*<br/>
ODBC API 函式。 有關 ODBC API 功能的詳細資訊,請參閱 Windows SDK。

### <a name="remarks"></a>備註

`AFX_SQL_ASYNC`只需調用宏[AFX_ODBC_CALL](#afx_odbc_call)並忽略*prs*參數。 在 MFC 4.2 之前的版本中，`AFX_SQL_ASYNC` 是用來呼叫可能傳回 `SQL_STILL_EXECUTING` 的 ODBC API 函式。 如果 ODBC API 函式確實傳回 `SQL_STILL_EXECUTING`，則 `AFX_SQL_ASYNC` 會呼叫 `prs->OnWaitForDataSource`。

> [!NOTE]
> MFC ODBC 類別現在只會使用同步處理。 為了執行非同步操作,必須呼叫 ODBC API`SQLSetConnectOption`函數 。 有關詳細資訊,請參閱 Windows SDK 中的主題「非同步執行函數」。

### <a name="requirements"></a>需求

  **頭**afxdb.h

## <a name="afx_sql_sync"></a><a name="afx_sql_sync"></a>AFX_SQL_SYNC

巨`AFX_SQL_SYNC`集只是呼叫`SQLFunc`函數 。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>參數

*SQLFunc*<br/>
ODBC API 函式。 有關這些功能的詳細資訊,請參閱 Windows SDK。

### <a name="remarks"></a>備註

使用此宏可以調用不會返回`SQL_STILL_EXECUTING`的ODBC API函數。

在調用`AFX_SQL_SYNC`之前,必須聲明 RETCODE 類型`nRetCode`的變數 , 您可以在宏調用後檢查`nRetCode`的值。

請注意,MFC `AFX_SQL_SYNC` 4.2 中的實現已更改。 由於不再需要檢查伺服器狀態,`AFX_SQL_SYNC`因此只需將值分配給`nRetCode`。 例如,而不是進行呼叫

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

你可以簡單地做分配

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>需求

  **頭**afxdb.h

## <a name="afxgethenv"></a><a name="afxgethenv"></a>阿夫達赫內夫

您可以在直接 ODBC 調用中使用傳回的句柄,但不得關閉句柄或假定該句柄`CDatabase`在`CRecordset`任何現有或 派生物件被銷毀後仍然有效且可用。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>傳回值

對 MFC 目前正在使用的 ODBC 環境的句柄。 `SQL_HENV_NULL`如果沒有[CDatabase](../../mfc/reference/cdatabase-class.md)物件,並且沒有[CRecordset](../../mfc/reference/crecordset-class.md)物件正在使用,則可以。

### <a name="requirements"></a>需求

  **頭**afxdb.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
