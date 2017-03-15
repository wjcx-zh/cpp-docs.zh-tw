---
title: "IConnectionPointContainerImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IConnectionPointContainerImpl
- ATL.IConnectionPointContainerImpl
- ATL.IConnectionPointContainerImpl<T>
- IConnectionPointContainerImpl
- ATL::IConnectionPointContainerImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 81a68cae1d961f2846c1a807432f22ae92ca3b89
ms.lasthandoff: 02/24/2017

---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 類別
這個類別會實作連接點容器來管理一堆[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IConnectionPointContainerImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|建立列舉值，可逐一查看支援可連接物件的連接點。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|擷取支援指定的 IID 的連接點的介面指標。|  
  
## <a name="remarks"></a>備註  
 `IConnectionPointContainerImpl`實作連接點容器來管理一堆[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。 `IConnectionPointContainerImpl`提供兩種用戶端可以呼叫來擷取可連接物件的相關資訊︰  
  
- `EnumConnectionPoints`可讓用戶端決定哪一個連出介面支援的物件。  
  
- `FindConnectionPoint`可讓用戶端決定物件是否支援特定的輸出介面。  
  
 ATL 中使用的連接點的相關資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
##  <a name="a-nameenumconnectionpointsa--iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints  
 建立列舉值，可逐一查看支援可連接物件的連接點。  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namefindconnectionpointa--iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint  
 擷取支援指定的 IID 的連接點的介面指標。  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [類別概觀](../../atl/atl-class-overview.md)

