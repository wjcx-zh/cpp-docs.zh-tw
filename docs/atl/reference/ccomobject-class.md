---
title: CComObject 類別
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497140"
---
# <a name="ccomobject-class"></a>CComObject 類別

這個類別`IUnknown`會針對非匯總物件進行。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別, 以及您想要在物件上支援的其他任何介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|建構函式。|
|[CComObject::~CComObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObject::AddRef](#addref)|遞增物件上的參考計數。|
|[CComObject::CreateInstance](#createinstance)|靜止建立新`CComObject`的物件。|
|[CComObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|
|[CComObject::Release](#release)|遞減物件上的參考計數。|

## <a name="remarks"></a>備註

`CComObject`執行非匯總物件的[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 。 不過, 對`QueryInterface`、 `AddRef`和`Release`的呼叫會委派給`CComObjectRootEx`。

如需使用`CComObject`的詳細資訊, 請參閱[ATL COM 物件的基本概念一](../../atl/fundamentals-of-atl-com-objects.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComObject`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="addref"></a>  CComObject::AddRef

遞增物件上的參考計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

此函式會傳回物件上新遞增的參考計數。 這個值可能有助於診斷或測試。

##  <a name="ccomobject"></a>  CComObject::CComObject

此函式會遞增模組鎖定計數。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>參數

<em>void\*</em><br/>
在未使用這個未命名的參數。 它存在於與其他`CComXXXObjectXXX`的函式的對稱。

### <a name="remarks"></a>備註

此函式會將它遞減。

如果衍生的物件成功使用 new 運算子進行結構化, 則初始參考計數為0。 `CComObject` 若要將參考計數設定為適當的值 (1), 請呼叫[AddRef](#addref)函數。

##  <a name="dtor"></a>  CComObject::~CComObject

解構函式。

```
CComObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源、呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease), 並遞減模組鎖定計數。

##  <a name="createinstance"></a>  CComObject::CreateInstance

此靜態函式可讓您建立新的**CComObject <** `Base` **>** 物件, 而不會產生[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的額外負荷。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>參數

*pp*<br/>
脫銷指向**CComObject <** `Base` **>** 指標的指標。 如果`CreateInstance`不成功, *pp*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

傳回的物件具有的參考計數為零, 因此, `AddRef`當您完成時`Release` , 請立即呼叫, 然後使用釋放物件指標的參考。

如果您不需要直接存取物件, 但仍想要建立新的物件`CoCreateInstance`, 而沒有額外負荷, 請改用[CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

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
脫銷*Iid*所識別之介面指標的指標。 如果物件不支援這個介面, *ppvObject*會設定為 Null。

*pp*<br/>
脫銷類型`Q`所識別之介面指標的指標。 如果物件不支援這個介面, 則會將*pp*設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="release"></a>CComObject:: Release

遞減物件上的參考計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

此函數會傳回物件上新的遞減參考計數。 在 debug 組建中, 傳回值可能有助於診斷或測試。 在非 debug 組建中, `Release`一律會傳回0。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[類別總覽](../../atl/atl-class-overview.md)
