---
title: "CAtlModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlModule
- CAtlModule
- ATL.CAtlModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
caps.latest.revision: 19
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
ms.sourcegitcommit: 5a06fc417902378c88e2e65a9b51ee5e4356a39d
ms.openlocfilehash: 75cb5b42cd6c9de14d9abf09b20a1e23716f1149
ms.lasthandoff: 02/24/2017

---
# <a name="catlmodule-class"></a>CAtlModule 類別
這個類別提供數個 ATL 模組類別所使用的方法。  
  
## <a name="syntax"></a>語法  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|建構函式。|  
|[CAtlModule:: ~ CAtlModule](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|覆寫這個方法，以將參數加入至 ATL 登錄元件 （登錄器） 取代對應。|  
|[CAtlModule::AddTermFunc](#addtermfunc)|加入新的函式，此模組結束時呼叫。|  
|[CAtlModule::GetGITPtr](#getgitptr)|傳回全域介面指標。|  
|[CAtlModule::GetLockCount](#getlockcount)|傳回的鎖定計數。|  
|[CAtlModule::Lock](#lock)|鎖定計數遞增。|  
|[CAtlModule::Term](#term)|釋放所有的資料成員。|  
|[CAtlModule::Unlock](#unlock)|減量鎖定計數。|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行指令碼包含在指定的資源，若要註冊或取消註冊物件。|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|這個方法會呼叫`UpdateRegistryFromResourceD`執行登錄更新。|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|執行指令碼包含在指定的資源，若要註冊或取消註冊物件。 這個方法會以靜態方式連結至 ATL 登錄元件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|包含目前模組的 GUID。|  
|[CAtlModule::m_pGIT](#m_pgit)|全域介面資料表的指標。|  
  
## <a name="remarks"></a>備註  
 這個類別由[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)， [CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)，和[CAtlServiceModuleT 類別](../../atl/reference/catlservicemodulet-class.md)分別提供 DLL 的應用程式、 EXE 應用程式和 Windows 服務的支援。  
  
 如需有關在 ATL 中模組的詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。  
  
 這個類別會取代過時[CComModule 類別](../../atl/reference/ccommodule-class.md)用在舊版的 ATL  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-nameaddcommonrgsreplacementsa--catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements  
 覆寫這個方法，以將參數加入至 ATL 登錄元件 （登錄器） 取代對應。  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>參數  
 *pRegistrar*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 可置換的參數允許的註冊機構的用戶端，以指定執行階段資料。 若要這樣做，註冊機構會維護取代對應到其中進入可置換的參數，在您的指令碼相關聯的值。 註冊機構會讓這些項目，在執行階段。  
  
 請參閱主題[使用可置換的參數 （註冊機構的前置處理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)如需詳細資訊。  
  
##  <a name="a-nameaddtermfunca--catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc  
 加入新的函式，此模組結束時呼叫。  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>參數  
 *pFunc*  
 若要新增函式的指標。  
  
 `dw`  
 使用者定義的資料傳遞至函式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-namecatlmodulea--catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule  
 建構函式。  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化資料成員，並起始關鍵區段周圍模組的執行緒。  
  
##  <a name="a-namedtora--catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule:: ~ CAtlModule  
 解構函式。  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。  
  
##  <a name="a-namegetgitptra--catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr  
 擷取全域介面資料表的指標。  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>參數  
 `ppGIT`  
 指標，此變數會接收全域介面資料表的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤代碼。 如果傳回 E_POINTER`ppGIT`等於 NULL。  
  
### <a name="remarks"></a>備註  
 如果全域介面資料表物件不存在，它建立，而且其位址會儲存在成員變數[CAtlModule::m_pGIT](#m_pgit)。  
  
 在偵錯組建，判斷提示就會發生錯誤，如果`ppGIT`等於 NULL，或如果無法取得全域介面資料表指標。  
  
 請參閱[IGlobalInterfaceTable](http://msdn.microsoft.com/library/windows/desktop/ms678517)全域介面資料表上的資訊。  
  
##  <a name="a-namegetlockcounta--catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount  
 傳回的鎖定計數。  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的鎖定計數。 這個值可能有助於診斷和偵錯。  
  
##  <a name="a-namelocka--catlmodulelock"></a><a name="lock"></a>CAtlModule::Lock  
 鎖定計數遞增。  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定計數遞增，並傳回更新的值。 這個值可能有助於診斷和偵錯。  
  
##  <a name="a-namemlibida--catlmodulemlibid"></a><a name="m_libid"></a>CAtlModule::m_libid  
 包含目前模組的 GUID。  
  
```
static GUID m_libid;
```  
  
##  <a name="a-namempgita--catlmodulempgit"></a><a name="m_pgit"></a>CAtlModule::m_pGIT  
 全域介面資料表的指標。  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="a-nameterma--catlmoduleterm"></a><a name="term"></a>CAtlModule::Term  
 釋放所有的資料成員。  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。 解構函式會呼叫這個方法。  
  
##  <a name="a-nameunlocka--catlmoduleunlock"></a><a name="unlock"></a>CAtlModule::Unlock  
 減量鎖定計數。  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 減量鎖定計數，並傳回更新的值。 這個值可能有助於診斷和偵錯。  
  
##  <a name="a-nameupdateregistryfromresourceda--catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD  
 執行指令碼包含在指定的資源，若要註冊或取消註冊物件。  
  
```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszRes`  
 資源名稱。  
  
 `nResID`  
 資源識別碼。  
  
 `bRegister`  
 **TRUE**如果應該註冊物件。**FALSE**否則。  
  
 `pMapEntries`  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %MODULE%。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 執行指令碼中所指定的資源包含*lpszRes 或 nResID*。 如果`bRegister`是**TRUE**，這個方法會登錄在系統登錄中的物件，否則從登錄中移除物件。  
  
 若要以靜態方式連結至 ATL 登錄元件 （登錄器），請參閱[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)。  
  
 這個方法會呼叫[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)和[IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister)。  
  
##  <a name="a-nameupdateregistryfromresourcedhelpera--catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper  
 這個方法會呼叫`UpdateRegistryFromResourceD`執行登錄更新。  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszRes`  
 資源名稱。  
  
 `bRegister`  
 指出是否應該註冊物件。  
  
 `pMapEntries`  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %MODULE%。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法提供實作[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)。  
  
##  <a name="a-nameupdateregistryfromresourcesa--catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS  
 執行指令碼包含在指定的資源，若要註冊或取消註冊物件。 這個方法會以靜態方式連結至 ATL 登錄元件。  
  
```
HRESULT WINAPI UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `nResID`  
 資源識別碼。  
  
 `lpszRes`  
 資源名稱。  
  
 `bRegister`  
 指出是否要登錄的資源指令碼。  
  
 `pMapEntries`  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %MODULE%。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用**NULL**預設值。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 類似於[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)除了`CAtlModule::UpdateRegistryFromResourceS`建立靜態連結 ATL 登錄元件 （登錄器）。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)   
 [登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)  

