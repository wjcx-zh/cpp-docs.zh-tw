---
title: CComObjectStack 類別
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327579"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack 類別

此類創建一個臨時 COM 物件,並為`IUnknown`它提供的骨骼實現。

## <a name="syntax"></a>語法

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>參數

*基地*<br/>
類派生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx,](../../atl/reference/ccomobjectrootex-class.md)以及來自要支援的物件的任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObject 堆疊:CComObject堆疊](#ccomobjectstack)|建構函式。|
|[CComObject 堆疊:*CComObject堆疊](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObjectStack::新增參考](#addref)|傳回零。 在除錯模式下,呼叫`_ASSERTE`。|
|[CComObjectStack::查詢介面](#queryinterface)|返回E_NOINTERFACE。 在除錯模式下,呼叫`_ASSERTE`。|
|[CComObjectStack::發佈](#release)|傳回零。 在除錯模式下,呼叫`_ASSERTE`。 ~|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|包含在建`CComObjectStack`譯 物件期間返回的 HRESULT。|

## <a name="remarks"></a>備註

`CComObjectStack`用於創建臨時 COM 物件,並提供`IUnknown`物件的屬性 實現。 通常,物件用作一個函數中的局部變數(即推送到堆疊上)。 由於物件在函數完成時被銷毀,因此不會執行引用計數以提高效率。

下面的範例展示如何建立函式式的 COM 物件:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

臨時物件`Tempobj`被推送到堆疊上,並在函數完成時自動消失。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Base`

`CComObjectStack`

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::新增參考

傳回零。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

傳回零。

### <a name="remarks"></a>備註

在除錯模式下,呼叫`_ASSERTE`。

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObject 堆疊:CComObject堆疊

建構函式。

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>備註

呼叫`FinalConstruct`,然後將[m_hResFinalConstruct](#m_hresfinalconstruct)設定`FinalConstruct`到傳回的 HRESULT。 如果您尚未從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)派生基類,則必須提供`FinalConstruct`您自己的方法。 此解構函式會呼叫 `FinalRelease`。

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObject 堆疊:*CComObject堆疊

解構函式。

```
CComObjectStack();
```

### <a name="remarks"></a>備註

釋放所有分配的資源,並調用[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

包含在`FinalConstruct``CComObjectStack`物件構造期間從調用返回的 HRESULT。

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::查詢介面

返回E_NOINTERFACE。

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>傳回值

返回E_NOINTERFACE。

### <a name="remarks"></a>備註

在除錯模式下,呼叫`_ASSERTE`。

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::發佈

傳回零。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

傳回零。

### <a name="remarks"></a>備註

在除錯模式下,呼叫`_ASSERTE`。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject 類別](../../atl/reference/ccomobject-class.md)<br/>
[CComObject 全球類別](../../atl/reference/ccomobjectglobal-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
