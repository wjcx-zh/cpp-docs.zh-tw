---
title: CComObject 全球類別
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
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327628"
---
# <a name="ccomobjectglobal-class"></a>CComObject 全球類別

此類管理包含物件的`Base`模組上的引用計數。

## <a name="syntax"></a>語法

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObject 全球:CComObject 全球](#ccomobjectglobal)|建構函式。|
|[CComObject 全球:*CComObject 全球](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObjectGlobal::新增參考](#addref)|實現全域`AddRef`。|
|[CComObject 全域::查詢介面](#queryinterface)|實現全域`QueryInterface`。|
|[CComObject 全球:發佈](#release)|實現全域`Release`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|包含在建`CComObjectGlobal`譯 物件期間返回的 HRESULT。|

## <a name="remarks"></a>備註

`CComObjectGlobal`管理包含物件的`Base`模組上的引用計數。 `CComObjectGlobal`確保只要不釋放模組,您的物件就不會被刪除。 僅當整個模組上的引用計數為零時,才會刪除物件。

例如,使用`CComObjectGlobal`類工廠可以保存由其所有用戶端共用的通用全域物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::新增參考

將物件的引用計數增加1。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

可用於診斷和測試的值。

### <a name="remarks"></a>備註

預設情況下,`AddRef`呼`_Module::Lock`叫`_Module`, [CComModule](../../atl/reference/ccommodule-class.md)的全域實例或派生自它的類的位置。

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObject 全球:CComObject 全球

建構函式。 呼叫`FinalConstruct`,[m_hResFinalConstruct](#m_hresfinalconstruct)然後 m_hResFinalConstruct`HRESULT`設定`FinalConstruct`到傳回的 。

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>備註

如果您尚未從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)派生基類,則必須提供`FinalConstruct`您自己的方法。 此解構函式會呼叫 `FinalRelease`。

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObject 全球:*CComObject 全球

解構函式。

```
CComObjectGlobal();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,並調用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

包含在物件構造期間從調用`FinalConstruct``CComObjectGlobal`的 HRESULT。

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObject 全域::查詢介面

檢索指向請求的介面指標的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>參數

*Iid*<br/>
[在]請求的介面的 GUID。

*ppvObject*<br/>
[出]指向 iid 識別的介面指標,如果未找到介面,則指向 NULL 的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

`QueryInterface` 只處理 COM 對應表格中的介面。

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObject 全球:發佈

將物件的引用計數減少 1。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

在除錯產生中`Release`,傳回可用於診斷和測試的值。 在非調試產生中,`Release`始終返回 0。

### <a name="remarks"></a>備註

預設情況下,`Release`呼`_Module::Unlock`叫`_Module`, [CComModule](../../atl/reference/ccommodule-class.md)的全域實例或派生自它的類的位置。

## <a name="see-also"></a>另請參閱

[CComObjectStack 類別](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
