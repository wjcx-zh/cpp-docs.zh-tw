---
title: "偵錯和錯誤報告全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b3383efcc78a022fc5131984957d94aa4b47838
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-global-functions"></a>偵錯和錯誤報告全域函式
這些函式提供有用的偵錯和追蹤功能。  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|傳回`GetLastError`錯誤程式碼，在以 HRESULT 的形式。|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|將 Win32 錯誤碼轉換成 HRESULT。|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設定**IErrorInfo**提供給用戶端的錯誤詳細資料。|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|擲回 `CAtlException`。|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|  
  
##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError  
 以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>備註  
 `AtlHresultFromLastError`呼叫`GetLastError`取得最後一個錯誤，並將它轉換成 HRESULT 使用之後傳回錯誤**HRESULT_FROM_WIN32**巨集。  

### <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32  
 將 Win32 錯誤碼轉換成 HRESULT。  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>參數  
 *錯誤*  
 要轉換的錯誤值。  
  
### <a name="remarks"></a>備註  
 將 Win32 錯誤碼轉換成 HRESULT，使用巨集**HRESULT_FROM_WIN32**。  
  
> [!NOTE]
>  而不是使用**HRESULT_FROM_WIN32(GetLastError())**，使用函數[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。  

### <a name="requirements"></a>需求  
 **標頭：** atlcomcli.h  

##  <a name="atlreporterror"></a>AtlReportError  
 設定`IErrorInfo`介面，以提供給用戶端物件的資訊時發生錯誤。  
  
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
 `clsid`  
 [in]報告錯誤物件的 CLSID。  
  
 `lpszDesc`  
 [in]描述錯誤的字串。 Unicode 版本指定`lpszDesc`的型別**LPCOLESTR**; ANSI 版本指定一種`LPCSTR`。  
  
 `iid`  
 [in]定義錯誤之介面的 IID 或`GUID_NULL`如果錯誤由作業系統所定義。  
  
 `hRes`  
 [in]`HRESULT`您想要傳回給呼叫者。  
  
 `nID`  
 [in]儲存錯誤描述字串資源的識別項。 這個值應該介於 0x0200 和 0xFFFF 之間 （含） 之間。 在偵錯組建**ASSERT**如果將會產生`nID`未索引的有效字串。 在發行組建中的錯誤描述字串將會設定為 「 未知的錯誤 」。  
  
 `dwHelpID`  
 [in]錯誤的說明內容識別碼。  
  
 `lpszHelpFile`  
 [in]路徑和名稱，描述錯誤的說明檔。  
  
 `hInst`  
 [in]資源控制代碼。 根據預設，這個參數是**__AtlBaseModuleModule::GetResourceInstance**，其中**__AtlBaseModuleModule**的全域執行個體[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)或類別衍生自它。  
  
### <a name="return-value"></a>傳回值  
 如果`hRes`參數為非零，傳回的值`hRes`。 如果`hRes`是零，則前四個新版`AtlReportError`傳回`DISP_E_EXCEPTION`。 最後兩個版本都會傳回巨集的結果**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。  
  
### <a name="remarks"></a>備註  
 字串*lpszDesc*用做為錯誤的文字描述。 當用戶端收到`hRes`您從傳回`AtlReportError`，用戶端可以存取**IErrorInfo**錯誤的詳細資料的結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  請勿使用`AtlReportError`c + + 中的 catch 處理常式。 這些函式的某些覆寫使用 ATL 字串轉換巨集就內部而言，接著使用`_alloca`函式內部。 使用`AtlReportError`在 c + + catch 處理常式可能會導致在 c + + catch 處理常式中的例外狀況。  

### <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
    
##  <a name="atlthrow"></a>AtlThrow  
 呼叫此函式可依據 `HRESULT` 狀態碼通知發生錯誤。  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>參數  
 `hr`  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此函式會使用 ATL 和 MFC 程式碼發生錯誤狀況時。 它也可以從自己的程式碼呼叫。 符號的定義取決於此函式的預設實作**_ATL_NO_EXCEPTIONS**及類型的專案中，MFC 或 atl。  
  
 在所有情況下，此函式會追蹤偵錯工具的 HRESULT。  
  
 在 Visual Studio 2015 Update 3 及更新版本，此函式是為了避免假性的 SAL 警告屬性化 __declspec （noreturn）。  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 MFC 專案中，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)基礎 HRESULT 值。  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 ATL 專案中，則函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果**_ATL_NO_EXCEPTIONS**是定義，此函式會造成判斷提示失敗，而不是擲回例外狀況。  
  
 ATL 專案中，很可能提供您自己的實作，此函式，以供 ATL 失敗。 若要這樣做，請定義您自己的函式具有相同的簽章`AtlThrow`和 #define`AtlThrow`函式的名稱。 這必須包括 atlexcept.h （亦即它必須完成之前因為 atlbase.h 包含 atlexcept.h ATL 標頭加入） 之前完成。 屬性函式`__declspec(noreturn)`避免假性的 SAL 警告。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>需求  
 **標頭：** atldef.h  

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32  
 呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>備註  
 此函式追蹤的結果`GetLastError`偵錯工具。  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 MFC 專案中，此函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) 所傳回的值為基礎`GetLastError`.  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 ATL 專案中，則函式會擲回[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果**_ATL_NO_EXCEPTIONS**是定義，此函式會造成判斷提示失敗，而不是擲回例外狀況。  

## <a name="requirements"></a>需求  
 **標頭：** atldef.h  
   
     
## <a name="see-also"></a>請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [偵錯和錯誤報告巨集](../../atl/reference/debugging-and-error-reporting-macros.md)









