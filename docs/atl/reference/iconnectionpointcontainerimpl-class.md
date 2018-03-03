---
title: "IConnectionPointContainerImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5e3a6ee6790c4fa0e93fe312d6a6b840b754a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 類別
這個類別會實作用於管理集合的連接點容器[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IConnectionPointContainerImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|建立列舉值逐一查看支援可連接物件的連接點。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|擷取支援指定的 IID 的連接點的介面指標。|  
  
## <a name="remarks"></a>備註  
 `IConnectionPointContainerImpl`實作連接點容器管理集合的[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。 `IConnectionPointContainerImpl`提供兩種用戶端可以呼叫以擷取可連接物件的相關資訊：  
  
- `EnumConnectionPoints`可讓用戶端決定哪些傳出介面物件支援。  
  
- `FindConnectionPoint`可讓用戶端決定物件是否支援特定的輸出介面。  
  
 ATL 中使用的連接點相關資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints  
 建立列舉值逐一查看支援可連接物件的連接點。  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) Windows SDK 中。  
  
##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint  
 擷取支援指定的 IID 的連接點的介面指標。  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [類別概觀](../../atl/atl-class-overview.md)
