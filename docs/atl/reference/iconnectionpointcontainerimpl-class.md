---
title: IConnectionPoint容器Impl類
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
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329871"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPoint容器Impl類

此類實現連接點容器來管理[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件的集合。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IConnectionPointContainerImpl`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPoint 容器 impl::Enal](#enumconnectionpoints)|建立枚舉器以透過可連接物件中支援的連接點反覆運算。|
|[IConnectionPoint 容器 impl::尋找連接點](#findconnectionpoint)|檢索指向支援指定 IID 的連接點的介面指標。|

## <a name="remarks"></a>備註

`IConnectionPointContainerImpl`實現連接點容器以管理[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件的集合。 `IConnectionPointContainerImpl`提供了兩種方法,用戶端可以調用這些方法來檢索有關可連接對象的詳細資訊:

- `EnumConnectionPoints`允許客戶端確定物件支援哪個傳出介面。

- `FindConnectionPoint`允許客戶端確定物件是否支援特定的傳出介面。

有關在 ATL 中使用連接點的資訊,請參考文章[連接點](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPoint 容器 impl::Enal

建立枚舉器以透過可連接物件中支援的連接點反覆運算。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>備註

請參考[IConnectPoint 容器:Windows SDK 中的 ens 的 Ens SDK 的 ens 。](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints)

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPoint 容器 impl::尋找連接點

檢索指向支援指定 IID 的連接點的介面指標。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>備註

請參閱[IConnectPoint 容器:在](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)Windows SDK 中尋找連接點。

## <a name="see-also"></a>另請參閱

[IConnectionPoint 容器](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[類別概觀](../../atl/atl-class-overview.md)
