---
title: CComTearOffObject 類別
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: 3eee1d33d5eded75d8805584a24e6b6f396a8369
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833617"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 類別

這個類別會執行卸載式介面。

## <a name="syntax"></a>語法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
您的卸載類別（衍生自）， `CComTearOffObjectBase` 以及您想要卸載物件支援的介面。

ATL 會在兩個階段中執行其卸載介面： `CComTearOffObjectBase` 方法會處理參考計數和 `QueryInterface` ，同時實作為 `CComTearOffObject` [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComTearOffObject：： CComTearOffObject](#ccomtearoffobject)|建構函式。|
|[CComTearOffObject：： ~ CComTearOffObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComTearOffObject：： AddRef](#addref)|遞增物件的參考計數 `CComTearOffObject` 。|
|[CComTearOffObject：： QueryInterface](#queryinterface)|將指標傳回給您的卸載類別或擁有者類別上要求的介面。|
|[CComTearOffObject：： Release](#release)|遞減物件的參考計數 `CComTearOffObject` ，並將它終結。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法

|函式|描述|
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|建構函式。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 資料成員

|資料成員|描述|
|-|-|
|[m_pOwner](#m_powner)|`CComObject`從擁有者類別衍生的指標。|

## <a name="remarks"></a>備註

`CComTearOffObject` 將卸載式介面實作為個別的物件，只有在查詢該介面時才會具現化。 當其參考計數變成零時，會刪除卸載。 一般來說，您會針對很少使用的介面建立一個卸載介面，因為使用卸載會將 vtable 指標儲存在主要物件的所有實例中。

您應該從 `CComTearOffObjectBase` 您想要卸載物件所要支援的任何介面，衍生出執行卸載的類別。 `CComTearOffObjectBase` 範本化于擁有者類別和執行緒模型上。 Owner 類別是物件的類別，該物件會被實作為卸載。 如果您未指定執行緒模型，則會使用預設執行緒模型。

您應該為您的卸載類別建立 COM 對應。 當 ATL 具現化卸載時，它會建立 `CComTearOffObject<CYourTearOffClass>` 或 `CComCachedTearOffObject<CYourTearOffClass>` 。

例如，在 BEEPER 範例中， `CBeeper2` 類別是卸載的類別，而 `CBeeper` 類別是 owner 類別：

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComTearOffObject`

## <a name="requirements"></a>規格需求

**標頭：** atlcom.h。h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a> CComTearOffObject：： AddRef

將物件的參考計數遞增 `CComTearOffObject` 一。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能適用于診斷和測試的值。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a> CComTearOffObject：： CComTearOffObject

建構函式。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
在將轉換成物件指標的指標 `CComObject<Owner>` 。

### <a name="remarks"></a>備註

將擁有者的參考計數遞增一。

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a> CComTearOffObject：： ~ CComTearOffObject

解構函式。

```
~CComTearOffObject();
```

### <a name="remarks"></a>備註

釋出所有已配置的資源、呼叫 FinalRelease，並遞減模組鎖定計數。

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a> CComTearOffObject：： CComTearOffObjectBase

建構函式。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>備註

將 [m_pOwner](#m_powner) 成員初始化為 Null。

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a> CComTearOffObject：： m_pOwner

衍生自*擁有*者之[CComObject](../../atl/reference/ccomobject-class.md)物件的指標。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>參數

*擁有者*<br/>
在正在執行卸載的類別。

### <a name="remarks"></a>備註

在結構化期間，指標會初始化為 Null。

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a> CComTearOffObject：： QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
在所要求之介面的 IID。

*ppvObject*<br/>
擴展由 *iid*識別之介面指標的指標，如果找不到介面，則為 Null。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

先對您的卸載類別上的介面進行查詢。 如果介面不存在，則會查詢擁有者物件上的介面。 如果要求的介面為，則會傳回擁有者的 `IUnknown` `IUnknown` 。

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a> CComTearOffObject：： Release

將參考計數遞減1，如果參考計數為零，則會刪除 `CComTearOffObject` 。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>傳回值

在非 debug 組建中，一律會傳回零。 在 debug 組建中，會傳回可能有助於診斷或測試的值。

## <a name="see-also"></a>另請參閱

[CComCachedTearOffObject 類別](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
