---
title: CComObjectStack 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c3e29c3eed99c95ee92841413ceaca6e17e8565
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755058"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack 類別

這個類別建立暫存的 COM 物件，並為它提供的架構實作`IUnknown`。

## <a name="syntax"></a>語法

```
template <class  Base>  
class CComObjectStack : public Base
```

#### <a name="parameters"></a>參數

*基底*  
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|建構函式。|
|[CComObjectStack:: ~ CComObjectStack](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|傳回零。 在偵錯模式中，呼叫`_ASSERTE`。|
|[CComObjectStack::QueryInterface](#queryinterface)|傳回 E_NOINTERFACE。 在偵錯模式中，呼叫`_ASSERTE`。|
|[CComObjectStack::Release](#release)|傳回零。 在偵錯模式中，呼叫`_ASSERTE`。 ~|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|包含在建構期間所傳回的 HRESULT`CComObjectStack`物件。|

## <a name="remarks"></a>備註

`CComObjectStack` 用來建立暫存的 COM 物件，並提供物件的架構實作`IUnknown`。 一般來說，物件用做為本機變數內有一個函式 （也就，推送到堆疊）。 因為函式完成時，會終結物件，參考計數不會執行提高效率。

下列範例示範如何建立 COM 物件，用於函式內：

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

暫存物件`Tempobj`推入堆疊和函式完成時，會自動消失。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComObjectStack`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="addref"></a>  CComObjectStack::AddRef

傳回零。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

傳回零。

### <a name="remarks"></a>備註

在偵錯模式中，呼叫`_ASSERTE`。

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

建構函式。

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>備註

呼叫`FinalConstruct`，然後設定[m_hResFinalConstruct](#m_hresfinalconstruct)所傳回的 HRESULT 來`FinalConstruct`。 如果您有不衍生的基底類別從[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)，您必須提供您自己`FinalConstruct`方法。 此解構函式會呼叫 `FinalRelease`。

##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack

解構函式。

```
CComObjectStack();
```

### <a name="remarks"></a>備註

釋放所有配置的資源並呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)。

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

包含從呼叫傳回的 HRESULT`FinalConstruct`的建構期間`CComObjectStack`物件。

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

傳回 E_NOINTERFACE。

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>傳回值

傳回 E_NOINTERFACE。

### <a name="remarks"></a>備註

在偵錯模式中，呼叫`_ASSERTE`。

##  <a name="release"></a>  CComObjectStack::Release

傳回零。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

傳回零。

### <a name="remarks"></a>備註

在偵錯模式中，呼叫`_ASSERTE`。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
[CComObject 類別](../../atl/reference/ccomobject-class.md)   
[CComObjectGlobal 類別](../../atl/reference/ccomobjectglobal-class.md)   
[類別概觀](../../atl/atl-class-overview.md)
