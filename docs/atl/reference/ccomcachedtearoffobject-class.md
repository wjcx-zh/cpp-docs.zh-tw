---
title: CComCachedTearOff物件類別
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
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748098"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOff物件類別

此類實現[「I未知」](/windows/win32/api/unknwn/nn-unknwn-iunknown)的拆解介面。

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

*包含*<br/>
您的拆解類,派生自`CComTearOffObjectBase`您希望拆解物件支援的介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCachedTearoff物件::CcomCachedTearoff物件](#ccomcachedtearoffobject)|建構函式。|
|[CComCachedTearoff物件::_CcomCachedTearoff物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCachedTearOff物件::添加參考](#addref)|增加`CComCachedTearOffObject`物件的引用計數。|
|[CComCachedTearOff物件::最終構造](#finalconstruct)|調用`m_contained::FinalConstruct`(分接類) 方法。|
|[CComCachedTearOff物件::最終發佈](#finalrelease)|調用`m_contained::FinalRelease`(分接類) 方法。|
|[CComCachedTearoff物件::查詢介面](#queryinterface)|返回指向`IUnknown``CComCachedTearOffObject`物件的的指標,或指向拆解類(類`contained`)上的請求介面。|
|[CComCachedTearOff物件::發佈](#release)|取消`CComCachedTearOffObject`物件的引用計數,並在引用計數為 0 時將其銷毀。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComCachedTearOff物件::m_contained](#m_contained)|派生`CComContainedObject`自拆解類(`contained`類 )的物件。|

## <a name="remarks"></a>備註

`CComCachedTearOffObject`實現[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)的拆解介面。 `CComTearOffObject`類不同於`CComCachedTearOffObject`具有其`IUnknown`自己的 、獨立於擁有者`IUnknown`物件的 (擁有者是為其創建撕掉的物件)。 `CComCachedTearOffObject`在其引用計數為零后,`IUnknown`在其上維護自己的引用計數並刪除自身。 但是,如果查詢其任何拆解介面,所有者物件的引用計數`IUnknown`將遞增。

如果實現`CComCachedTearOffObject`分淚的物件已實例化,並且再次查詢拆解介面,則重用同`CComCachedTearOffObject`一 物件。 相反,如果通過`CComTearOffObject`所有者物件再次查詢由 實現的分出介面,則將實例化另一`CComTearOffObject`個。

擁有者類`FinalRelease`必須實現和調`Release``IUnknown`用 的`CComCachedTearOffObject`快取的 。,這將遞減其引用計數。 這將導致調用`CComCachedTearOffObject``FinalRelease`並 刪除撕裂。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOff物件::添加參考

將`CComCachedTearOffObject`物件的引用計數增加1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷和測試的值。

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearoff物件::CcomCachedTearoff物件

建構函式。

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
[在]指向的`IUnknown`指標`CComCachedTearOffObject`。

### <a name="remarks"></a>備註

初始化`CComContainedObject`成員[,m_contained](#m_contained)。

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearoff物件::_CcomCachedTearoff物件

解構函式。

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,並調用[FinalRelease](#finalrelease)。

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOff物件::最終構造

呼叫`m_contained::FinalConstruct``m_contained`,`CComContainedObject`< `contained`用於存取撕裂類別的介面>物件。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOff物件::最終發佈

調用`m_contained::FinalRelease``m_contained`自由`CComContainedObject`< `contained`,> 物件。

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOff物件::m_contained

從拆解類別的[CComContainedObject 物件](../../atl/reference/ccomcontainedobject-class.md)。

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>參數

*包含*<br/>
[在]您的拆解類,派生自`CComTearOffObjectBase`您希望拆解物件支援的介面。

### <a name="remarks"></a>備註

方法`m_contained`繼承用於通過緩存的拆解物件`QueryInterface`的`FinalConstruct`和訪問拆解類中的拆解`FinalRelease`介面。

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearoff物件::查詢介面

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]請求的介面的 GUID。

*ppvObject*<br/>
[出]指向*iid*識別的介面指標,如果找不到介面,則指向 NULL 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果請求的介面為`IUnknown`,則返回`CComCachedTearOffObject`指向`IUnknown`的自己的指標,並遞增引用計數。 否則,使用`CComObjectRootEx`從繼承的內部[查詢介面](ccomobjectrootex-class.md#internalqueryinterface)方法查詢拆解類上的介面。

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOff物件::發佈

將引用計數減為 1,如果引用計數為 0,`CComCachedTearOffObject`則刪除 物件。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在非調試生成中,始終返回 0。 在調試生成中,返回可用於診斷或測試的值。

## <a name="see-also"></a>另請參閱

[CComTearoff 物件類別](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
