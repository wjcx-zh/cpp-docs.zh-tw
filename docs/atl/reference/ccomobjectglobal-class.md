---
title: CComObjectGlobal 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: ec3abd04ce72cce98dae72a1ed8cbb8d9fe72079
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267429"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal 類別

此類別會管理模組包含的參考計數程式`Base`物件。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>參數

*基底*<br/>
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|建構函式。|
|[CComObjectGlobal::~CComObjectGlobal](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|實作全域`AddRef`。|
|[CComObjectGlobal::QueryInterface](#queryinterface)|實作全域`QueryInterface`。|
|[CComObjectGlobal::Release](#release)|實作全域`Release`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含在建構期間所傳回的 HRESULT`CComObjectGlobal`物件。|

## <a name="remarks"></a>備註

`CComObjectGlobal` 管理模組包含的參考計數程式`Base`物件。 `CComObjectGlobal` 可確保只要不會釋放此模組，將不會刪除您的物件。 整個模組上的參考計數歸零時，只會移除您的物件。

例如，使用`CComObjectGlobal`，class factory 可以保存通用的全域物件共用的所有用戶端。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

物件的參考計數遞增 1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

值，這個值可能有助於診斷和測試。

### <a name="remarks"></a>備註

根據預設，`AddRef`呼叫`_Module::Lock`，其中`_Module`全域執行個體[CComModule](../../atl/reference/ccommodule-class.md)或從它衍生的類別。

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

建構函式。 呼叫`FinalConstruct`，然後設定[m_hResFinalConstruct](#m_hresfinalconstruct)要`HRESULT`所傳回`FinalConstruct`。

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>備註

如果您有不衍生的基底類別從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，您必須提供您自己`FinalConstruct`方法。 此解構函式會呼叫 `FinalRelease`。

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

解構函式。

```
CComObjectGlobal();
```

### <a name="remarks"></a>備註

釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

包含呼叫 HRESULT`FinalConstruct`的建構期間`CComObjectGlobal`物件。

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

擷取要求的介面指標的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*iid*<br/>
[in]所要求介面的 GUID。

*ppvObject*<br/>
[out]識別 iid，則為 NULL，如果找不到介面之介面指標的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

`QueryInterface` 只處理 COM 對應表格中的介面。

##  <a name="release"></a>  CComObjectGlobal::Release

物件的參考計數以 1 遞減。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在偵錯組建`Release`傳回值，這個值可能有助於診斷和測試。 在非偵錯組建中，`Release`一律會傳回 0。

### <a name="remarks"></a>備註

根據預設，`Release`呼叫`_Module::Unlock`，其中`_Module`全域執行個體[CComModule](../../atl/reference/ccommodule-class.md)或從它衍生的類別。

## <a name="see-also"></a>另請參閱

[CComObjectStack 類別](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
