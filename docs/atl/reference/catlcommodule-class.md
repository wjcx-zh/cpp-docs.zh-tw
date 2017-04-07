---
title: "CAtlComModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
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
ms.openlocfilehash: 6b933b5388fccc2dc0e31d035aa7eb56de3b1866
ms.lasthandoff: 02/24/2017

---
# <a name="catlcommodule-class"></a>CAtlComModule 類別
這個類別會實作 COM 伺服器模組。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|建構函式。|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|呼叫這個方法來更新系統登錄中的物件對應每個物件。|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|呼叫這個方法來註冊類型程式庫。|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|呼叫此方法以移除物件對應中的每個物件的註冊。|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|呼叫這個方法來取消註冊類型程式庫。|  
  
## <a name="remarks"></a>備註  
 `CAtlComModule`會實作 COM 伺服器模組，可讓用戶端存取模組的元件。  
  
 這個類別會取代過時[CComModule](../../atl/reference/ccommodule-class.md)用在舊版的 ATL 類別 請參閱[ATL 模組類別](../../atl/atl-module-classes.md)如需詳細資訊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule  
 建構函式。  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化模組。  
  
##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule  
 解構函式。  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>備註  
 釋放所有的 class factory。  
  
##  <a name="registerserver"></a>CAtlComModule::RegisterServer  
 呼叫這個方法來更新系統登錄中的物件對應每個物件。  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 如果型別程式庫註冊，則為 TRUE。 預設值為 FALSE。  
  
 `pCLSID`  
 要註冊的物件的 CLSID 指標。 如果將註冊 NULL （預設值），在物件對應中的所有物件。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 全域函式會呼叫[AtlComModuleRegisterServer](http://msdn.microsoft.com/library/d11a0c91-0c56-4b1b-a5f5-1287970f798b)。  
  
##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib  
 呼叫這個方法來註冊類型程式庫。  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 格式字串"\\\N 」，其中 N 是型別程式庫資源的整數索引。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 將型別程式庫的相關資訊加入至系統登錄。 如果模組執行個體包含多個型別程式庫，請使用這個方法的第一個版本來指定應該使用哪一個型別程式庫。  
  
##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 呼叫此方法以移除物件對應中的每個物件的註冊。  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>參數  
 `bRegTypeLib`  
 如果要取消註冊類型程式庫，則為 TRUE。 預設值為 FALSE。  
  
 `pCLSID`  
 要移除註冊物件的 CLSID 指標。 如果 NULL （預設值），在物件對應中的所有物件就會取消註冊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 全域函式會呼叫[AtlComModuleUnregisterServer](http://msdn.microsoft.com/library/c4ef3da4-def7-4aaf-b005-573a02e389d5)。  
  
##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib  
 呼叫這個方法來取消註冊類型程式庫。  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 格式字串"\\\N 」，其中 N 是型別程式庫資源的整數索引。  
  
### <a name="remarks"></a>備註  
 移除系統登錄中的型別程式庫的相關資訊。 如果模組執行個體包含多個型別程式庫，請使用這個方法的第一個版本來指定應該使用哪一個型別程式庫。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [類別概觀](../../atl/atl-class-overview.md)

