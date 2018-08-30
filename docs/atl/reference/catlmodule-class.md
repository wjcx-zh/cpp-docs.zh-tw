---
title: CAtlModule 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4412e30316bd2d5f43eac4dddb062adb11dc6f6e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209997"
---
# <a name="catlmodule-class"></a>CAtlModule 類別
這個類別提供數個 ATL 模組類別所使用的方法。  
  
## <a name="syntax"></a>語法  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|建構函式。|  
|[CAtlModule:: ~ CAtlModule](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|覆寫這個方法，以將參數新增至 ATL 登錄元件 （登錄器） 取代對應。|  
|[CAtlModule::AddTermFunc](#addtermfunc)|加入新的函式，此模組結束時呼叫。|  
|[CAtlModule::GetGITPtr](#getgitptr)|傳回全域的介面指標。|  
|[CAtlModule::GetLockCount](#getlockcount)|傳回的鎖定計數。|  
|[CAtlModule::Lock](#lock)|鎖定計數遞增。|  
|[CAtlModule::Term](#term)|釋放所有的資料成員。|  
|[CAtlModule::Unlock](#unlock)|減量鎖定計數。|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|執行指令碼包含在指定的資源，以註冊或取消登錄的物件。|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|這個方法會呼叫`UpdateRegistryFromResourceD`執行登錄更新。|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|執行指令碼包含在指定的資源，以註冊或取消登錄的物件。 這個方法以靜態方式連結至 ATL 登錄元件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|包含目前模組的 GUID。|  
|[CAtlModule::m_pGIT](#m_pgit)|全域介面資料表指標。|  
  
## <a name="remarks"></a>備註  
 此類別由[CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)， [Catldllmodulet 類別](../../atl/reference/catlexemodulet-class.md)，並[CAtlServiceModuleT 類別](../../atl/reference/catlservicemodulet-class.md)為 DLL 的應用程式，EXE 應用程式，提供支援和Windows 服務，分別。  
  
 如需有關在 ATL 中的模組的詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。  
  
 這個類別會取代過時[CComModule 類別](../../atl/reference/ccommodule-class.md)用在舊版的 ATL  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements  
 覆寫這個方法，以將參數新增至 ATL 登錄元件 （登錄器） 取代對應。  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>參數  
 *pRegistrar*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 可置換的參數允許註冊機構的用戶端，來指定執行階段資料。 若要這樣做，註冊機構會維護取代對應至其中進入您的指令碼可置換的參數相關聯的值。 在註冊機構會讓這些項目，在執行階段。  
  
 請參閱主題[使用可置換的參數 （登錄器的前置處理器）](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)如需詳細資訊。  
  
##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc  
 加入新的函式，此模組結束時呼叫。  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>參數  
 *pFunc*  
 若要新增函式指標。  
  
 *dw*  
 使用者定義的資料，傳遞至函式。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="catlmodule"></a>  CAtlModule::CAtlModule  
 建構函式。  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化資料成員，並起始模組的執行緒周圍的重要區段。  
  
##  <a name="dtor"></a>  CAtlModule:: ~ CAtlModule  
 解構函式。  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。  
  
##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr  
 擷取全域介面資料表的指標。  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>參數  
 *ppGIT*  
 指標，此變數會接收全域介面資料表的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或在失敗的錯誤代碼。 如果，則會傳回 E_POINTER *ppGIT*等於 NULL。  
  
### <a name="remarks"></a>備註  
 如果 Global Interface Table 物件不存在，它會建立，而且它的位址儲存在成員變數[CAtlModule::m_pGIT](#m_pgit)。  
  
 在偵錯組建中，判斷提示就會發生錯誤，如果*ppGIT*等於 NULL，或如果無法取得全域介面資料表指標。  
  
 請參閱[IGlobalInterfaceTable](/windows/desktop/api/objidl/nn-objidl-iglobalinterfacetable)全域介面資料表上的資訊。  
  
##  <a name="getlockcount"></a>  CAtlModule::GetLockCount  
 傳回的鎖定計數。  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回的鎖定計數。 此值可能有助於診斷和偵錯。  
  
##  <a name="lock"></a>  CAtlModule::Lock  
 鎖定計數遞增。  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 鎖定計數遞增，並傳回更新的值。 此值可能有助於診斷和偵錯。  
  
##  <a name="m_libid"></a>  CAtlModule::m_libid  
 包含目前模組的 GUID。  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>  CAtlModule::m_pGIT  
 全域介面資料表指標。  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>  CAtlModule::Term  
 釋放所有的資料成員。  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的資料成員。 解構函式會呼叫這個方法。  
  
##  <a name="unlock"></a>  CAtlModule::Unlock  
 減量鎖定計數。  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>傳回值  
 減量鎖定計數，並傳回更新的值。 此值可能有助於診斷和偵錯。  
  
##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD  
 執行指令碼包含在指定的資源，以註冊或取消登錄的物件。  
  
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
 *lpszRes*  
 資源名稱。  
  
 *nResID*  
 資源識別碼。  
  
 *bRegister*  
 如果物件應該註冊;，則為 TRUE。FALSE 否則。  
  
 *pMapEntries*  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %模組。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 NULL 預設值。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 執行指令碼包含在所指定的資源*lpszRes 或 nResID*。 如果*bRegister*為 TRUE 時，這個方法會註冊在系統登錄中的物件; 否則為從登錄移除物件。  
  
 若要以靜態方式連結至 ATL 登錄元件 （登錄器），請參閱[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)。  
  
 這個方法會呼叫[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)並[IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister)。  
  
##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper  
 這個方法會呼叫`UpdateRegistryFromResourceD`執行登錄更新。  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 *lpszRes*  
 資源名稱。  
  
 *bRegister*  
 表示是否應該註冊的物件。  
  
 *pMapEntries*  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %模組。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 NULL 預設值。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法可實作[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)。  
  
##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS  
 執行指令碼包含在指定的資源，以註冊或取消登錄的物件。 這個方法以靜態方式連結至 ATL 登錄元件。  
  
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
 *nResID*  
 資源識別碼。  
  
 *lpszRes*  
 資源名稱。  
  
 *bRegister*  
 表示是否應該註冊資源指令碼。  
  
 *pMapEntries*  
 儲存指令碼的可置換的參數相關聯的值取代對應指標。 ATL 會自動使用 %模組。 若要使用其他可置換的參數，請參閱[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)。 否則，請使用 NULL 預設值。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 類似於[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)除了`CAtlModule::UpdateRegistryFromResourceS`建立靜態連結 ATL 登錄元件 （登錄器）。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)   
 [登錄元件 （登錄器）](../../atl/atl-registry-component-registrar.md)  
