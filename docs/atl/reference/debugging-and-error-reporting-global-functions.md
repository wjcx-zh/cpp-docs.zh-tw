---
title: "偵錯和錯誤報告全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4a412910d13d10606080c14412d33d2b614fdcec
ms.lasthandoff: 02/24/2017

---
# <a name="debugging-and-error-reporting-global-functions"></a>偵錯和錯誤報告全域函式
這些函式提供有用的偵錯和追蹤功能。  
  
|||  
|-|-|  
|[AtlHresultFromLastError](http://msdn.microsoft.com/library/74530d7d-3c91-484c-acf3-aff755715d66)|傳回`GetLastError`HRESULT 的形式中的錯誤碼。|  
|[AtlHresultFromWin32](http://msdn.microsoft.com/library/63add2dd-274c-4e72-a98c-040b93413a2f)|將 Win32 錯誤碼轉換成 HRESULT。|  
|[AtlReportError](http://msdn.microsoft.com/library/86b046a5-ea18-4ecf-9aab-40fc1eab847c)|設定**IErrorInfo**錯誤詳細資料提供給用戶端。|  
|[AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)|擲回 `CAtlException`。|  
|[AtlThrowLastWin32](http://msdn.microsoft.com/library/8bce8e56-c7cd-4ebb-8c62-80ebc63a3d07)|呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。|  
  
##  <a name="a-nameatlhresultfromlasterrora--atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultFromLastError  
 以 HRESULT 的形式，傳回呼叫執行緒的最後一個錯誤碼值。  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>備註  
 `AtlHresultFromLastError`呼叫`GetLastError`取得最後一個錯誤，並將它轉換成 HRESULT 使用之後傳回錯誤**HRESULT_FROM_WIN32**巨集。  

### <a name="requirements"></a>需求  
 **標頭︰** atlcomcli.h  

##  <a name="a-nameatlhresultfromwin32a--atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultFromWin32  
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
>  而不是使用**HRESULT_FROM_WIN32(GetLastError())**，使用函數[AtlHresultFromLastError](http://msdn.microsoft.com/library/74530d7d-3c91-484c-acf3-aff755715d66)。  

### <a name="requirements"></a>需求  
 **標頭︰** atlcomcli.h  

##  <a name="a-nameatlreporterrora--atlreporterror"></a><a name="atlreporterror"></a>AtlReportError  
 設定`IErrorInfo`介面物件的用戶端提供錯誤資訊。  
  
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
 [in]報告該錯誤之物件的 CLSID。  
  
 `lpszDesc`  
 [in]描述錯誤的字串。 指定的 Unicode 版本`lpszDesc`的型別**LPCOLESTR**，ANSI 版本指定類型的`LPCSTR`。  
  
 `iid`  
 [in]定義錯誤之介面的 IID 或`GUID_NULL`如果錯誤由作業系統所定義。  
  
 `hRes`  
 [in]`HRESULT`您想要傳回給呼叫者。  
  
 `nID`  
 [in]儲存的錯誤描述字串資源的識別項。 這個值應該介於 0x0200 和 0xFFFF 之間 （含） 之間。 在偵錯組建**ASSERT**如果就會產生`nID`未索引的有效字串。 在發行組建的錯誤描述字串會設定為 「 未知的錯誤 」。  
  
 `dwHelpID`  
 [in]這個錯誤的說明內容識別碼。  
  
 `lpszHelpFile`  
 [in]路徑名稱與描述錯誤的說明檔。  
  
 `hInst`  
 [in]資源控制代碼。 根據預設，這個參數是**__AtlBaseModuleModule::GetResourceInstance**，其中**__AtlBaseModuleModule**全域執行個體[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)或從中衍生的類別。  
  
### <a name="return-value"></a>傳回值  
 如果`hRes`參數為非零，則傳回的值`hRes`。 如果`hRes`是零，則前四個版本`AtlReportError`傳回`DISP_E_EXCEPTION`。 最後兩個版本都會傳回巨集的結果**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。  
  
### <a name="remarks"></a>備註  
 字串*lpszDesc*做為錯誤的文字描述。 當用戶端收到`hRes`您從傳回`AtlReportError`，用戶端可以存取**IErrorInfo**錯誤的詳細資訊的結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM&#52;](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  請勿使用`AtlReportError`在 c + + catch 處理常式。 某些覆寫這些函式使用 ATL 字串轉換巨集就內部而言，依序使用`_alloca`內部函式。 使用`AtlReportError`在 c + + catch 處理常式可能會導致 c + + catch 處理常式中的例外狀況。  

### <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
    
##  <a name="a-nameatlthrowa--atlthrow"></a><a name="atlthrow"></a>AtlThrow  
 呼叫此函式可依據 `HRESULT` 狀態碼通知發生錯誤。  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>參數  
 `hr`  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此函式會使用 ATL 和 MFC 程式碼發生錯誤狀況時。 它也可以從自己的程式碼呼叫。 此函式的預設實作取決於定義的符號**_ATL_NO_EXCEPTIONS**和 MFC 或 ATL 的專案類型  
  
 在所有情況下，此函式會追蹤偵錯工具的 HRESULT。  
  
 在 Visual Studio 2015 Update 3 及更新版本，此函式是為了避免假性 SAL 警告屬性化 __declspec （noreturn）。  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 MFC 專案中，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)基礎 HRESULT 值。  
  
 如果**_ATL_NO_EXCEPTIONS** ATL 專案，則函式會擲回中未定義[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果**_ATL_NO_EXCEPTIONS**是定義，此函數會引發判斷提示而非擲回例外狀況。  
  
 ATL 專案，就可以提供自己的實作，此函式可供 ATL 發生失敗時。 若要這樣做，請定義您自己的函式具有相同的簽章`AtlThrow`和 #define`AtlThrow`函式的名稱。 這必須包括 atlexcept.h （亦即，必須完成之前因為 atlbase.h 包含 atlexcept.h，包括任何 ATL 標頭） 之前完成。 屬性函式`__declspec(noreturn)`可避免假性 SAL 警告。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&95;](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>需求  
 **標頭︰** atldef.h  

##  <a name="a-nameatlthrowlastwin32a--atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32  
 呼叫此函式可依據 Windows 函式 `GetLastError` 的結果通知發生錯誤。  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>備註  
 此函式追蹤的結果`GetLastError`偵錯工具。  
  
 如果**_ATL_NO_EXCEPTIONS**未定義在 MFC 專案中，此函式會擲回[Afxthrowmemoryexception](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)根據所傳回的值`GetLastError`。  
  
 如果**_ATL_NO_EXCEPTIONS** ATL 專案，則函式會擲回中未定義[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果**_ATL_NO_EXCEPTIONS**是定義，此函數會引發判斷提示而非擲回例外狀況。  

## <a name="requirements"></a>需求  
 **標頭︰** atldef.h  
   
     
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)   
 [偵錯和錯誤報告巨集](../../atl/reference/debugging-and-error-reporting-macros.md)










