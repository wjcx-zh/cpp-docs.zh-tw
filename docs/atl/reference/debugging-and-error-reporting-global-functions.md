---
title: 調試和錯誤報表全域函式
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: 10aca6862f6989c126981a9f6437c61f1c07bdae
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742784"
---
# <a name="debugging-and-error-reporting-global-functions"></a>調試和錯誤報表全域函式

這些函式會提供實用的調試和追蹤功能。

|名稱|描述|
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|`GetLastError`以 HRESULT 的形式傳回錯誤碼。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|將 Win32 錯誤碼轉換成 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設定 `IErrorInfo` 以提供錯誤詳細資料給用戶端。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|擲回 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a> AtlHresultFromLastError

以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>備註

`AtlHresultFromLastError` 呼叫 `GetLastError` 以取得最後一個錯誤，並在使用 HRESULT_FROM_WIN32 宏將錯誤轉換成 HRESULT 之後傳回錯誤。

### <a name="requirements"></a>規格需求

**標頭：** atlcomcli.h。h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a> AtlHresultFromWin32

將 Win32 錯誤碼轉換成 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>參數

*error*<br/>
要轉換的錯誤值。

### <a name="remarks"></a>備註

使用宏 HRESULT_FROM_WIN32，將 Win32 錯誤碼轉換成 HRESULT。

> [!NOTE]
> 使用函式 `HRESULT_FROM_WIN32(GetLastError())` [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)，而不是使用。

### <a name="requirements"></a>規格需求

**標頭：** atlcomcli.h。h

## <a name="atlreporterror"></a><a name="atlreporterror"></a> AtlReportError

設定 `IErrorInfo` 介面，以提供錯誤資訊給物件的用戶端。

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>參數

*Clsid*<br/>
在報告錯誤之物件的 CLSID。

*lpszDesc*<br/>
在描述錯誤的字串。 Unicode 版本會指定 *lpszDesc* 的類型是 LPCOLESTR;ANSI 版本會指定 LPCSTR 的類型。

*Iid*<br/>
在定義錯誤之介面的 IID，如果錯誤是由作業系統所定義，則為 GUID_Null。

*hRes*<br/>
在您要傳回給呼叫者的 HRESULT。

*nID*<br/>
在儲存錯誤描述字串的資源識別碼。 此值應介於0x0200 與0xFFFF 之間。 在 debug 組建中，如果*nID*沒有為有效的字串編制索引 **，就會產生判斷**提示。 在發行組建中，錯誤描述字串會設定為「未知的錯誤」。

*dwHelpID*<br/>
在錯誤的說明內容識別碼。

*lpszHelpFile*<br/>
在描述錯誤之說明檔的路徑和名稱。

*hInst*<br/>
在資源的控制碼。 根據預設，這個參數是 `__AtlBaseModuleModule::GetResourceInstance` ，其中 `__AtlBaseModuleModule` 是 [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) 的全域實例或衍生自它的類別。

### <a name="return-value"></a>傳回值

如果 *hRes* 參數為非零值，則會傳回 *hRes*的值。 如果 *hRes* 為零，則會傳回 DISP_E_EXCEPTION 的前四個版本 `AtlReportError` 。 最後兩個版本會傳回宏 MAKE_HRESULT 的結果 ** ( 1、FACILITY_ITF** `nID` **) **。

### <a name="remarks"></a>備註

字串 *lpszDesc* 會用來做為錯誤的文字描述。 當用戶端收到您從傳回的 *hRes* 時 `AtlReportError` ，用戶端可以存取該 `IErrorInfo` 結構以取得錯誤的詳細資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> 請勿 `AtlReportError` 在 c + + catch 處理常式中使用。 這些函式的某些覆寫會在內部使用 ATL 字串轉換宏，而後者接著會在 `_alloca` 內部使用函數。 `AtlReportError`在 c + + catch 處理常式中使用，可能會導致 c + + catch 處理常式發生例外狀況

### <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="atlthrow"></a><a name="atlthrow"></a> AtlThrow

呼叫此函式可根據 HRESULT 狀態碼來發出錯誤信號。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>參數

*小時*<br/>
標準 HRESULT 值。

### <a name="remarks"></a>備註

當錯誤狀況發生時，ATL 和 MFC 程式碼會使用這個函數。 您也可以從自己的程式碼呼叫它。 這個函式的預設執行取決於符號的定義 _ATL_NO_EXCEPTIONS 以及專案、MFC 或 ATL 的類型。

在所有情況下，此函式會將 HRESULT 追蹤至偵錯工具。

在 Visual Studio 2015 Update 3 和更新版本中，此函式的屬性 __declspec (noreturn) ，以避免發生虛假的 SAL 警告。

如果未在 MFC 專案中定義 _ATL_NO_EXCEPTIONS，此函式會根據 HRESULT 的值擲回 [CMemoryException](../../mfc/reference/cmemoryexception-class.md) 或 [COleException](../../mfc/reference/coleexception-class.md) 。

如果 _ATL_NO_EXCEPTIONS 未在 ATL 專案中定義，則函數會擲回 [CAtlException](../../atl/reference/catlexception-class.md)。

如果定義了 _ATL_NO_EXCEPTIONS，函數會導致判斷提示失敗，而不是擲回例外狀況。

在 ATL 專案中，您可以提供您自己的函式執行，以便 ATL 在發生失敗時使用。 若要這樣做，請使用與相同的簽章來定義您自己的函式， `AtlThrow` 並 #define `AtlThrow` 為您的函式名稱。 這必須在包含 (atlexcept 之前完成，這表示必須在包含任何 ATL 標頭之前完成此步驟，因為 atlbase.h 包含 atlexcept 的) 。 為您的函式 `__declspec(noreturn)` 進行屬性，以避免發生虛假的 SAL 警告。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

### <a name="requirements"></a>規格需求

**標頭：** atldef。h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a> AtlThrowLastWin32

呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>備註

此函數會將的結果追蹤 `GetLastError` 至偵錯工具。

如果未在 MFC 專案中定義 _ATL_NO_EXCEPTIONS，此函式會根據所傳回的值擲回 [CMemoryException](../../mfc/reference/cmemoryexception-class.md) 或 [COleException](../../mfc/reference/coleexception-class.md) `GetLastError` 。

如果 _ATL_NO_EXCEPTIONS 未在 ATL 專案中定義，則函數會擲回 [CAtlException](../../atl/reference/catlexception-class.md)。

如果定義了 _ATL_NO_EXCEPTIONS，函數會導致判斷提示失敗，而不是擲回例外狀況。

### <a name="requirements"></a>規格需求

**標頭：** atldef。h

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[調試和錯誤報表宏](../../atl/reference/debugging-and-error-reporting-macros.md)
