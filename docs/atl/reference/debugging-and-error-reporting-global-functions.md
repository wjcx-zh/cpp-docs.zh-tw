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
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417709"
---
# <a name="debugging-and-error-reporting-global-functions"></a>調試和錯誤報表全域函式

這些函式提供有用的調試和追蹤功能。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|以 HRESULT 的形式傳回 `GetLastError` 錯誤碼。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|將 Win32 錯誤碼轉換成 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設定 `IErrorInfo` 將錯誤詳細資料提供給用戶端。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|擲回 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|

##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>備註

`AtlHresultFromLastError` 會 `GetLastError` 取得最後一個錯誤，並在使用 HRESULT_FROM_WIN32 宏將它轉換成 HRESULT 之後傳回錯誤。

### <a name="requirements"></a>需求

**標頭：** atlcomcli.h。h

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32

將 Win32 錯誤碼轉換成 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>參數

*error*<br/>
要轉換的錯誤值。

### <a name="remarks"></a>備註

使用宏 HRESULT_FROM_WIN32，將 Win32 錯誤代碼轉換成 HRESULT。

> [!NOTE]
>  不使用 `HRESULT_FROM_WIN32(GetLastError())`，而是使用函式[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。

### <a name="requirements"></a>需求

**標頭：** atlcomcli.h。h

##  <a name="atlreporterror"></a>AtlReportError

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

*clsid*<br/>
在報告錯誤之物件的 CLSID。

*lpszDesc*<br/>
在描述錯誤的字串。 Unicode 版本指定*lpszDesc*的類型為 LPCOLESTR;ANSI 版本會指定 LPCSTR 的類型。

*iid*<br/>
在定義錯誤之介面的 IID，如果錯誤是由作業系統所定義，則為 GUID_Null。

*hRes*<br/>
在您想要傳回給呼叫者的 HRESULT。

*nID*<br/>
在儲存錯誤描述字串的資源識別碼。 這個值應介於0x0200 與0xFFFF （含）之間。 在 debug 組建中，如果*nID*未編制有效字串的索引 **，就會產生判斷**提示。 在發行組建中，錯誤描述字串會設定為「未知的錯誤」。

*dwHelpID*<br/>
在錯誤的說明內容識別碼。

*lpszHelpFile*<br/>
在描述錯誤之說明檔的路徑和名稱。

*hInst*<br/>
在資源的控制碼。 根據預設，此參數為 `__AtlBaseModuleModule::GetResourceInstance`，其中 `__AtlBaseModuleModule` 是[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)的全域實例或從中衍生的類別。

### <a name="return-value"></a>傳回值

如果*hRes*參數不是零，則會傳回*hRes*的值。 如果*hRes*為零，則 `AtlReportError` 的前四個版本會傳回 DISP_E_EXCEPTION。 最後兩個版本會傳回宏的結果**MAKE_HRESULT （1，FACILITY_ITF，** `nID` **）** 。

### <a name="remarks"></a>備註

字串*lpszDesc*會當做錯誤的文字描述使用。 當用戶端收到您從 `AtlReportError`傳回的*hRes*時，用戶端可以存取 `IErrorInfo` 結構，以取得錯誤的詳細資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  請勿在 catch 處理常式C++中使用 `AtlReportError`。 這些函式的某些覆寫會在內部使用「ATL 字串轉換宏」，而這會在內部使用 `_alloca` 函數。 在C++ catch 處理常式中使用 `AtlReportError` 可能會在C++ catch 處理常式中造成例外狀況。

### <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="atlthrow"></a>AtlThrow

呼叫此函式可根據 HRESULT 狀態碼來發出錯誤信號。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>參數

*工時*<br/>
標準 HRESULT 值。

### <a name="remarks"></a>備註

當發生錯誤狀況時，ATL 和 MFC 程式碼會使用這個函式。 也可以從您自己的程式碼呼叫它。 此函式的預設執行取決於符號的定義 _ATL_NO_EXCEPTIONS 以及專案、MFC 或 ATL 的類型。

在所有情況下，此函式都會將 HRESULT 追蹤至偵錯工具。

在 Visual Studio 2015 Update 3 和更新版本中，此函式已屬性化 __declspec （noreturn），以避免發生虛假的 SAL 警告。

如果未在 MFC 專案中定義 _ATL_NO_EXCEPTIONS，此函式會根據 HRESULT 的值擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) 。

如果 _ATL_NO_EXCEPTIONS 未在 ATL 專案中定義，則函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。

如果已定義 _ATL_NO_EXCEPTIONS，此函式會導致判斷提示失敗，而不會擲回例外狀況。

針對 ATL 專案，可以提供您自己的函式，以便在發生失敗時由 ATL 使用。 若要這麼做，請使用與 `AtlThrow` 相同的簽章來定義您自己的函式，並 #define `AtlThrow` 為函式的名稱。 這必須在包含 atlexcept 之前完成（這表示必須在包含任何 ATL 標頭之前完成此動作，因為 atlbase.h 包含 atlexcept。 h）。 屬性您的函式 `__declspec(noreturn)` 以避免發生虛假的 SAL 警告。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>需求

**標頭：** atldef。h

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32

呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>備註

此函式會將 `GetLastError` 的結果追蹤至偵錯工具。

如果未在 MFC 專案中定義 _ATL_NO_EXCEPTIONS，此函式會根據 `GetLastError`所傳回的值來擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) 。

如果 _ATL_NO_EXCEPTIONS 未在 ATL 專案中定義，則函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。

如果已定義 _ATL_NO_EXCEPTIONS，此函式會導致判斷提示失敗，而不會擲回例外狀況。

## <a name="requirements"></a>需求

**標頭：** atldef。h

## <a name="see-also"></a>另請參閱

[函數](../../atl/reference/atl-functions.md)<br/>
[偵錯和錯誤報告巨集](../../atl/reference/debugging-and-error-reporting-macros.md)
