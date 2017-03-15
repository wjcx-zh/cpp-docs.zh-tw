---
title: "IRunnableObjectImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: 20
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
ms.openlocfilehash: a9b2698c195ac5bd709e6d40d3c30008d3fa26d4
ms.lasthandoff: 02/24/2017

---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 類別
這個類別會實作**IUnknown** ，並提供的預設實作[IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IRunnableObjectImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|傳回執行中控制項的 CLSID。 ATL 實作設定 CLSID `GUID_NULL` ，並傳回**E_UNEXPECTED**。|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|判斷控制項是否正在執行。 ATL 實作會傳回**TRUE**。|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|鎖定控制項的執行狀態。 ATL 實作會傳回`S_OK`。|  
|[IRunnableObjectImpl::Run](#run)|強制執行控制項。 ATL 實作會傳回`S_OK`。|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|表示控制項內嵌。 ATL 實作會傳回`S_OK`。|  
  
## <a name="remarks"></a>備註  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783)介面可讓容器，以判斷控制項是否正在執行，強制執行，或由於鎖定進入執行狀態。 類別`IRunnableObjectImpl`提供此介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="a-namegetrunningclassa--irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass  
 傳回執行中控制項的 CLSID。  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作集\* *lpClsid*至`GUID_NULL`，並傳回**E_UNEXPECTED**。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisrunninga--irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::IsRunning  
 判斷控制項是否正在執行。  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回**TRUE**。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namelockrunninga--irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning  
 鎖定控制項的執行狀態。  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回`S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameruna--irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Run  
 強制執行控制項。  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回`S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetcontainedobjecta--irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject  
 表示控制項內嵌。  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>傳回值  
 ATL 實作會傳回`S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

