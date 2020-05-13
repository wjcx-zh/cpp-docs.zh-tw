---
title: IConnectionPointimpl 類別
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
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329847"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointimpl 類別

此類實現連接點。

## <a name="syntax"></a>語法

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`IConnectionPointImpl`。

*皮伊德*<br/>
指向連接點物件表示的介面 IID 的指標。

*CDV*<br/>
管理連接的類。 默認值為[CComDynamicUnkarray,](../../atl/reference/ccomdynamicunkarray-class.md)它允許無限制的連接。 您還可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md),它指定固定數量的連接。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPointimpl::建議](#advise)|在連接點和接收器之間建立連接。|
|[IConnectionPointimpl::Eners](#enumconnections)|建立枚舉器以迴圈透過連接點的連接。|
|[IConnection點impl::取得連接介面](#getconnectioninterface)|檢索連接點表示的介面的IID。|
|[IConnectionPointimpl::取得連接點容器](#getconnectionpointcontainer)|檢索指向可連接物件的介面指標。|
|[IConnectionPointimpl::取消建議](#unadvise)|終止以前通過`Advise`建立的連接。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[IConnectionPointimpl::m_vec](#m_vec)|管理連接點的連接。|

## <a name="remarks"></a>備註

`IConnectionPointImpl`實現一個連接點,它允許物件向用戶端公開傳出介面。 用戶端在稱為接收器的對象上實現此介面。

ATL 使用[IConnectionPoint容器Impl](../../atl/reference/iconnectionpointcontainerimpl-class.md)來實現可連接物件。 可連接物件中的每個連接點表示一個傳出介面,由*piid*標識。 *CDV*類管理連接點和接收器之間的連接。 每個連接都由"cookie"唯一標識。

有關在 ATL 中使用連接點的詳細資訊,請參閱文章[連接點](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointimpl::建議

在連接點和接收器之間建立連接。

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>備註

使用[「不建議」](#unadvise)終止連接呼叫。

請參閱[IConnectionPoint::Windows](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) SDK 中的建議。

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointimpl::Eners

建立枚舉器以迴圈透過連接點的連接。

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>備註

請參閱[IConnectPoint:Windows](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) SDK 中的枚舉連接。

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnection點impl::取得連接介面

檢索連接點表示的介面的IID。

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>備註

請參閱[IConnectPoint:獲取](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface)Windows SDK 中的連接介面。

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointimpl::取得連接點容器

檢索指向可連接物件的介面指標。

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>備註

請參閱[IConnectPoint:獲取](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer)Windows SDK 中的連接點容器。

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointimpl::m_vec

管理連接點物件和接收器之間的連接。

```
CDV m_vec;
```

### <a name="remarks"></a>備註

預設的項目`m_vec`, 是[CComDynamic Unkarray 類型](../../atl/reference/ccomdynamicunkarray-class.md)。

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointimpl::取消建議

終止以前通過[通知](#advise)建立的連接。

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>備註

請參閱[IConnectPoint::](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)在 Windows SDK 中取消建議。

## <a name="see-also"></a>另請參閱

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[類別概觀](../../atl/atl-class-overview.md)
