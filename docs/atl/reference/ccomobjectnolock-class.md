---
title: CComObjectnolock 類別
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
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327621"
---
# <a name="ccomobjectnolock-class"></a>CComObjectnolock 類別

類實現`IUnknown`非聚合物件,但不增加構造函數中的模組鎖計數。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComobject 無鎖::Ccomobject 無鎖](#ccomobjectnolock)|建構函式。|
|[CComobject 無鎖::*CComobject 無鎖](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObjectnoLock::新增參考](#addref)|增加物件上的引用計數。|
|[CComObject 無鎖定::查詢介面](#queryinterface)|返回指向請求的介面的指標。|
|[CComObjectnoLock::發佈](#release)|對物件進行引用計數的取消。|

## <a name="remarks"></a>備註

`CComObjectNoLock`與[CComObject](../../atl/reference/ccomobject-class.md)類似,因為它為非聚合物件實現了[I 未知](/windows/win32/api/unknwn/nn-unknwn-iunknown);但是,`CComObjectNoLock`不會增加構造函數中的模組鎖計數。

ATL`CComObjectNoLock`在內部用於一流工廠。 通常,您不會直接使用此類。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectnoLock::新增參考

增加物件上的引用計數。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷或測試的值。

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComobject 無鎖::Ccomobject 無鎖

建構函式。 與[CComObject 不同](../../atl/reference/ccomobject-class.md),不增加模組鎖計數。

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>參數

<em>void\*</em><br/>
[在]不使用此未命名的參數。 它與其他`CComXXXObjectXXX`構造函數的對稱性存在。

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComobject 無鎖::*CComobject 無鎖

解構函式。

```
~CComObjectNoLock();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,並調用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObject 無鎖定::查詢介面

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]要請求的介面的標識碼。

*ppvObject*<br/>
[出]指向*iid*標識的介面指標的指標。 如果物件不支援此介面,*則 ppvObject*設定為 NULL。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectnoLock::發佈

對物件進行引用計數的取消。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在除錯產生中`Release`,傳回可用於診斷或測試的值。 在非調試產生中,`Release`始終返回 0。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
