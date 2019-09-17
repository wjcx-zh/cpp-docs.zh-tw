---
title: CComCachedTearOffObject 類別
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497542"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject 類別

這個類別會針對卸載介面來實行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。

## <a name="syntax"></a>語法

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包容*<br/>
您的卸載類別，衍生自`CComTearOffObjectBase`和您想要卸載的物件所支援的介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|建構函式。|
|[CComCachedTearOffObject：： ~ CComCachedTearOffObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|遞增`CComCachedTearOffObject`物件的參考計數。|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|`m_contained::FinalConstruct`呼叫（脫離類別的方法）。|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|`m_contained::FinalRelease`呼叫（脫離類別的方法）。|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|傳回`IUnknown` `CComCachedTearOffObject`物件的指標，或傳回您的卸載類別（類別`contained`）上所要求的介面。|
|[CComCachedTearOffObject::Release](#release)|遞減`CComCachedTearOffObject`物件的參考計數，如果參考計數為0，則會將它終結。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|衍生`CComContainedObject`自您的卸載類別（類別`contained`）的物件。|

## <a name="remarks"></a>備註

`CComCachedTearOffObject`針對卸載介面執行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 這個類別與`CComTearOffObject`中的`CComCachedTearOffObject`不同，其本身`IUnknown`與擁有者物件的`IUnknown`不同（擁有者是要建立卸載的物件）。 `CComCachedTearOffObject`會在其`IUnknown`上維護自己的參考計數，並在其參考計數為零時刪除其本身。 不過，如果您查詢其任何卸載介面，則擁有者物件`IUnknown`的參考計數會遞增。

如果已具現化執行卸載的`CComCachedTearOffObject` 物件，並且重新查詢卸載介面，則會重複使用相同的物件。`CComCachedTearOffObject` 相反地，如果透過擁有者`CComTearOffObject`物件重新查詢由所執行的卸載介面，則會具現化另一個。 `CComTearOffObject`

Owner `FinalRelease`類別必須`Release` 在快`IUnknown`取的上執行並呼叫，這樣會遞減其參考計數。`CComCachedTearOffObject` 這會導致`CComCachedTearOffObject` `FinalRelease`呼叫，並刪除卸載。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="addref"></a>CComCachedTearOffObject：： AddRef

將`CComCachedTearOffObject`物件的參考計數遞增1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷和測試的值。

##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

建構函式。

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
在`IUnknown` 的`CComCachedTearOffObject`指標。

### <a name="remarks"></a>備註

初始化成員 [m_contained](#m_contained)。`CComContainedObject`

##  <a name="dtor"></a>CComCachedTearOffObject：： ~ CComCachedTearOffObject

解構函式。

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源，並呼叫[FinalRelease](#finalrelease)。

##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

呼叫`m_contained::FinalConstruct`以建立`m_contained`，這`CComContainedObject`是< 用來存取您的卸載類別所實作為介面`contained`的 > 物件。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

呼叫`m_contained::FinalRelease` free `m_contained`， `CComContainedObject` >物件。<  `contained`

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained

衍生自您的卸載類別的[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件。

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>參數

*包容*<br/>
在您的卸載類別，衍生自`CComTearOffObjectBase`和您想要卸載的物件所支援的介面。

### <a name="remarks"></a>備註

這些方法`m_contained`會透過快取的卸載`QueryInterface`物件、 `FinalConstruct`和`FinalRelease`，用來存取您的卸載類別中的卸載介面。

##  <a name="queryinterface"></a>CComCachedTearOffObject：： QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的 GUID。

*ppvObject*<br/>
脫銷*Iid*所識別之介面指標的指標，如果找不到介面，則為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果要求的介面是`IUnknown`，會傳回本身`IUnknown`的指標`CComCachedTearOffObject`，並遞增參考計數。 否則，會使用繼承自`CComObjectRootEx`的[InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface)方法，來查詢您的卸載類別上的介面。

##  <a name="release"></a>CComCachedTearOffObject：： Release

將參考計數遞減1，如果參考計數為0，則刪除`CComCachedTearOffObject`物件。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在非 debug 組建中，一律會傳回0。 在 [偵錯工具] 組建中，傳回可能有助於診斷或測試的值。

## <a name="see-also"></a>另請參閱

[CComTearOffObject 類別](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
