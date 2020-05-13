---
title: CComContained 物件類別
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320789"
---
# <a name="ccomcontainedobject-class"></a>CComContained 物件類別

此類通過委派到所有者對象`IUnknown`的 實現 I[未知。](/windows/win32/api/unknwn/nn-unknwn-iunknown)

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
您的類別,衍生[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom 包含物件::Ccom包含物件](#ccomcontainedobject)|建構函式。 初始化指向擁有者物件的成員指標`IUnknown`。|
|[CCom 包含物件:*CCom包含物件](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 包含物件::新增參考](#addref)|增加擁有者物件的引用計數。|
|[CCom 包含物件:取得控制未知](#getcontrollingunknown)|檢索擁有者物件的`IUnknown`。|
|[CCom包含物件:查詢介面](#queryinterface)|檢索指向所有者物件上請求的介面的指標。|
|[CCom包含物件::發佈](#release)|對所有者物件的引用計數進行聲明。|

## <a name="remarks"></a>備註

ATL在`CComContainedObject`類[CComAggObject,CComPolyObject,](../../atl/reference/ccomaggobject-class.md)和[CComCachedTearOff 物件](../../atl/reference/ccomcachedtearoffobject-class.md)中使用。 [CComPolyObject](../../atl/reference/ccompolyobject-class.md) `CComContainedObject`實現[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown),通過委派到擁有`IUnknown`者物件的 。 (擁有者是聚合的外部物件,或者是為其創建拆解介面的物件。`CComContainedObject`呼叫`CComObjectRootEx`的`OuterQueryInterface``OuterAddRef`、`OuterRelease`和`Base`, 都透過繼承。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComContainedObject`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CCom 包含物件::新增參考

增加擁有者物件的引用計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CCom 包含物件::Ccom包含物件

建構函式。

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
[在]擁有者物件的`IUnknown`。

### <a name="remarks"></a>備註

將`m_pOuterUnknown`成員指標 (`Base`透過類別繼承)設定為*pv*。

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CCom 包含物件:*CCom包含物件

解構函式。

```
~CComContainedObject();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CCom 包含物件:取得控制未知

傳回`m_pOuterUnknown`儲存擁有者物件`IUnknown`的成員指標(透過*Base*類別)

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>傳回值

擁有者物件的`IUnknown`。

### <a name="remarks"></a>備註

如果`Base`已聲明[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏,則此方法可能是虛擬的。

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CCom包含物件:查詢介面

檢索指向所有者物件上請求的介面的指標。

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CCom包含物件::發佈

對所有者物件的引用計數進行聲明。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在除錯產生中`Release`,傳回可用於診斷或測試的值。 在非調試產生中,`Release`始終返回 0。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
