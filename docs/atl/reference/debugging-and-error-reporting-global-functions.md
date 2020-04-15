---
title: 除錯及錯誤報告全域函數
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330198"
---
# <a name="debugging-and-error-reporting-global-functions"></a>除錯及錯誤報告全域函數

這些功能提供有用的調試和跟蹤功能。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|返回`GetLastError`HRESULT 形式的錯誤代碼。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|將 Win32 錯誤碼轉換成 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設置`IErrorInfo`以向用戶端提供錯誤詳細資訊。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|擲回 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>從上次錯誤中得出

以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>備註

`AtlHresultFromLastError`調用`GetLastError`以取得最後一個錯誤,並在使用HRESULT_FROM_WIN32宏將其轉換為 HRESULT 後返回該錯誤。

### <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresult從Win32

將 Win32 錯誤碼轉換成 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>參數

*error*<br/>
要轉換的錯誤值。

### <a name="remarks"></a>備註

使用宏HRESULT_FROM_WIN32將 Win32 錯誤代碼轉換為 HRESULT。

> [!NOTE]
> 而不是使用`HRESULT_FROM_WIN32(GetLastError())`, 使用函數[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。

### <a name="requirements"></a>需求

**標題:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReport錯誤

設置`IErrorInfo`介面以向物件的用戶端提供錯誤資訊。

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
[在]報告錯誤的物件的 CLSID。

*lpszDesc*<br/>
[在]描述錯誤的字串。 Unicode 版本指定*lpszDesc*的類型為 LPCOLESTR;ANSI 版本指定 LPCSTR 的類型。

*Iid*<br/>
[在]定義錯誤的介面的 IID,或者如果錯誤是由操作系統定義的,則GUID_NULL。

*hRes*<br/>
[在]要返回給調用方的 HRESULT。

*nID*<br/>
[在]儲存錯誤描述字串的資源識別碼。 此值應介於 0x0200 和 0xFF 之間(包括)。 在除錯產生中,如果*nID*不索引有效字串,則會產生**ASSERT。** 在發佈版本中,錯誤描述字串將設置為"未知錯誤"。

*dwHelpID*<br/>
[在]錯誤的説明上下文標識碼。

*lpszHelp 檔案*<br/>
[在]描述錯誤的幫助檔的路徑和名稱。

*hInst*<br/>
[在]資源的句柄。 默認情況下,此參數是`__AtlBaseModuleModule::GetResourceInstance``__AtlBaseModuleModule` [,CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)的全域實例或派生自它的類位於此地。

### <a name="return-value"></a>傳回值

如果*hRes*參數是非零,則返回*hRes*的值。 如果*hRes*為零`AtlReportError`,則返回的前四個版本DISP_E_EXCEPTION。 最後兩個版本返回宏**MAKE_HRESULT的結果(1,FACILITY_ITF。** `nID` **)**

### <a name="remarks"></a>備註

字串*lpszDesc*用作錯誤的文本說明。 當用戶端收到您從`AtlReportError`返回*的 hRe 時*,用戶端可以`IErrorInfo`訪問結構以瞭解有關錯誤的詳細資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> 請勿在`AtlReportError`C++捕獲處理程式中使用。 這些函數的某些重寫在內部使用 ATL 字串轉換宏,而後者又在內部`_alloca`使用 該函數。 `AtlReportError`在C++捕獲處理程式中使用可能會導致C++捕獲處理程式中的異常。

### <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow

呼叫此函數以根據 HRESULT 狀態代碼發出錯誤信號。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>參數

*人力資源*<br/>
標準 HRESULT 值。

### <a name="remarks"></a>備註

在出現錯誤情況時,ATL 和 MFC 代碼會使用此功能。 也可以從您自己的代碼調用它。 此函數的預設實現取決於符號_ATL_NO_EXCEPTIONS的定義以及項目類型 MFC 或 ATL。

在所有情況下,此函數將HRESULT追蹤到除錯器。

在 Visual Studio 2015 更新 3 及更高版本中,此功能被歸因於__declspec(不返回),以避免虛假的 SAL 警告。

如果未在 MFC 專案中定義_ATL_NO_EXCEPTIONS,則此函數將基於 HRESULT 的值引發[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException。](../../mfc/reference/coleexception-class.md)

如果在 ATL 專案中未定義_ATL_NO_EXCEPTIONS,則函數將引發[CAtlException](../../atl/reference/catlexception-class.md)。

如果定義了_ATL_NO_EXCEPTIONS,則函數會導致斷言失敗,而不是引發異常。

對於 ATL 專案,可以提供您自己的實現,以便 ATL 在發生故障時使用此功能。 為此,使用與`AtlThrow`函數的名稱相同的簽名和#define`AtlThrow`定義您自己的函數。 這必須在包括 atlexcept.h 之前完成(這意味著在包括任何 ATL 標頭之前必須完成,因為 atlbase.h 包含 atlexcept.h)。 屬性函數`__declspec(noreturn)`以避免虛假的 SAL 警告。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>需求

**標題:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>備註

此函式追蹤除錯器的結果`GetLastError`。

如果未在 MFC 專案中定義_ATL_NO_EXCEPTIONS,則此函數將`GetLastError`基於返回的值引發[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException。](../../mfc/reference/coleexception-class.md)

如果在 ATL 專案中未定義_ATL_NO_EXCEPTIONS,則函數將引發[CAtlException](../../atl/reference/catlexception-class.md)。

如果定義了_ATL_NO_EXCEPTIONS,則函數會導致斷言失敗,而不是引發異常。

## <a name="requirements"></a>需求

**標題:** atldef.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[除錯和錯誤報告巨集](../../atl/reference/debugging-and-error-reporting-macros.md)
