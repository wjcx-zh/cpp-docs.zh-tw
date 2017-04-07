---
title: "CComModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 23
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d0d5f040d7c6fbe4a4d83da0d589e123588c6bb1
ms.lasthandoff: 03/17/2017

---
# <a name="ccommodule-class"></a>CComModule 類別
ATL 7.0 截至`CComModule`已被取代︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|建立指定的 CLSID 的物件。 只有 dll。|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|傳回 `m_hInst`。|  
|[CComModule::GetResourceInstance](#getresourceinstance)|傳回 `m_hInstResource`。|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|傳回 `m_hInstTypeLib`。|  
|[CComModule::Init](#init)|初始化資料成員。|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|輸入物件的標準類別登錄在系統登錄中。|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|註冊類別物件。 針對只有 Exe。|  
|[CComModule::RegisterServer](#registerserver)|更新系統登錄中的物件對應每個物件。|  
|[CComModule::RegisterTypeLib](#registertypelib)|註冊類型程式庫。|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|撤銷類別物件。 針對只有 Exe。|  
|[CComModule::Term](#term)|釋放資料成員。|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|物件的標準的類別註冊移除系統登錄中。|  
|[CComModule::UnregisterServer](#unregisterserver)|移除物件對應中的每個物件的註冊。|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|註冊或取消註冊物件的標準的類別註冊。|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行指令碼包含在指定的資源，若要註冊或取消註冊物件。|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|靜態連結 ATL 登錄元件。 執行指令碼包含在指定的資源，若要註冊或取消註冊物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|可確保已同步處理的存取物件的對應資訊。|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|可確保已同步處理的型別程式庫資訊的存取。|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|可確保視窗類別資訊和視窗建立期間使用的靜態資料的同步的存取。|  
|[CComModule::m_hInst](#m_hinst)|包含模組的執行個體的控制代碼。|  
|[CComModule::m_hInstResource](#m_hinstresource)|根據預設，包含模組的執行個體的控制代碼。|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|根據預設，包含模組的執行個體的控制代碼。|  
|[CComModule::m_pObjMap](#m_pobjmap)|模組執行個體所維護的物件對應至點。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個類別已經過時，而且現在使用 ATL 程式碼產生精靈[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)和[CAtlModule](../../atl/reference/catlmodule-class.md)衍生的類別。 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。 接下來的資訊適用於與 ATL 較舊版本建立的應用程式 `CComModule`仍是一部分的 ATL 回溯功能。  
  
 `CComModule`會實作 COM 伺服器模組，可讓用戶端存取模組的元件。 `CComModule`支援 （同處理序） 的 DLL 和 EXE (local) 模組。  
  
 A`CComModule`執行個體用來維護一組類別物件定義的物件對應。 此物件對應會實作為一組`_ATL_OBJMAP_ENTRY`結構，和包含的資訊︰  
  
-   輸入並移除系統登錄中的物件描述。  
  
-   Class factory 具現化物件。  
  
-   元件中建立用戶端與根物件之間的通訊。  
  
-   執行類別物件的存留期管理。  
  
 當您執行 ATL COM AppWizard 時，精靈會自動產生`_Module`，全域執行個體`CComModule`或從中衍生的類別。 如需 ATL 專案精靈 的詳細資訊，請參閱文章[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。  
  
 除了`CComModule`，ATL 還提供[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，可用來實作 Exe 和 Windows 服務的 apartment model 模組。 衍生您的模組，從`CComAutoThreadModule`當您想要在多個 apartment 中建立物件。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="getclassobject"></a>CComModule::GetClassObject  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
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
 [out]所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppv`設為**NULL**。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 建立指定 CLSID 的物件，並擷取這個物件的介面指標。  
  
 `GetClassObject`才能夠使用 dll。  
  
##  <a name="getmoduleinstance"></a>CComModule::GetModuleInstance  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`識別此模組。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInst](#m_hinst)資料成員。  
  
##  <a name="getresourceinstance"></a>CComModule::GetResourceInstance  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInstResource](#m_hinstresource)資料成員。  
  
##  <a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 `HINSTANCE`。  
  
### <a name="remarks"></a>備註  
 傳回[m_hInstTypeLib](#m_hinsttypelib)資料成員。  
  
##  <a name="init"></a>CComModule::Init  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 [in]物件對應項目的陣列的指標。  
  
 `h`  
 [in]`HINSTANCE`傳遞至**DLLMain**或`WinMain`。  
  
 `plibid`  
 [in]與專案相關聯的型別程式庫的 LIBID 指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 初始化所有的資料成員。  
  
##  <a name="m_csobjmap"></a>CComModule::m_csObjMap  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>備註  
 可確保物件對應到已同步處理的存取。  
  
##  <a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>備註  
 可確保已同步處理的類型程式庫的存取。  
  
##  <a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>備註  
 可確保視窗類別資訊，並在視窗的建立期間使用的靜態資料的同步的存取。  
  
##  <a name="m_hinst"></a>CComModule::m_hInst  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>備註  
 包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInst`至控制代碼傳遞至**DLLMain**或`WinMain`。  
  
##  <a name="m_hinstresource"></a>CComModule::m_hInstResource  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>備註  
 根據預設，包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInstResource`至控制代碼傳遞至**DLLMain**或`WinMain`。 您可以明確設定`m_hInstResource`資源控制代碼。  
  
 [GetResourceInstance](#getresourceinstance)方法傳回的控制代碼儲存在`m_hInstResource`。  
  
##  <a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>備註  
 根據預設，包含模組的執行個體的控制代碼。  
  
 [Init](#init)方法會設定`m_hInstTypeLib`至控制代碼傳遞至**DLLMain**或`WinMain`。 您可以明確設定`m_hInstTypeLib`型別程式庫的控制代碼。  
  
 [GetTypeLibInstance](#gettypelibinstance)方法傳回的控制代碼儲存在`m_hInstTypeLib`。  
  
##  <a name="m_pobjmap"></a>CComModule::m_pObjMap  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>備註  
 模組執行個體所維護的物件對應至點。  
  
##  <a name="registerclasshelper"></a>CComModule::RegisterClassHelper  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
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
 [in]要註冊之物件的 CLSID。  
  
 `lpszProgID`  
 [in]與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]與物件相關聯的版本無關的 ProgID。  
  
 `nDescID`  
 [in]如需物件的說明字串資源的識別項。  
  
 `dwFlags`  
 [in]指定要在登錄中輸入的執行緒模型。 可能的值為**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 輸入物件的標準類別登錄在系統登錄中。  
  
 [UpdateRegistryClass](#updateregistryclass)方法呼叫`RegisterClassHelper`。  
  
##  <a name="registerclassobjects"></a>CComModule::RegisterClassObjects  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwClsContext`  
 [in]指定要執行之類別物件的內容。 可能的值為**CLSCTX_INPROC_SERVER**， **CLSCTX_INPROC_HANDLER**，或**CLSCTX_LOCAL_SERVER**。 如需這些值的說明，請參閱[CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwFlags`  
 [in]決定連線類型，對類別物件。 可能的值為**REGCLS_SINGLEUSE**， **REGCLS_MULTIPLEUSE**，或**REGCLS_MULTI_SEPARATE**。 如需這些值的說明，請參閱[REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 讓其他應用程式可以連接到它，則您可以向 OLE EXE 類別物件。 這個方法僅用於 Exe。  
  
##  <a name="registerserver"></a>CComModule::RegisterServer  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 [in]指出是否將登錄型別程式庫。 預設值是**FALSE**。  
  
 `pCLSID`  
 [in]要註冊的物件的 CLSID 指標。 如果**NULL** （預設值），將會登錄在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 取決於`pCLSID`參數，會更新系統登錄單一類別物件或物件對應中的所有物件。  
  
 如果`bRegTypeLib`是**TRUE**，類型程式庫資訊也會一併更新。  
  
 請參閱[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)如需有關如何將項目加入至物件的對應資訊。  
  
 `RegisterServer`將會自動呼叫**DLLRegisterServer** DLL，或讓`WinMain`之以執行 EXE **/RegServer**命令列選項。  
  
##  <a name="registertypelib"></a>CComModule::RegisterTypeLib  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 [in]格式字串`"\\N"`，其中`N`是整數的型別程式庫資源的索引。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 將型別程式庫的相關資訊加入至系統登錄。  
  
 如果模組執行個體包含多個型別程式庫，請使用此方法的第二個版本來指定應該使用哪一個型別程式庫。  
  
##  <a name="revokeclassobjects"></a>CComModule::RevokeClassObjects  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 移除類別的物件。 這個方法僅用於 Exe。  
  
##  <a name="term"></a>CComModule::Term  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。  
  
##  <a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>參數  
 `clsid`  
 [in]要取消註冊之物件的 CLSID。  
  
 `lpszProgID`  
 [in]與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 [in]與物件相關聯的版本無關的 ProgID。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 物件的標準的類別註冊移除系統登錄中。  
  
 [UpdateRegistryClass](#updateregistryclass)方法呼叫`UnregisterClassHelper`。  
  
##  <a name="unregisterserver"></a>CComModule::UnregisterServer  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>參數  
 `bUnRegTypeLib`  
 如果**TRUE**，型別程式庫也已取消註冊。  
  
 `pCLSID`  
 要移除註冊物件的 CLSID 指標。 如果**NULL** （預設值），在物件對應中的所有物件將都會取消註冊。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 取決於`pCLSID`參數，取消登錄單一類別物件或物件對應中的所有物件。  
  
 `UnregisterServer`將會自動呼叫**DLLUnregisterServer** DLL，或讓`WinMain`之以執行 EXE **/UnregServer**命令列選項。  
  
 請參閱[OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c)如需有關如何將項目加入至物件的對應資訊。  
  
##  <a name="updateregistryclass"></a>CComModule::UpdateRegistryClass  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
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
 若要登錄或取消登錄物件的 CLSID。  
  
 `lpszProgID`  
 與物件相關的 ProgID。  
  
 `lpszVerIndProgID`  
 與物件相關聯的版本無關的 ProgID。  
  
 `nDescID`  
 物件的描述的字串資源識別碼。  
  
 `szDesc`  
 字串，包含物件的描述。  
  
 `dwFlags`  
 指定要在登錄中輸入的執行緒模型。 可能的值為**THREADFLAGS_APARTMENT**， **THREADFLAGS_BOTH**，或**AUTPRXFLAG**。  
  
 `bRegister`  
 指出是否應該註冊物件。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如果`bRegister`是**TRUE**，這個方法會進入物件的標準類別登錄在系統登錄中。  
  
 如果`bRegister`是**FALSE**，它會移除物件的註冊。  
  
 值而定`bRegister`，`UpdateRegistryClass`呼叫是[RegisterClassHelper](#registerclasshelper)或[UnregisterClassHelper](#unregisterclasshelper)。  
  
 藉由指定[DECLARE_REGISTRY](http://msdn.microsoft.com/library/89b8949b-5c27-4a9c-8a51-ad276bba3a54)巨集，`UpdateRegistryClass`就會叫用自動處理物件對應時。  
  
##  <a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
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
 [in]儲存指令碼的可置換的參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 < 備註 > 以取得詳細資料。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 執行指令碼中所指定的資源包含`lpszRes`或`nResID`。  
  
 如果`bRegister`是**TRUE**，這個方法會登錄在系統登錄中的物件; 否則它會移除註冊物件。  
  
 藉由指定[DECLARE_REGISTRY_RESOURCE](http://msdn.microsoft.com/library/7ac11498-8ee2-4156-8df2-7076f7ddda8b)或[DECLARE_REGISTRY_RESOURCEID](http://msdn.microsoft.com/library/65bf3576-5396-416e-ba48-e14b3236c49b)巨集，`UpdateRegistryFromResourceD`就會叫用自動處理物件對應時。  
  
> [!NOTE]
>  在執行階段中替換成取代值，並指定`DECLARE_REGISTRY_RESOURCE`或`DECLARE_REGISTRY_RESOURCEID`巨集。 相反地，建立陣列**_ATL_REGMAP_ENTRIES**與要在執行階段取代預留位置的值配對的結構，其中每個項目都包含變數的預留位置。 然後呼叫`UpdateRegistryFromResourceD`，傳遞陣列`pMapEntries`參數。 這會將新增中的取代值**_ATL_REGMAP_ENTRIES**註冊機構的取代對應的結構。  
  
> [!NOTE]
>  若要以靜態方式連結至 ATL 登錄元件 （登錄器），請參閱[UpdateRegistryFromResourceS](#updateregistryfromresources)。  
  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
##  <a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResourceS  
 ATL 7.0 截至`CComModule`已過時︰ 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
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
 [in]指出是否要登錄的資源指令碼。  
  
 `pMapEntries`  
 [in]儲存指令碼的可置換的參數相關聯的值取代對應指標。 會自動使用 ATL `%MODULE%`。 若要使用其他可置換的參數，請參閱 < 備註 > 以取得詳細資料。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 類似於[UpdateRegistryFromResourceD](#updateregistryfromresourced)除了`UpdateRegistryFromResourceS`建立靜態連結 ATL 登錄元件 （登錄器）。  
  
 `UpdateRegistryFromResourceS`將會叫用自動處理物件對應時，提供您加入`#define _ATL_STATIC_REGISTRY`到您的 stdafx.h。  
  
> [!NOTE]
>  在執行階段中替換成取代值，並指定[DECLARE_REGISTRY_RESOURCE](http://msdn.microsoft.com/library/7ac11498-8ee2-4156-8df2-7076f7ddda8b)或[DECLARE_REGISTRY_RESOURCEID](http://msdn.microsoft.com/library/65bf3576-5396-416e-ba48-e14b3236c49b)巨集。 相反地，建立陣列**_ATL_REGMAP_ENTRIES**與要在執行階段取代預留位置的值配對的結構，其中每個項目都包含變數的預留位置。 然後呼叫`UpdateRegistryFromResourceS`，傳遞陣列`pMapEntries`參數。 這會將新增中的取代值**_ATL_REGMAP_ENTRIES**註冊機構的取代對應的結構。  
  
 如需可置換的參數和指令碼的詳細資訊，請參閱文章[ATL 登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

