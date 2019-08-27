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
ms.openlocfilehash: bd88fd5d00df0347c0bd2161129b8cfa3ca35406
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496086"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 類別

這個類別會執行連接點。

## <a name="syntax"></a>語法

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IConnectionPointImpl`的類別。

*piid*<br/>
連接點物件所代表之介面的 IID 指標。

*CDV*<br/>
管理連接的類別。 預設值為[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), 允許無限制的連接。 您也可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md), 它會指定固定的連線數目。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|建立連接點與接收之間的連接。|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|建立列舉值, 以逐一查看連接點的連接。|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|抓取連接點所表示之介面的 IID。|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|抓取可連線物件的介面指標。|
|[IConnectionPointImpl::Unadvise](#unadvise)|終止先前透過`Advise`建立的連接。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|管理連接點的連接。|

## <a name="remarks"></a>備註

`IConnectionPointImpl`會執行連接點, 以允許物件將傳出介面公開給用戶端。 用戶端會在稱為接收的物件上, 執行此介面。

ATL 會使用[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)來執行可連接的物件。 可連線物件內的每個連接點都代表*piid*所識別的輸出介面。 [類別*CDV* ] 會管理連接點與接收之間的連接。 每個連接都是由「cookie」唯一識別。

如需在 ATL 中使用連接點的詳細資訊, 請參閱[連接點](../../atl/atl-connection-points.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="advise"></a>IConnectionPointImpl:: Advise

建立連接點與接收之間的連接。

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>備註

使用[Unadvise](#unadvise)來終止連接呼叫。

請參閱 Windows SDK 中的[IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) 。

##  <a name="enumconnections"></a>IConnectionPointImpl:: EnumConnections

建立列舉值, 以逐一查看連接點的連接。

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) 。

##  <a name="getconnectioninterface"></a>IConnectionPointImpl:: GetConnectionInterface

抓取連接點所表示之介面的 IID。

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) 。

##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl:: GetConnectionPointContainer

抓取可連線物件的介面指標。

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) 。

##  <a name="m_vec"></a>IConnectionPointImpl:: m_vec

管理連接點物件與接收之間的連接。

```
CDV m_vec;
```

### <a name="remarks"></a>備註

根據預設, `m_vec`的類型是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)。

##  <a name="unadvise"></a>IConnectionPointImpl:: Unadvise

終止先前透過 [[通知](#advise)] 建立的連接。

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) 。

## <a name="see-also"></a>另請參閱

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[類別總覽](../../atl/atl-class-overview.md)
