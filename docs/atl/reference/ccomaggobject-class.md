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
ms.openlocfilehash: 9f05e83c8d0a1fd68fce3228dea9cfeab6183c96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321162"
---
# <a name="ccomaggobject-class"></a>CComAggObject 類別

此類實現聚合物件的[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面。 根據定義,聚合物件包含在外部物件中。 該`CComAggObject`類類似於[CComObject 類](../../atl/reference/ccomobject-class.md),只不過它公開了外部用戶端可直接訪問的介面。

## <a name="syntax"></a>語法

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包含*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComagg 物件:Ccomagg 物件](#ccomaggobject)|建構函式。|
|[CComAgg 物件:*CcomAgg 物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComAgg 物件:addRef](#addref)|增加聚合物件的引用計數。|
|[CComAgg 物件:建立實體](#createinstance)|此靜態函數允許您創建一個新的**CComAggObject<**`contained`**>** 物件,而無需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的開銷。|
|[CComAgg 物件:最終建構](#finalconstruct)|執行`m_contained`的最後初始化。|
|[CComAgg 物件:最終發佈](#finalrelease)|對執行`m_contained`的最後銷毀。|
|[CComAgg 物件:查詢介面](#queryinterface)|擷取所要求介面的指標。|
|[CComAgg 物件::發佈](#release)|對聚合物件取消引用計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComAgg 物件::m_contained](#m_contained)|委託`IUnknown`調用外部未知。|

## <a name="remarks"></a>備註

`CComAggObject`實現[聚合物件的 I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown) `CComAggObject`有自己的`IUnknown`介面,獨立於外部物件`IUnknown`的介面,並維護自己的引用計數。

有關聚合的詳細資訊,請參閱[ATL COM 物件的基礎](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAgg 物件:addRef

增加聚合物件的引用計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComagg 物件:Ccomagg 物件

建構函式。

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
[在]外部未知。

### <a name="remarks"></a>備註

初始化`CComContainedObject`成員[,m_contained,](#m_contained)並遞增模組鎖計數。

析構函數會聲明模組鎖計數。

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAgg 物件:*CcomAgg 物件

解構函式。

```
~CComAggObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,調用[FinalRelease,](#finalrelease)並遞減模組鎖計數。

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAgg 物件:建立實體

此靜態函數允許您創建一個新的**CComAggObject<**`contained`**>** 物件,而無需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的開銷。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>參數

*Pp*<br/>
[出]指向**CComAggObject\<的**指標<em>包含</em>**>** 指標。 如果`CreateInstance`不成功 *,pp*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

返回的物件的引用計數為零,因此立即調用`AddRef`,然後在完成後`Release`使用 釋放物件指標上的引用。

如果不需要直接存取該物件,但仍希望創建一個沒有開銷的新`CoCreateInstance`物件 ,請使用[CComCoClass:::createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAgg 物件:最終建構

在物件構造的最後階段調用此方法,對[m_contained](#m_contained)成員執行任何最終初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAgg 物件:最終發佈

在物件銷毀期間調用此方法釋放[m_contained](#m_contained)成員。

```
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAgg 物件::m_contained

衍生[CComContainedObject 物件](../../atl/reference/ccomcontainedobject-class.md)。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>參數

*包含*<br/>
[在]類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

### <a name="remarks"></a>備註

所有`IUnknown``m_contained`通過的呼叫都委託給外部未知。

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAgg 物件:查詢介面

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]要請求的介面的標識碼。

*ppvObject*<br/>
[出]指向*iid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObject*設定為 NULL。

*Pp*<br/>
[出]指向類型標識的介面指標`Q`的指標。 如果物件不支援此介面 *,pp*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果請求的介面為`IUnknown``QueryInterface`,則返回指向聚合物件`IUnknown`自己的 指標,並遞增引用計數。 否則,此方法通過`CComContainedObject`成員查詢介面[,m_contained](#m_contained)。

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAgg 物件::發佈

對聚合物件取消引用計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在除錯產生中`Release`,傳回可用於診斷或測試的值。 在非調試產生中,`Release`始終返回 0。

## <a name="see-also"></a>另請參閱

[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComPoly 物件類別](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[類別概觀](../../atl/atl-class-overview.md)
