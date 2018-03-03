---
title: "CAtlDllModuleT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 650924898532e352df30d7e8173620b974f30138
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT 類別
此類別代表模組 dll。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>參數  
 `T`  
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
|[CAtlDllModuleT::DllMain](#dllmain)|選擇性的進入點的動態連結程式庫 (DLL)。|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|將項目加入至系統登錄 DLL 中的物件。|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|在 DLL 中的物件系統登錄移除項目。|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|傳回 class factory。 所叫用[DllGetClassObject](#dllgetclassobject)。|  
  
## <a name="remarks"></a>備註  
 `CAtlDllModuleT`代表動態連結程式庫 (DLL) 模組，並提供使用的所有 DLL 專案函式。 此特製化的[CAtlModuleT](../../atl/reference/catlmodulet-class.md)類別包含登錄的支援。  
  
 如需 ATL 中模組的詳細資訊，請參閱[ATL 模組類別](../../atl/atl-module-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT  
 建構函式。  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT  
 解構函式。  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow  
 測試是否可以卸載 DLL。  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果它無法會傳回 S_OK，如果可以卸載 DLL 或 S_FALSE。  
  
##  <a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject  
 傳回 class factory。  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>參數  
 `rclsid`  
 建立物件的 CLSID。  
  
 `riid`  
 所要求介面的 IID。  
  
 `ppv`  
 所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppv`設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="dllmain"></a>CAtlDllModuleT::DllMain  
 選擇性的進入點的動態連結程式庫 (DLL)。  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>參數  
 `dwReason`  
 如果設定為 DLL_PROCESS_ATTACH、 DLL_THREAD_ATTACH 和 DLL_THREAD_DETACH 通知呼叫已停用。  
  
 *lpreserved，請*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 停用 DLL_THREAD_ATTACH 和呼叫可以有多個 Dll 的多執行緒應用程式的有用最佳化 DLL_THREAD_DETACH 通知，請經常建立和刪除的執行緒，Dll 不需要的這些執行緒層級通知附加/中斷連結。  
  
##  <a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer  
 將項目加入至系統登錄 DLL 中的物件。  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 如果類型程式庫註冊，則為 TRUE。 預設值為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer  
 在 DLL 中的物件系統登錄移除項目。  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>參數  
 `bUnRegTypeLib`  
 如果是從登錄中移除類型程式庫，則為 TRUE。 預設值為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getclassobject"></a>CAtlDllModuleT::GetClassObject  
 建立指定的 CLSID 的物件。  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>參數  
 `rclsid`  
 建立物件的 CLSID。  
  
 `riid`  
 所要求介面的 IID。  
  
 `ppv`  
 所識別的介面指標的指標`riid`。 如果物件不支援這個介面，`ppv`設為 NULL。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)且其包含回溯相容性。  
  
## <a name="see-also"></a>請參閱  
 [CAtlModuleT 類別](../../atl/reference/catlmodulet-class.md)   
 [CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
