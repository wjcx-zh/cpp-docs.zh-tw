---
title: CComObjectNoLock 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497027"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock 類別

這個類別`IUnknown`會針對非匯總物件進行實作為, 但不會遞增此函式中的模組鎖定計數。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>參數

*群體*<br/>
衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)的類別, 以及您想要在物件上支援的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|建構函式。|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|遞增物件上的參考計數。|
|[CComObjectNoLock::QueryInterface](#queryinterface)|傳回所要求介面的指標。|
|[CComObjectNoLock::Release](#release)|遞減物件上的參考計數。|

## <a name="remarks"></a>備註

`CComObjectNoLock`類似于[CComObject](../../atl/reference/ccomobject-class.md) , 因為它會針對非匯總物件執行[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ;不過, `CComObjectNoLock`不會遞增在此函式中的模組鎖定計數。

ATL 會`CComObjectNoLock`在內部針對 class factory 使用。 一般來說, 您不會直接使用這個類別。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>需求

**標頭:** atlcom.h。h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

遞增物件上的參考計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可能有助於診斷或測試的值。

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

建構函式。 不同于[CComObject](../../atl/reference/ccomobject-class.md), 不會遞增模組鎖定計數。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>參數

<em>void\*</em><br/>
在未使用這個未命名的參數。 它存在於與其他`CComXXXObjectXXX`的函式的對稱。

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

解構函式。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>備註

釋放所有配置的資源, 並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
在所要求之介面的識別碼。

*ppvObject*<br/>
脫銷*Iid*所識別之介面指標的指標。 如果物件不支援這個介面, *ppvObject*會設定為 Null。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="release"></a>  CComObjectNoLock::Release

遞減物件上的參考計數。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在 [偵錯工具`Release` ] 組建中, 傳回可能有助於診斷或測試的值。 在非 debug 組建中, `Release`一律會傳回0。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
