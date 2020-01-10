---
title: CComPolyObject 類別
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497145"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 類別

這個類別`IUnknown`會針對匯總或非匯總物件來執行。

## <a name="syntax"></a>語法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包容*<br/>
衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別，以及您想要在物件上支援的其他任何介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|建構函式。|
|[CComPolyObject：： ~ CComPolyObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|遞增物件的參考計數。|
|[CComPolyObject::CreateInstance](#createinstance)|靜止可讓您建立新的**CComPolyObject <** `contained` **>** 物件，而不會產生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的額外負荷。|
|[CComPolyObject::FinalConstruct](#finalconstruct)|執行的`m_contained`最後初始化。|
|[CComPolyObject::FinalRelease](#finalrelease)|執行的`m_contained`最後析構。|
|[CComPolyObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|
|[CComPolyObject::Release](#release)|遞減物件的參考計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|如果`IUnknown`物件已匯總，請將呼叫委派給外部未知，如果`IUnknown`未匯總物件，則委派給物件的。|

## <a name="remarks"></a>備註

`CComPolyObject`為匯總或非匯總物件執行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。

建立實例`CComPolyObject`時，會核取 [外部未知] 的值。 如果是 Null， `IUnknown`則會針對非匯總物件執行。 如果外部未知不是 Null， `IUnknown`則會針對匯總物件來執行。

使用`CComPolyObject`的優點是，您可以避免在模組中同時具有[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[CComObject](../../atl/reference/ccomobject-class.md) ，以處理匯總和非匯總案例。 單一`CComPolyObject`物件可處理這兩種情況。 這表示只會有一個 vtable 複本，而您的模組中會有一份函數複本。 如果您的 vtable 很大，這可能會大幅降低您的模組大小。 不過，如果您的 vtable 很小， `CComPolyObject`使用可能會產生稍微大一點的模組大小，因為它不會針對匯總或非匯總物件進行優化`CComAggObject` ， `CComObject`如同和。

如果您在物件的類別定義中指定 DECLARE_POLY_AGGREGATABLE 宏， `CComPolyObject`將會用來建立您的物件。 如果您使用 ATL 專案 Wizard 來建立完全控制或 Internet Explorer 控制項，則會自動宣告 DECLARE_POLY_AGGREGATABLE。

如果已匯總， `CComPolyObject`物件會有自己`IUnknown`的，與外部物件的`IUnknown`不同，並維護它自己的參考計數。 `CComPolyObject`會使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)來委派給外部未知的。

如需匯總的詳細資訊，請參閱[ATL COM 物件的基本概念一](../../atl/fundamentals-of-atl-com-objects.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="addref"></a>CComPolyObject：： AddRef

遞增物件上的參考計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

##  <a name="ccompolyobject"></a>CComPolyObject：： CComPolyObject

建構函式。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
在如果要匯總物件，則為外部未知的指標，如果物件未匯總，則為 Null。

### <a name="remarks"></a>備註

初始化資料成員 [m_contained](#m_contained)，並遞增模組鎖定計數。`CComContainedObject`

此函式會遞減模組鎖定計數。

##  <a name="dtor"></a>CComPolyObject：： ~ CComPolyObject

解構函式。

```
~CComPolyObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源、呼叫[FinalRelease](#finalrelease)，並遞減模組鎖定計數。

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

可讓您建立新的**CComPolyObject <** `contained` **>** 物件，而不會產生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的額外負荷。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>參數

*pp*<br/>
脫銷指向**CComPolyObject <** `contained` **>** 指標的指標。 如果`CreateInstance`不成功， *pp*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

傳回的物件具有的參考計數為零，因此， `AddRef`當您完成時`Release` ，請立即呼叫，然後使用釋放物件指標的參考。

如果您不需要直接存取物件，但仍想要建立新的物件`CoCreateInstance`，而沒有額外負荷，請改用[CComCoClass：： CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

##  <a name="finalconstruct"></a>CComPolyObject：： FinalConstruct

在物件結構的最後階段中呼叫，這個方法會在[m_contained](#m_contained)資料成員上執行任何最後的初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="finalrelease"></a>CComPolyObject：： FinalRelease

在物件損毀期間呼叫，這個方法會釋放[m_contained](#m_contained)資料成員。

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComPolyObject：： m_contained

衍生自您的類別的[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>參數

*包容*<br/>
在衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別，以及您想要在物件上支援的其他任何介面。

### <a name="remarks"></a>備註

`IUnknown`如果已匯總物件，則`IUnknown` 會將呼叫委派給外部未知，如果物件未匯總，則會委派給這個物件的。`m_contained`

##  <a name="queryinterface"></a>CComPolyObject：： QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>參數

*Q*<br/>
COM 介面。

*iid*<br/>
在所要求之介面的識別碼。

*ppvObject*<br/>
脫銷*Iid*所識別之介面指標的指標。 如果物件不支援這個介面， *ppvObject*會設定為 Null。

*pp*<br/>
脫銷所識別`__uuidof(Q)`之介面的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

若為匯總物件，如果要求的介面為`IUnknown`， `QueryInterface`會傳回匯總物件本身`IUnknown`的指標，並遞增參考計數。 否則，這個方法會透過`CComContainedObject`資料成員[m_contained](#m_contained)來查詢介面。

##  <a name="release"></a>CComPolyObject：： Release

遞減物件上的參考計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在 [偵錯工具`Release` ] 組建中，傳回可能有助於診斷或測試的值。 在 nondebug 組建中`Release` ，一律會傳回0。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[類別總覽](../../atl/atl-class-overview.md)
