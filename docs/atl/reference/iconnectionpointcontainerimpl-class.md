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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496016"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 類別

此類別會執行連接點容器, 以管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件的集合。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IConnectionPointContainerImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|建立列舉值, 以逐一查看可連線物件中支援的連接點。|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|抓取支援指定之 IID 之連接點的介面指標。|

## <a name="remarks"></a>備註

`IConnectionPointContainerImpl`執行連接點容器來管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)物件的集合。 `IConnectionPointContainerImpl`提供兩種方法, 讓用戶端可以呼叫以取得可連線物件的詳細資訊:

- `EnumConnectionPoints`可讓用戶端判斷物件支援的傳出介面。

- `FindConnectionPoint`可讓用戶端判斷物件是否支援特定的傳出介面。

如需在 ATL 中使用連接點的詳細資訊, 請參閱[連接點](../../atl/atl-connection-points.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

建立列舉值, 以逐一查看可連線物件中支援的連接點。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) 。

##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

抓取支援指定之 IID 之連接點的介面指標。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) 。

## <a name="see-also"></a>另請參閱

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[類別總覽](../../atl/atl-class-overview.md)
