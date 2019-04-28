---
title: IConnectionPointImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: 54231a4229db9a9afeecad878d695814565d776b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275538"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 類別

這個類別會實作連接點。

## <a name="syntax"></a>語法

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IConnectionPointImpl`。

*piid*<br/>
指向 IID 的連接點物件所代表之介面的指標。

*CDV*<br/>
管理連接的類別。 預設值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，可讓連接無限制。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，指定固定的連接數目。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|建立連接點與接收之間的連線。|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|建立列舉值以逐一查看的連接點的連線。|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|擷取連接點所代表之介面的 IID。|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|擷取可連接物件的介面指標。|
|[IConnectionPointImpl::Unadvise](#unadvise)|會透過先前建立的連線終止`Advise`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|管理連接點的連線。|

## <a name="remarks"></a>備註

`IConnectionPointImpl` 實作連接點，可讓物件公開給用戶端的輸出介面。 用戶端會實作此介面上呼叫接收的物件。

使用 ATL [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)實作可連接物件。 可連接物件中的每一個連接點代表所識別的連出介面*piid*。 類別*CDV*管理之間的連接點和接收器的連接。 每個連線會識別"cookie"。

如需有關如何使用 ATL 中的連接點的詳細資訊，請參閱[連接點](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="advise"></a>  IConnectionPointImpl::Advise

建立連接點與接收之間的連線。

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>備註

使用[Unadvise](#unadvise)終止連線。

請參閱[IConnectionPoint::Advise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-advise) Windows SDK 中。

##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections

建立列舉值以逐一查看的連接點的連線。

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>備註

請參閱[IConnectionPoint::EnumConnections](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) Windows SDK 中。

##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface

擷取連接點所代表之介面的 IID。

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>備註

請參閱[IConnectionPoint::GetConnectionInterface](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) Windows SDK 中。

##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer

擷取可連接物件的介面指標。

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>備註

請參閱[IConnectionPoint::GetConnectionPointContainer](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) Windows SDK 中。

##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec

管理連接點物件與接收之間的連線。

```
CDV m_vec;
```

### <a name="remarks"></a>備註

根據預設，`m_vec`屬於型別[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)。

##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise

會透過先前建立的連線終止[Advise](#advise)。

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>備註

請參閱[iconnectionpoint::](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[類別概觀](../../atl/atl-class-overview.md)
