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
ms.openlocfilehash: 9f84c022ac1dee34b6dca2931abb349eefb7d690
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495884"
---
# <a name="ccompolyobject-class"></a>CComPolyObject 類別

這個類別會實作`IUnknown`彙總或非彙總物件。

## <a name="syntax"></a>語法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包含*<br/>
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|建構函式。|
|[CComPolyObject:: ~ CComPolyObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|物件的參考計數會遞增。|
|[CComPolyObject::CreateInstance](#createinstance)|（靜態）可讓您建立新**CComPolyObject <** `contained` **>** 物件，而不需要的額外負荷[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。|
|[CComPolyObject::FinalConstruct](#finalconstruct)|執行最後的初始化`m_contained`。|
|[CComPolyObject::FinalRelease](#finalrelease)|執行最終解構`m_contained`。|
|[CComPolyObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|
|[CComPolyObject::Release](#release)|遞減物件的參考計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|委派`IUnknown`呼叫的外部未知，如果物件已彙總或`IUnknown`如果物件不會彙總的物件。|

## <a name="remarks"></a>備註

`CComPolyObject` 會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)彙總或非彙總物件。

執行個體時`CComPolyObject`會建立值的外部未知已核取。 如果它是 NULL，`IUnknown`實作非彙總的物件。 如果不是 NULL，外部未知`IUnknown`會彙總物件的實作。

使用的優點`CComPolyObject`避免擁有[CComAggObject](../../atl/reference/ccomaggobject-class.md)並[CComObject](../../atl/reference/ccomobject-class.md)處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 這表示只有一個複本的 vtable 和一份函式存在於您的模組。 如果您的 vtable 很大，這可以大幅降低您的模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`可能會導致稍微大一點的模組大小因為它不會最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。

如果在您的物件類別定義中，指定 DECLARE_POLY_AGGREGATABLE 巨集`CComPolyObject`會用來建立您的物件。 如果您使用 [ATL 專案精靈] 來建立完整控制權 」 或 「 Internet Explorer 的控制項，將會自動宣告 DECLARE_POLY_AGGREGATABLE。

如果彙總，`CComPolyObject`物件都有它自己`IUnknown`，為分開的外部物件`IUnknown`，並維護其本身的參考計數。 `CComPolyObject` 會使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委派給外部未知。

如需有關彙總的詳細資訊，請參閱[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="addref"></a>  CComPolyObject::AddRef

遞增參考計數物件上。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷或測試。

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

建構函式。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
[in]如果物件是彙總，或如果為 NULL 的外部未知的指標的物件，如果物件不會彙總。

### <a name="remarks"></a>備註

初始化`CComContainedObject`資料成員[m_contained](#m_contained)，並遞增模組鎖定計數。

解構函式會遞減模組鎖定計數。

##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject

解構函式。

```
~CComPolyObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源，呼叫[FinalRelease](#finalrelease)，並遞減模組鎖定計數。

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

可讓您建立新**CComPolyObject <** `contained` **>** 物件，而不需要的額外負荷[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>參數

*前置處理*<br/>
[out]指標**CComPolyObject <** `contained` **>** 指標。 如果`CreateInstance`不成功， *pp*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

傳回的物件擁有的參考計數為零，因此呼叫`AddRef`立即執行，然後使用`Release`釋放物件指標的參考，當您完成時。

如果您不需要直接存取物件，但仍想要建立新的物件，而不需要的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改。

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

在物件建構的最後階段期間呼叫，這個方法會執行任何最後的初始化上[m_contained](#m_contained)資料成員。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

在物件解構期間呼叫，這個方法會釋放[m_contained](#m_contained)資料成員。

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)物件衍生自您的類別。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>參數

*包含*<br/>
[in]您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。

### <a name="remarks"></a>備註

`IUnknown` 透過呼叫`m_contained`如果已彙總物件，或委派給外部未知`IUnknown`如果物件不會彙總此物件。

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

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
[in]所要求的介面識別碼。

*ppvObject*<br/>
[out]所識別之介面指標的指標*iid*。 如果物件不支援這個介面， *ppvObject*設為 NULL。

*前置處理*<br/>
[out]所識別之介面指標`__uuidof(Q)`。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

彙總的物件，如果要求的介面`IUnknown`，`QueryInterface`讓指標回到彙總物件本身`IUnknown`並遞增參考計數。 否則，這個方法會查詢透過介面`CComContainedObject`資料成員[m_contained](#m_contained)。

##  <a name="release"></a>  CComPolyObject::Release

遞減參考計數物件。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在偵錯組建`Release`傳回值，這個值可能有助於診斷或測試。 在非偵錯組建中，`Release`一律會傳回 0。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[類別概觀](../../atl/atl-class-overview.md)
