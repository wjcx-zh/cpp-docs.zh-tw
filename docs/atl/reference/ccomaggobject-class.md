---
title: CComAggObject 類別
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 8b05284104f9d2e5e7704bceaee6f8adf9a33aac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497663"
---
# <a name="ccomaggobject-class"></a>CComAggObject 類別

這個類別會實作為匯總物件的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面。 根據定義，匯總物件包含在外部物件中。 類別類似于[CComObject 類別](../../atl/reference/ccomobject-class.md)，不同之處在于它會公開可直接存取外部用戶端的介面。 `CComAggObject`

## <a name="syntax"></a>語法

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包容*<br/>
衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別，以及您想要在物件上支援的其他任何介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|建構函式。|
|[CComAggObject：： ~ CComAggObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|遞增匯總物件上的參考計數。|
|[CComAggObject::CreateInstance](#createinstance)|此靜態函式可讓您建立新的**CComAggObject <** `contained` **>** 物件，而不會產生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的額外負荷。|
|[CComAggObject::FinalConstruct](#finalconstruct)|執行的`m_contained`最後初始化。|
|[CComAggObject::FinalRelease](#finalrelease)|執行的`m_contained`最後析構。|
|[CComAggObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|
|[CComAggObject::Release](#release)|遞減匯總物件上的參考計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|委派`IUnknown`對外部未知的呼叫。|

## <a name="remarks"></a>備註

`CComAggObject`執行匯總物件的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 `CComAggObject`有自己`IUnknown`的介面，與外部物件的`IUnknown`介面分開，並維護它自己的參考計數。

如需匯總的詳細資訊，請參閱[ATL COM 物件的基本概念一](../../atl/fundamentals-of-atl-com-objects.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="addref"></a>CComAggObject：： AddRef

遞增匯總物件上的參考計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

##  <a name="ccomaggobject"></a>CComAggObject：： CComAggObject

建構函式。

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
在外部不明。

### <a name="remarks"></a>備註

初始化成員、[m_contained](#m_contained)，並遞增模組鎖定計數。`CComContainedObject`

此函式會遞減模組鎖定計數。

##  <a name="dtor"></a>CComAggObject：： ~ CComAggObject

解構函式。

```
~CComAggObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源、呼叫[FinalRelease](#finalrelease)，並遞減模組鎖定計數。

##  <a name="createinstance"></a>CComAggObject：： CreateInstance

此靜態函式可讓您建立新的**CComAggObject <** `contained` **>** 物件，而不會產生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的額外負荷。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>參數

*pp*<br/>
脫銷 **CComAggObject\<** **包含>** 指標的指標。 如果`CreateInstance`不成功， *pp*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

傳回的物件具有的參考計數為零，因此， `AddRef`當您完成時`Release` ，請立即呼叫，然後使用釋放物件指標的參考。

如果您不需要直接存取物件，但仍想要建立新的物件`CoCreateInstance`，而沒有額外負荷，請改用[CComCoClass：： CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

##  <a name="finalconstruct"></a>CComAggObject：： FinalConstruct

在物件結構的最後階段中呼叫，這個方法會在[m_contained](#m_contained)成員上執行任何最後的初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="finalrelease"></a>CComAggObject：： FinalRelease

在物件損毀期間呼叫，這個方法會釋放[m_contained](#m_contained)成員。

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComAggObject：： m_contained

衍生自您的類別的[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>參數

*包容*<br/>
在衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別，以及您想要在物件上支援的其他任何介面。

### <a name="remarks"></a>備註

所有`IUnknown` 透過`m_contained`的呼叫都會委派給外部未知。

##  <a name="queryinterface"></a>CComAggObject：： QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的識別碼。

*ppvObject*<br/>
脫銷*Iid*所識別之介面指標的指標。 如果物件不支援這個介面， *ppvObject*會設定為 Null。

*pp*<br/>
脫銷類型`Q`所識別之介面指標的指標。 如果物件不支援這個介面，則會將*pp*設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

如果要求的介面是`IUnknown`， `QueryInterface`會傳回匯總物件本身`IUnknown`的指標，並遞增參考計數。 否則，這個方法會透過`CComContainedObject` [m_contained](#m_contained)成員查詢介面。

##  <a name="release"></a>CComAggObject：： Release

遞減匯總物件上的參考計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在 [偵錯工具`Release` ] 組建中，傳回可能有助於診斷或測試的值。 在非 debug 組建中， `Release`一律會傳回0。

## <a name="see-also"></a>另請參閱

[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[類別總覽](../../atl/atl-class-overview.md)
