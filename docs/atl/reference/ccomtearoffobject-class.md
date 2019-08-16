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
ms.openlocfilehash: 0d27a6fa3c0070cd32c78971a7544327c51d4393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496921"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject 類別

這個類別會執行一個卸載介面。

## <a name="syntax"></a>語法

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
您的卸載類別, 衍生自`CComTearOffObjectBase`和您想要卸載的物件所支援的介面。

ATL 會在兩個階段中執行其卸載的介面`CComTearOffObjectBase` : 方法會處理參考計數`QueryInterface`和, `CComTearOffObject`同時執行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|建構函式。|
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|遞增`CComTearOffObject`物件的參考計數。|
|[CComTearOffObject::QueryInterface](#queryinterface)|在您的卸載類別或擁有者類別上, 傳回所要求介面的指標。|
|[CComTearOffObject::Release](#release)|遞減`CComTearOffObject`物件的參考計數, 並將其損毀。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase 方法

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|建構函式。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase 資料成員

|||
|-|-|
|[m_pOwner](#m_powner)|從擁有者類別`CComObject`衍生的指標。|

## <a name="remarks"></a>備註

`CComTearOffObject`將卸載介面實作為個別的物件, 只有在查詢該介面時才會具現化。 當其參考計數變成零時, 會刪除卸載。 一般來說, 您會針對很少使用的介面建立一個中斷介面, 因為使用卸載功能會將 vtable 指標儲存在主要物件的所有實例中。

您應該從`CComTearOffObjectBase`和您想要卸載的物件所要支援的任何介面, 衍生一個執行卸載的類別。 `CComTearOffObjectBase`會範本化在擁有者類別和執行緒模型上。 擁有者類別是正在執行卸載的物件類別。 如果您未指定執行緒模型, 則會使用預設的執行緒模型。

您應該為您的卸載類別建立 COM 對應。 當 ATL 具現化卸載時, 它會建立`CComTearOffObject<CYourTearOffClass>`或`CComCachedTearOffObject<CYourTearOffClass>`。

例如, 在 BEEPER 範例中, `CBeeper2`類別是卸載類別, `CBeeper`而類別是擁有者類別:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComTearOffObject`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="addref"></a>CComTearOffObject:: AddRef

將`CComTearOffObject`物件的參考計數遞增一。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷和測試的值。

##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

建構函式。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
在將轉換成`CComObject<Owner>`物件指標的指標。

### <a name="remarks"></a>備註

將擁有者的參考計數遞增一。

##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject

解構函式。

```
~CComTearOffObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源、呼叫 FinalRelease, 並遞減模組鎖定計數。

##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

建構函式。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>備註

將[m_pOwner](#m_powner)成員初始化為 Null。

##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner

衍生自*Owner*的[CComObject](../../atl/reference/ccomobject-class.md)物件指標。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>參數

*主人*<br/>
在正在執行卸載的類別。

### <a name="remarks"></a>備註

在結構化期間, 指標會初始化為 Null。

##  <a name="queryinterface"></a>CComTearOffObject:: QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的 IID。

*ppvObject*<br/>
脫銷*Iid*所識別之介面指標的指標, 如果找不到介面, 則為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

會先查詢您的卸載類別介面。 如果介面不存在, 就會查詢擁有者物件上的介面。 如果要求的介面是`IUnknown`, `IUnknown`會傳回擁有者的。

##  <a name="release"></a>CComTearOffObject:: Release

將參考計數遞減一, 如果參考計數為零, 則會刪除`CComTearOffObject`。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>傳回值

在非 debug 組建中, 一律會傳回零。 在 [偵錯工具] 組建中, 傳回可能有助於診斷或測試的值。

## <a name="see-also"></a>另請參閱

[CComCachedTearOffObject 類別](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
