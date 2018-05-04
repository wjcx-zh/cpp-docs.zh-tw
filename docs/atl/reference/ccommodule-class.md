---
title: CComModule 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b4ec763f6ee719e96627be3dc81a1e9b56c2c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ccommodule-class"></a>CComModule 類別
為準，ATL 7.0`CComModule`已被取代： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|建立指定的 CLSID 的物件。 只有 dll。|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|傳回 `m_hInst`。|  
|[CComModule::GetResourceInstance](#getresourceinstance)|傳回 `m_hInstResource`。|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|傳回 `m_hInstTypeLib`。|  
|[Init](#init)|初始化資料成員。|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|輸入物件的標準類別註冊系統登錄中。|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|註冊類別物件。 針對只 Exe。|  
|[CComModule::RegisterServer](#registerserver)|更新系統登錄的物件對應中每個物件。|  
|[CComModule::RegisterTypeLib](#registertypelib)|註冊類型程式庫。|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。 針對只 Exe。|  
|[Ccommodule:: Term](#term)|釋放資料成員。|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|從系統登錄中移除物件的標準類別註冊。|  
|[CComModule::UnregisterServer](#unregisterserver)|移除物件對應中的每個物件的註冊。|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|註冊或取消註冊物件的標準類別註冊。|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行指定的資源登錄或取消登錄物件中包含的指令碼。|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|以靜態方式連結至 ATL 登錄元件。 執行指定的資源登錄或取消登錄物件中包含的指令碼。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|可確保物件對應資訊的同步的存取。|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|可確保同步處理的資訊的存取權類型程式庫。|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|可確保視窗類別資訊和視窗建立期間使用的靜態資料的同步的存取。|  
|[CComModule::m_hInst](#m_hinst)|包含模組的執行個體的控制代碼。|  
|[CComModule::m_hInstResource](#m_hinstresource)|根據預設，包含模組的執行個體的控制代碼。|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|根據預設，包含模組的執行個體的控制代碼。|  
|[CComModule::m_pObjMap](#m_pobjmap)|指向模組執行個體所維護的物件對應。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個類別已經過時，而且現在使用 ATL 程式碼產生精靈[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)衍生的類別。 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。 遵循的資訊是用於建立以 ATL 的版本還舊的應用程式 `CComModule` 仍然是 ATL 的一部分回溯功能。  
  
 `CComModule` 實作 COM 伺服器模組，可讓用戶端存取模組的元件。 `CComModule` 支援 （同處理序） 的 DLL 及 EXE (local) 的模組。  
  
 A`CComModule`執行個體會維護一組類別物件定義使用物件對應。 此物件的對應會實作為陣列`_ATL_OBJMAP_ENTRY`結構，和包含的資訊：  
  
-   輸入，並在系統登錄中移除物件的描述。  
  
-   Class factory 具現化物件。  
  
-   在元件中建立用戶端與根物件之間的通訊。  
  
-   執行類別物件的存留期管理。  
  
 當您執行 ATL COM AppWizard 時，精靈會自動產生`_Module`的全域執行個體`CComModule`或從其衍生的類別。 如需 ATL 專案精靈的詳細資訊，請參閱文章[ATL 專案建立](../../atl/reference/creating-an-atl-project.md)。  
  
 除了`CComModule`，ATL 提供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，它會實作 Exe 和 Windows 服務的 apartment model 模組。 衍生您的模組，從`CComAutoThreadModule`當您想要在多個 apartment 中建立物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="getclassobject"></a>  CComModule::GetClassObject  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>參數  
 `rclsid`  
 [in]建立物件的 CLSID。  
  
 `riid`  
 [in]所要求介面的 IID。  
  
 `ppv`  
 [out]所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppv`設**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 建立指定的 CLSID 的物件，並擷取這個物件的介面指標。  
  
 `GetClassObject` 只有使用 dll。  
  
##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`識別這個模組。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInst](#m_hinst)資料成員。  
  
##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInstResource](#m_hinstresource)資料成員。  
  
##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInstTypeLib](#m_hinsttypelib)資料成員。  
  
##  <a name="init"></a>  Init  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]物件的對應項目的陣列的指標。  
  
 `h`  
 [in]`HINSTANCE`傳遞至**DLLMain**或`WinMain`。  
  
 `plibid`  
 [in]與專案相關聯的類型程式庫的 LIBID 指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 初始化所有的資料成員。  
  
##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>備註  
 可確保物件對應至同步的存取。  
  
##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>備註  
 可確保同步處理的類型程式庫的存取。  
  
##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>備註  
 可確保視窗類別資訊，並在視窗建立期間使用的靜態資料的同步的存取。  
  
##  <a name="m_hinst"></a>  CComModule::m_hInst  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>備註  
 包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInst`至控制代碼傳遞給**DLLMain**或`WinMain`。  
  
##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>備註  
 根據預設，包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInstResource`至控制代碼傳遞給**DLLMain**或`WinMain`。 您可以明確設定`m_hInstResource`資源控制代碼。  
  
 [GetResourceInstance](#getresourceinstance)方法傳回的控制代碼儲存在`m_hInstResource`。  
  
##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>備註  
 根據預設，包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInstTypeLib`至控制代碼傳遞給**DLLMain**或`WinMain`。 您可以明確設定`m_hInstTypeLib`至類型程式庫的控制代碼。  
  
 [GetTypeLibInstance](#gettypelibinstance)方法傳回的控制代碼儲存在`m_hInstTypeLib`。  
  
##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>備註  
 指向模組執行個體所維護的物件對應。  
  
##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in]註冊物件的 CLSID。  
  
 `lpszProgID`  
 [in]與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]與物件相關聯的版本無關的 ProgID。  
  
 `nDescID`  
 [in]物件的描述的字串資源的識別項。  
  
 `dwFlags`  
 [in]指定要在登錄中輸入的執行緒模型。 可能的值為**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 輸入物件的標準類別註冊系統登錄中。  
  
 [UpdateRegistryClass](#updateregistryclass)方法呼叫`RegisterClassHelper`。  
  
##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwClsContext`  
 [in]指定要執行的類別物件的內容。 可能的值為**CLSCTX_INPROC_SERVER**， **CLSCTX_INPROC_HANDLER**，或**CLSCTX_LOCAL_SERVER**。 如需這些值的說明，請參閱[CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) Windows SDK 中。  
  
 `dwFlags`  
 [in]決定類別物件的連接類型。 可能的值為**REGCLS_SINGLEUSE**， **REGCLS_MULTIPLEUSE**，或**REGCLS_MULTI_SEPARATE**。 如需這些值的說明，請參閱[REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 讓其他應用程式可以連接到它，請向 OLE 註冊 EXE 類別物件。 這個方法僅用於 Exe。  
  
##  <a name="registerserver"></a>  CComModule::RegisterServer  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 [in]指出是否將註冊類型程式庫。 預設值是**FALSE**。  
  
 `pCLSID`  
 [in]指向 CLSID 要註冊的物件。 如果**NULL** （預設值），將註冊的物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 取決於`pCLSID`參數，更新系統登錄單一類別物件或物件對應中的所有物件。  
  
 如果`bRegTypeLib`是**TRUE**，類型程式庫資訊也會一併更新。  
  
 請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)如需有關如何將項目加入至物件對應資訊。  
  
 `RegisterServer` 將會自動呼叫**DLLRegisterServer** DLL 或`WinMain`以執行 exe **/RegServer**命令列選項。  
  
##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 [in]格式字串`"\\N"`，其中`N`是整數索引型別程式庫資源。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 將類型程式庫的相關資訊加入至系統登錄。  
  
 如果模組執行個體包含多個類型程式庫，使用這個方法的第二個版本，以指定應該使用哪一個類型程式庫。  
  
##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 移除類別的物件。 這個方法僅用於 Exe。  
  
##  <a name="term"></a>  Ccommodule:: Term  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。  
  
##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in]要移除註冊物件的 CLSID。  
  
 `lpszProgID`  
 [in]與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]與物件相關聯的版本無關的 ProgID。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 從系統登錄中移除物件的標準類別註冊。  
  
 [UpdateRegistryClass](#updateregistryclass)方法呼叫`UnregisterClassHelper`。  
  
##  <a name="unregisterserver"></a>  CComModule::UnregisterServer  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>參數  
 `bUnRegTypeLib`  
 如果**TRUE**，類型程式庫還有未註冊。  
  
 `pCLSID`  
 要移除註冊物件的 clsid 點。 如果**NULL** （預設值），在物件對應中的所有物件都將取消登錄。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 取決於`pCLSID`參數，取消登錄單一類別物件或物件對應中的所有物件。  
  
 `UnregisterServer` 將會自動呼叫**DLLUnregisterServer** DLL 或`WinMain`以執行 exe **/UnregServer**命令列選項。  
  
 請參閱[OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)如需有關如何將項目加入至物件對應資訊。  
  
##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 要註冊或取消註冊物件的 CLSID。  
  
 `lpszProgID`  
 與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 與物件相關聯的版本無關的 ProgID。  
  
 `nDescID`  
 物件的描述的字串資源的識別項。  
  
 `szDesc`  
 字串，包含物件的描述。  
  
 `dwFlags`  
 指定要在登錄中輸入的執行緒模型。 可能的值為**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
 `bRegister`  
 指出是否應該註冊物件。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如果`bRegister`是**TRUE**，這個方法在系統登錄中輸入物件的標準類別註冊。  
  
 如果`bRegister`是**FALSE**，它會移除物件的註冊。  
  
 值而定`bRegister`，`UpdateRegistryClass`呼叫  [RegisterClassHelper](#registerclasshelper)或[UnregisterClassHelper](#unregisterclasshelper)。  
  
 藉由指定[DECLARE_REGISTRY](registry-macros.md#declare_registry)巨集，`UpdateRegistryClass`會時要叫用自動處理物件對應。  
  
##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
virtual HRESULT UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```  
  
### <a name="parameters"></a>參數  
 `lpszRes`  
 [in]資源名稱。  
  
 `nResID`  
 [in]資源識別碼。  
  
 `bRegister`  
 [in]指出是否應該註冊物件。  
  
 `pMapEntries`  
 [in]儲存指令碼的可取代參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 < 備註 >，如需詳細資訊。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 執行指令碼中所指定的資源包含`lpszRes`或`nResID`。  
  
 如果`bRegister`是**TRUE**，這個方法會在系統登錄中註冊的物件; 否則，請取消登錄該物件。  
  
 藉由指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)巨集，`UpdateRegistryFromResourceD`會時要叫用自動處理物件對應。  
  
> [!NOTE]
>  在執行階段取代值，請勿指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列 **_ATL_REGMAP_ENTRIES**結構，其中每個項目都包含變數的預留位置搭配要在執行階段取代預留位置的值。 然後呼叫`UpdateRegistryFromResourceD`，並將陣列傳遞`pMapEntries`參數。 這樣會加入中的取代值 **_ATL_REGMAP_ENTRIES**的註冊機構取代對應的結構。  
  
> [!NOTE]
>  若要以靜態方式連結至 ATL 登錄元件 （登錄器），請參閱[UpdateRegistryFromResourceS](#updateregistryfromresources)。  
  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS  
 為準，ATL 7.0`CComModule`已過時： 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
virtual HRESULT UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszRes`  
 [in]資源名稱。  
  
 `nResID`  
 [in]資源識別碼。  
  
 `bRegister`  
 [in]指出是否應該註冊資源指令碼。  
  
 `pMapEntries`  
 [in]儲存指令碼的可取代參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 < 備註 >，如需詳細資訊。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 類似於[UpdateRegistryFromResourceD](#updateregistryfromresourced)除了`UpdateRegistryFromResourceS`建立靜態連結 ATL 登錄元件 （登錄器）。  
  
 `UpdateRegistryFromResourceS` 將會叫用自動處理物件對應時，提供您加入`#define _ATL_STATIC_REGISTRY`為您的 stdafx.h。  
  
> [!NOTE]
>  在執行階段取代值，請勿指定[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)或[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)巨集。 相反地，建立陣列 **_ATL_REGMAP_ENTRIES**結構，其中每個項目都包含變數的預留位置搭配要在執行階段取代預留位置的值。 然後呼叫`UpdateRegistryFromResourceS`，並將陣列傳遞`pMapEntries`參數。 這樣會加入中的取代值 **_ATL_REGMAP_ENTRIES**的註冊機構取代對應的結構。  
  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
