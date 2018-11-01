---
title: IConnectionPointContainerImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: 247013322925ad6fe246b079bcff7e0521e5561d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551641"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 類別

這個類別會實作連接點容器來管理集合[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IConnectionPointContainerImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|建立列舉值以逐一查看支援可連接物件的連接點。|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|擷取支援指定的 IID 的連接點的介面指標。|

## <a name="remarks"></a>備註

`IConnectionPointContainerImpl` 實作連接點容器來管理集合[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件。 `IConnectionPointContainerImpl` 提供用戶端可以呼叫以擷取可連接物件的相關資訊的兩種：

- `EnumConnectionPoints` 允許用戶端，以判斷哪一個連出介面物件支援。

- `FindConnectionPoint` 允許用戶端，以判斷物件是否支援特定的輸出介面。

如需使用 ATL 中的連接點的資訊，請參閱文章[連接點](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

建立列舉值以逐一查看支援可連接物件的連接點。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>備註

請參閱[IConnectionPointContainer::EnumConnectionPoints](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) Windows SDK 中。

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

擷取支援指定的 IID 的連接點的介面指標。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>備註

請參閱[IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[類別概觀](../../atl/atl-class-overview.md)
