---
title: CAtlModuleT 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
dev_langs:
- C++
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29088c56d7020b38febb96be7512771a258e25fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="catlmodulet-class"></a>CAtlModuleT 類別
這個類別會實作 ATL 模組。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別衍生自`CAtlModuleT`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|初始化資料成員包含目前模組的 GUID。|  
|[CAtlModuleT::RegisterAppId](#registerappid)|將 EXE 加入登錄。|  
|[CAtlModuleT::RegisterServer](#registerserver)|將服務加入至登錄。|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|從登錄中移除該 exe 檔。|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|從登錄移除服務。|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|更新登錄中的 EXE 資訊。|  
  
## <a name="remarks"></a>備註  
 `CAtlModuleT`衍生自[CAtlModule](../../atl/reference/catlmodule-class.md)，實作可執行檔 (EXE) 或服務 (EXE) ATL 模組。 可執行模組為本機的跨處理序伺服器，而服務模組是 Windows 啟動時，會在背景中執行的 Windows 應用程式。  
  
 `CAtlModuleT` 提供初始化、 註冊和取消註冊模組的支援。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT  
 建構函式。  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlModuleT::InitLibId](#initlibid)。  
  
##  <a name="initlibid"></a>  CAtlModuleT::InitLibId  
 初始化資料成員包含目前模組的 GUID。  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>備註  
 建構函式呼叫[CAtlModuleT::CAtlModuleT](#catlmodulet)。  
  
##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId  
 將 EXE 加入登錄。  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer  
 將服務加入至登錄。  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 如果類型程式庫註冊，則為 TRUE。 預設值為 FALSE。  
  
 `pCLSID`  
 指向 CLSID 要註冊的物件。 如果將註冊 NULL （預設值），在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId  
 從登錄中移除該 exe 檔。  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer  
 從登錄移除服務。  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bUnRegTypeLib`  
 如果類型程式庫也是用來取消登錄，則為 TRUE。  
  
 `pCLSID`  
 要移除註冊物件的 clsid 點。 如果將取消登錄 NULL （預設值），在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId  
 更新登錄中的 EXE 資訊。  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegister`  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlModule 類別](../../atl/reference/catlmodule-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
