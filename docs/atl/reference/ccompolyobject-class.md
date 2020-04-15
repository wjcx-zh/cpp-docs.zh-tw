---
title: CComPoly 物件類別
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
ms.openlocfilehash: e30afef455db5f83afca8ff9e515f39f015c3b8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327565"
---
# <a name="ccompolyobject-class"></a>CComPoly 物件類別

類實現`IUnknown`聚合或非聚合物件。

## <a name="syntax"></a>語法

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>參數

*包含*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom波利物件:CComPoly物件](#ccompolyobject)|建構函式。|
|[CCom波利物件:*CCom波利物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComPoly 物件:新增參考](#addref)|增加物件的引用計數。|
|[CComPoly 物件:建立實體](#createinstance)|(靜態)允許您創建新的**CComPolyObject<**`contained`**>** 物件,而無需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的開銷。|
|[CComPoly物件:最終建構](#finalconstruct)|執行`m_contained`的最後初始化。|
|[CComPoly物件:最終釋放](#finalrelease)|對執行`m_contained`的最後銷毀。|
|[CComPoly 物件:查詢介面](#queryinterface)|擷取所要求介面的指標。|
|[CComPoly 物件:發佈](#release)|取消物件的引用計數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComPoly 物件::m_contained](#m_contained)|委託`IUnknown`呼叫外部未知物件是聚合物件還是物件`IUnknown`( 如果物件未聚合)。|

## <a name="remarks"></a>備註

`CComPolyObject`實現聚合或非聚合物件的[I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown)

建立`CComPolyObject`的 實體時,將檢查外部未知值。 如果為 NULL,`IUnknown`則為非聚合物件實現。 如果外部未知值不是 NULL,`IUnknown`則為聚合對象實現。

使用`CComPolyObject`的優點是避免在模組中同時使用[CComAggObject](../../atl/reference/ccomaggobject-class.md)和[CComObject](../../atl/reference/ccomobject-class.md)來處理聚合和非聚合情況。 單個`CComPolyObject`物件處理這兩種情況。 這意味著模組中僅存在一個 vtable 副本和一個函數副本。 如果 vtable 很大,這可大幅減小模組大小。 但是,如果 vtable 很小`CComPolyObject`,則使用可能會導致模組大小稍大一些,因為它未針對聚合或非聚合物件進行優化`CComAggObject`,`CComObject`例如和 。

如果在物件的類定義中指定了DECLARE_POLY_AGGREGATABLE宏,`CComPolyObject`則將用於創建物件。 如果您使用 ATL 專案精靈建立完全控制或 Internet 資源管理器控制項,將自動聲明DECLARE_POLY_AGGREGATABLE。

如果聚合,則`CComPolyObject`物件具有其`IUnknown`自己的 ,與外部物件`IUnknown`的分離 ,並維護其自己的引用計數。 `CComPolyObject`使用[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)委託給外部未知物件。

有關聚合的詳細資訊,請參閱[ATL COM 物件的基礎](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPoly 物件:新增參考

增加物件上的引用計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CCom波利物件:CComPoly物件

建構函式。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
[在]如果要聚合物件,則指向外部未知指標;如果物件未聚合,則指向 NULL。

### <a name="remarks"></a>備註

初始化`CComContainedObject`資料成員[,m_contained,](#m_contained)並遞增模組鎖計數。

析構函數會聲明模組鎖計數。

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CCom波利物件:*CCom波利物件

解構函式。

```
~CComPolyObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,調用[FinalRelease,](#finalrelease)並遞減模組鎖計數。

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPoly 物件:建立實體

允許您創建新的**CComPolyObject<**`contained`**>** 物件,而無需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的開銷。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>參數

*Pp*<br/>
[出]指向**CComPolyObject 的指標<**`contained`**>** 指標。 如果`CreateInstance`不成功 *,pp*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

返回的物件的引用計數為零,因此立即調用`AddRef`,然後在完成後`Release`使用 釋放物件指標上的引用。

如果不需要直接存取該物件,但仍希望創建一個沒有開銷的新`CoCreateInstance`物件 ,請使用[CComCoClass:::createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPoly物件:最終建構

在物件構造的最後階段調用此方法對[m_contained](#m_contained)數據成員執行任何最終初始化。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPoly物件:最終釋放

在物件銷毀期間調用此方法釋放[m_contained](#m_contained)數據成員。

```
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPoly 物件::m_contained

衍生[CComContainedObject 物件](../../atl/reference/ccomcontainedobject-class.md)。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>參數

*包含*<br/>
[在]類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

### <a name="remarks"></a>備註

`IUnknown`如果對`m_contained`象 是聚合的,則通過調用委託給外部未知物件,如果物件未`IUnknown`聚合 ,則委託給此物件的調用。

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPoly 物件:查詢介面

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>參數

*Q*<br/>
COM 介面。

*Iid*<br/>
[在]要請求的介面的標識碼。

*ppvObject*<br/>
[出]指向*iid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObject*設定為 NULL。

*Pp*<br/>
[出]指向標識的介面的`__uuidof(Q)`指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

對於聚合物件,如果請求的介面為`IUnknown``QueryInterface`, 則返回指向聚合`IUnknown`物件自己的 指標,並遞增引用計數。 否則,此方法通過`CComContainedObject`數據成員[m_contained](#m_contained)查詢介面。

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPoly 物件:發佈

對物件進行引用計數的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在除錯產生中`Release`,傳回可用於診斷或測試的值。 在非調試生成中`Release`,始終返回 0。

## <a name="see-also"></a>另請參閱

[CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[類別概觀](../../atl/atl-class-overview.md)
