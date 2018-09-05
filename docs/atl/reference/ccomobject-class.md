---
title: CComObject 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0600d675d37e2fed1d318645daaedcce5f80ed89
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752367"
---
# <a name="ccomobject-class"></a>CComObject 類別

這個類別會實作`IUnknown`非彙總的物件。

## <a name="syntax"></a>語法

```
template<class Base>  
class CComObject : public Base
```

#### <a name="parameters"></a>參數

*基底*  
您的類別，衍生自[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)或是[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，因為您想要在物件上支援從任何其他介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|建構函式。|
|[CComObject::~CComObject](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComObject::AddRef](#addref)|遞增參考計數物件上。|
|[CComObject::CreateInstance](#createinstance)|（靜態）建立新`CComObject`物件。|
|[CComObject::QueryInterface](#queryinterface)|擷取所要求介面的指標。|
|[CComObject::Release](#release)|遞減參考計數物件。|

## <a name="remarks"></a>備註

`CComObject` 會實作[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)非彙總的物件。 不過，呼叫`QueryInterface`， `AddRef`，並`Release`委派給`CComObjectRootEx`。

如需使用詳細資訊`CComObject`，請參閱文章[ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`Base`

`CComObject`

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="addref"></a>  CComObject::AddRef

遞增參考計數物件上。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>傳回值

此函數會傳回新的遞增的參考計數物件上。 此值可能適用於診斷或測試。

##  <a name="ccomobject"></a>  CComObject::CComObject

建構函式會遞增模組鎖定計數。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>參數

<em>void\*</em>  
[in]不使用這個未命名的參數。 存在與其他對稱`CComXXXObjectXXX`建構函式。

### <a name="remarks"></a>備註

解構函式會遞減它。

如果`CComObject`-使用成功建構衍生的物件**新**運算子，初始參考計數為 0。 若要設定為適當的值 (1) 的參考計數，請呼叫[AddRef](#addref)函式。

##  <a name="dtor"></a>  CComObject::~CComObject

解構函式。

```
CComObject();
```

### <a name="remarks"></a>備註

釋放所有配置的資源，呼叫[FinalRelease](ccomobjectrootex-class.md#finalrelease)，並遞減模組鎖定計數。  

##  <a name="createinstance"></a>  CComObject::CreateInstance

此靜態函式可讓您建立新**CComObject <** `Base` **>** 物件，而不需要的額外負荷[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>參數

*前置處理*  
[out]指標**CComObject <** `Base` **>** 指標。 如果`CreateInstance`不成功， *pp*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

傳回的物件擁有的參考計數為零，因此呼叫`AddRef`立即執行，然後使用`Release`釋放物件指標的參考，當您完成時。

如果您執行不需要直接存取物件，但仍想要建立新的物件，而不需要的額外負荷`CoCreateInstance`，使用[CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)改。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

擷取所要求介面的指標。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>參數

*iid*  
[in]所要求的介面識別碼。

*ppvObject*  
[out]所識別之介面指標的指標*iid*。 如果物件不支援這個介面， *ppvObject*設為 NULL。

*前置處理*  
[out]依類型識別之介面指標的指標`Q`。 如果物件不支援這個介面， *pp*設為 NULL。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

##  <a name="release"></a>  CComObject::Release

遞減參考計數物件。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>傳回值

此函數會傳回新的遞減參考計數物件上。 在偵錯組建中，傳回的值可能有助於診斷或測試。 在非偵錯組建中，`Release`一律會傳回 0。

## <a name="see-also"></a>另請參閱

[CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
[CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
[類別概觀](../../atl/atl-class-overview.md)
