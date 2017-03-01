---
title: "CAtlModuleT 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlModuleT<T>
- ATL.CAtlModuleT
- ATL.CAtlModuleT<T>
- ATL::CAtlModuleT
- CAtlModuleT
dev_langs:
- C++
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 9c0c6a2302932df06db7166d83fe9a561dfe38ac
ms.lasthandoff: 02/24/2017

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
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|初始化資料成員，其中包含目前模組的 GUID。|  
|[CAtlModuleT::RegisterAppId](#registerappid)|將 EXE 加入登錄。|  
|[CAtlModuleT::RegisterServer](#registerserver)|將服務加入至登錄。|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|從登錄移除 EXE。|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|從登錄中移除服務。|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|更新登錄中的 EXE 資訊。|  
  
## <a name="remarks"></a>備註  
 `CAtlModuleT`衍生自[CAtlModule](../../atl/reference/catlmodule-class.md)，實作可執行檔 (EXE) 或服務 (EXE) ATL 模組。 可執行模組為本機、 跨處理序伺服器，而服務模組是 Windows 啟動時，會在背景中執行的 Windows 應用程式。  
  
 `CAtlModuleT`提供初始化、 註冊和取消註冊模組的支援。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="a-namecatlmoduleta--catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT  
 建構函式。  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>備註  
 呼叫[CAtlModuleT::InitLibId](#initlibid)。  
  
##  <a name="a-nameinitlibida--catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId  
 初始化資料成員，其中包含目前模組的 GUID。  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>備註  
 建構函式呼叫[CAtlModuleT::CAtlModuleT](#catlmodulet)。  
  
##  <a name="a-nameregisterappida--catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId  
 將 EXE 加入登錄。  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-nameregisterservera--catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer  
 將服務加入至登錄。  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 如果型別程式庫註冊，則為 TRUE。 預設值為 FALSE。  
  
 `pCLSID`  
 要註冊的物件的 CLSID 指標。 如果將註冊 NULL （預設值），在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-nameunregisterappida--catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId  
 從登錄移除 EXE。  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-nameunregisterservera--catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer  
 從登錄中移除服務。  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>參數  
 `bUnRegTypeLib`  
 如果型別程式庫也是要移除註冊，則為 TRUE。  
  
 `pCLSID`  
 要移除註冊物件的 CLSID 指標。 如果 NULL （預設值），在物件對應中的所有物件就會取消註冊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="a-nameupdateregistryappida--catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId  
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

