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
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327636"
---
# <a name="ccomobject-class"></a>CComObject 類別

類實現`IUnknown`非聚合物件。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObject:CComObject](#ccomobject)|建構函式。|
|[CCom 物件:*CCom物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObject:addRef](#addref)|增加物件上的引用計數。|
|[CComObject:建立實體](#createinstance)|(靜態)創建新`CComObject`物件。|
|[CComObject:查詢介面](#queryinterface)|擷取所要求介面的指標。|
|[CComObject:發佈](#release)|對物件進行引用計數的取消。|

## <a name="remarks"></a>備註

`CComObject`實現非聚合物件的[I 未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown) 但是,對`QueryInterface`的`AddRef`調用`Release`將委派給`CComObjectRootEx`。

有關使用`CComObject`的詳細資訊,請參閱[ATL COM 物件的基礎](../../atl/fundamentals-of-atl-com-objects.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject:addRef

增加物件上的引用計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

此函數返回物件上新的增量引用計數。 此值可用於診斷或測試。

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject:CComObject

構造函數增加模組鎖計數。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>參數

<em>void\*</em><br/>
[在]不使用此未命名的參數。 它與其他`CComXXXObjectXXX`構造函數的對稱性存在。

### <a name="remarks"></a>備註

析構函數將其遞減。

如果使用新`CComObject`運算符成功構造派生物件,則初始**new**引用計數為 0。 要將引用計數設置為正確的值 (1),請調用[AddRef](#addref)函數。

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CCom 物件:*CCom物件

解構函式。

```
CComObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,調用[FinalRelease,](ccomobjectrootex-class.md#finalrelease)並遞減模組鎖計數。

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject:建立實體

此靜態函數允許您創建一個新的**CComObject<**`Base`**>** 物件,而無需[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的開銷。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>參數

*Pp*<br/>
[出]指向**CComObject 的指標<**`Base`**>** 指標。 如果`CreateInstance`不成功 *,pp*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

返回的物件的引用計數為零,因此立即調用`AddRef`,然後在完成後`Release`使用 釋放物件指標上的引用。

如果不需要直接存取該物件,但仍希望創建一個沒有開銷的新`CoCreateInstance`物件 ,請使用[CComCoClass:::createInstance。](../../atl/reference/ccomcoclass-class.md#createinstance)

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject:查詢介面

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject:發佈

對物件進行引用計數的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

此函數返回物件上的新遞減引用計數。 在調試生成中,返回值可用於診斷或測試。 在非調試產生中,`Release`始終返回 0。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPoly 物件類別](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[類別概觀](../../atl/atl-class-overview.md)
