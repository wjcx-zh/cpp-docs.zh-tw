---
title: CAtlDllModuleT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86fae3c77f06ab7dd3fb2104eda928c1a72b8cc3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883540"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 類別
此類別代表模組的 dll。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>參數  
 *T*  
 您的類別衍生自`CAtlDllModuleT`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|建構函式。|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|測試是否可以卸載 DLL。|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|傳回 class factory。|  
|[CAtlDllModuleT::DllMain](#dllmain)|動態連結程式庫 (DLL) 的選擇性項目點。|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|將項目加入至系統登錄 DLL 中的物件。|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|在 DLL 中的物件的系統登錄中移除項目。|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|傳回 class factory。 藉由叫用[DllGetClassObject](#dllgetclassobject)。|  
  
## <a name="remarks"></a>備註  
 `CAtlDllModuleT` 代表動態連結程式庫 (DLL) 模組，並提供所有的 DLL 專案所使用的函式。 此特製化[CAtlModuleT](../../atl/reference/catlmodulet-class.md)類別包含註冊的支援。  
  
 如需有關在 ATL 中的模組的詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT  
 建構函式。  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>  CAtlDllModuleT:: ~ CAtlDllModuleT  
 解構函式。  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow  
 測試是否可以卸載 DLL。  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果它不會傳回 S_OK，如果可以卸載 DLL 或 S_FALSE。  
  
##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject  
 傳回 class factory。  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>參數  
 *rclsid*  
 若要建立之物件的 CLSID。  
  
 *riid*  
 要求的介面 IID。  
  
 *ppv*  
 所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppv*設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain  
 動態連結程式庫 (DLL) 的選擇性項目點。  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>參數  
 *dwReason*  
 如果設為 DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知呼叫已停用。  
  
 *lpreserved，請*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 一律會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 停用 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知呼叫可以有許多 Dll 的多執行緒應用程式有用的最佳化，，，經常建立和刪除執行緒，而其 Dll 不需要的這些執行緒層級通知附加/中斷連結。  
  
##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer  
 將項目加入至系統登錄 DLL 中的物件。  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 *bRegTypeLib*  
 如果型別程式庫是要註冊，則為 TRUE。 預設值為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer  
 在 DLL 中的物件的系統登錄中移除項目。  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 *bUnRegTypeLib*  
 如果型別程式庫是從登錄中移除，則為 TRUE。 預設值為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject  
 建立指定的 CLSID 的物件。  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>參數  
 *rclsid*  
 若要建立之物件的 CLSID。  
  
 *riid*  
 要求的介面 IID。  
  
 *ppv*  
 所識別之介面指標的指標*riid*。 如果物件不支援這個介面， *ppv*設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)且其包含回溯相容性。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)   
 [Catldllmodulet 類別](../../atl/reference/catlexemodulet-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
