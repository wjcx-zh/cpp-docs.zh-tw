---
title: 偵錯和錯誤報告全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bef300671894e054ddf9b1ca0ab9dcf3b135370
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019407"
---
# <a name="debugging-and-error-reporting-global-functions"></a>偵錯和錯誤報告全域函式

這些函式會提供有用的偵錯和追蹤工具。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|傳回`GetLastError`HRESULT 的形式中的錯誤程式碼。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|將 Win32 錯誤碼轉換成 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設定`IErrorInfo`提供給用戶端的錯誤詳細資料。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|擲回 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|

##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError

以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>備註

`AtlHresultFromLastError` 呼叫`GetLastError`取得最後一個錯誤，並將它轉換成 HRESULT 使用 HRESULT_FROM_WIN32 巨集之後傳回錯誤。  

### <a name="requirements"></a>需求

**標頭：** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32

將 Win32 錯誤碼轉換成 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>參數

*error*<br/>
要轉換的錯誤值。

### <a name="remarks"></a>備註

將 Win32 錯誤碼轉換成 HRESULT，使用巨集 HRESULT_FROM_WIN32。

> [!NOTE]
>  而不是使用`HRESULT_FROM_WIN32(GetLastError())`，使用函式[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。  

### <a name="requirements"></a>需求

**標頭：** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError

設定`IErrorInfo`錯誤資訊提供給用戶端物件的介面。

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
[in]報告錯誤之物件的 CLSID。

*lpszDesc*<br/>
[in]描述錯誤的字串。 指定的 Unicode 版本*lpszDesc*屬於類型 LPCOLESTR; ANSI 版本指定 LPCSTR 類型。

*iid*<br/>
[in]如果錯誤定義作業系統所定義的錯誤或 GUID_NULL 之介面的 IID。

*hRes*<br/>
[in]您想要的 HRESULT 傳回給呼叫者。

*nID*<br/>
[in]資源識別項的錯誤描述字串的儲存位置。 此值應介於 0x0200 和 0xFFFF 之間 （含）。 在偵錯組建**ASSERT**如果將會產生*nID*並不編製索引的有效字串。 在發行組建中的錯誤描述字串將會設定為 「 未知的錯誤 」。

*dwHelpID*<br/>
[in]錯誤的說明內容識別碼。

*lpszHelpFile*<br/>
[in]路徑名稱與描述錯誤的說明檔。

*hInst*<br/>
[in]資源控制代碼。 根據預設，這個參數是`__AtlBaseModuleModule::GetResourceInstance`，其中`__AtlBaseModuleModule`全域執行個體[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)或從它衍生的類別。

### <a name="return-value"></a>傳回值

如果*hRes*參數為非零值，則傳回的值*hRes*。 如果*hRes*為零，則前四個新版`AtlReportError`傳回 DISP_E_EXCEPTION。 最後兩個版本都會傳回巨集的結果**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。

### <a name="remarks"></a>備註

字串*lpszDesc*做為錯誤的文字描述。 當用戶端收到*hRes*您從傳回`AtlReportError`，用戶端可以存取`IErrorInfo`有關錯誤的詳細資料的結構。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  請勿使用`AtlReportError`c + + catch 處理常式。 這些函式的某些覆寫使用 ATL 字串轉換巨集就內部而言，這會依次使用`_alloca`內部函式。 使用`AtlReportError`在 c + + catch 處理常式可能會造成 c + + catch 處理常式中的例外狀況。  

### <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="atlthrow"></a>  AtlThrow

呼叫此函式可通知發生錯誤，HRESULT 狀態碼為基礎。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>參數

*hr*<br/>
標準的 HRESULT 值。

### <a name="remarks"></a>備註

此函式會使用 ATL 和 MFC 程式碼發生錯誤狀況時。 它也可以從自己的程式碼呼叫。 此函式的預設實作取決於定義的符號 _ATL_NO_EXCEPTIONS 和 MFC 或 ATL 的專案類型

在所有情況下，此函式會追蹤偵錯工具的 HRESULT。

在 Visual Studio 2015 Update 3 和更新版本，此函式是為了避免假性的 SAL 警告屬性化 __declspec （noreturn）。

如果未定義 _ATL_NO_EXCEPTIONS MFC 專案中，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) HRESULT 的值。

如果未定義 _ATL_NO_EXCEPTIONS ATL 專案中，函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。

如果定義 _ATL_NO_EXCEPTIONS，函式會造成判斷提示失敗而非擲回例外狀況。

ATL 專案，就可以提供您自己的實作，可供在失敗時的 ATL 此函式。 若要這樣做，請定義您自己的函式具有相同的簽章`AtlThrow`和 #define`AtlThrow`設為您的函式的名稱。 這必須包括 atlexcept.h （亦即，必須完成之前因為 atlbase.h 包含 atlexcept.h，包括任何 ATL 標頭） 之前完成。 屬性函式`__declspec(noreturn)`以避免假性的 SAL 警告。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>需求

**標頭：** atldef.h  

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32

呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>備註

此函式追蹤的結果`GetLastError`偵錯工具。

如果未定義 _ATL_NO_EXCEPTIONS MFC 專案中，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或是[COleException](../../mfc/reference/coleexception-class.md)所傳回的值為基礎`GetLastError`。

如果未定義 _ATL_NO_EXCEPTIONS ATL 專案中，函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。

如果定義 _ATL_NO_EXCEPTIONS，函式會造成判斷提示失敗而非擲回例外狀況。  

## <a name="requirements"></a>需求

**標頭：** atldef.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)<br/>
[偵錯和錯誤報告巨集](../../atl/reference/debugging-and-error-reporting-macros.md)

