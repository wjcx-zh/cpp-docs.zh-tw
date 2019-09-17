---
title: CComContainedObject 類別
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
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497325"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject 類別

這個類別會藉由委派給擁有者物件的`IUnknown`來實作為 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|建構函式。 將成員指標初始化為擁有者物件的`IUnknown`。|
|[CComContainedObject：： ~ CComContainedObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|遞增擁有者物件上的參考計數。|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|抓取擁有者物件的`IUnknown`。|
|[CComContainedObject::QueryInterface](#queryinterface)|抓取在擁有者物件上所要求之介面的指標。|
|[CComContainedObject::Release](#release)|遞減擁有者物件上的參考計數。|

## <a name="remarks"></a>備註

ATL 會`CComContainedObject`在[CComAggObject](../../atl/reference/ccomaggobject-class.md)、 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)和[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)類別中使用。 `CComContainedObject`藉由委派給擁有者物件的`IUnknown`來實作為 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。 （擁有者可以是匯總的外部物件，或是正在建立卸載介面的物件）。`CComContainedObject`呼叫的、`OuterQueryInterface`和全都會透過`Base`繼承。 `OuterAddRef` `CComObjectRootEx` `OuterRelease`

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComContainedObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="addref"></a>CComContainedObject：： AddRef

遞增擁有者物件上的參考計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

建構函式。

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
在擁有者物件的`IUnknown`。

### <a name="remarks"></a>備註

將成員指標（繼承`Base`自類別）設定為*pv。* `m_pOuterUnknown`

##  <a name="dtor"></a>CComContainedObject：： ~ CComContainedObject

解構函式。

```
~CComContainedObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

傳回保存擁有者物件`IUnknown`之的 成員指標（繼承自基類`m_pOuterUnknown` ）。

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>傳回值

擁有者物件的`IUnknown`。

### <a name="remarks"></a>備註

如果`Base`已宣告[DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)宏，這個方法可能是虛擬的。

##  <a name="queryinterface"></a>CComContainedObject：： QueryInterface

抓取在擁有者物件上所要求之介面的指標。

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

##  <a name="release"></a>CComContainedObject：： Release

遞減擁有者物件上的參考計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在 [偵錯工具`Release` ] 組建中，傳回可能有助於診斷或測試的值。 在非 debug 組建中， `Release`一律會傳回0。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
