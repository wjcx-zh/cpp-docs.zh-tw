---
title: CComUnkArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComUnkArray
- ATLCOM/ATL::CComUnkArray
- ATLCOM/ATL::CComUnkArray::CComUnkArray
- ATLCOM/ATL::CComUnkArray::Add
- ATLCOM/ATL::CComUnkArray::begin
- ATLCOM/ATL::CComUnkArray::end
- ATLCOM/ATL::CComUnkArray::GetCookie
- ATLCOM/ATL::CComUnkArray::GetUnknown
- ATLCOM/ATL::CComUnkArray::Remove
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cab0ea4ecf4bfabede365b9e0fbc9d4a02e2515
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057446"
---
# <a name="ccomunkarray-class"></a>CComUnkArray 類別

這個類別會儲存`IUnknown`指標，並設計來做為參數[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。

## <a name="syntax"></a>語法

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>參數

*nMaxSize*<br/>
最大數目`IUnknown`可保存於靜態陣列的指標。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComUnkArray::CComUnkArray](#ccomunkarray)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComUnkArray::Add](#add)|呼叫這個方法來加入`IUnknown`陣列的指標。|
|[CComUnkArray::begin](#begin)|讓指標回到第一個`IUnknown`集合中的指標。|
|[CComUnkArray::end](#end)|讓指標回到越過最後一個`IUnknown`集合中的指標。|
|[CComUnkArray::GetCookie](#getcookie)|呼叫此方法，以取得相關聯的 cookie 指定`IUnknown`指標。|
|[CComUnkArray::GetUnknown](#getunknown)|呼叫這個方法來取得`IUnknown`與指定的 cookie 相關聯的指標。|
|[CComUnkArray::Remove](#remove)|呼叫這個方法來移除`IUnknown`從陣列的指標。|

## <a name="remarks"></a>備註

`CComUnkArray` 保留固定的數目的`IUnknown`指標，每個介面的連接上的點。 `CComUnkArray` 可用的參數當做[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別。 `CComUnkArray<1>` 是的樣板特製化`CComUnkArray`，已經過最佳化，一個連接點。

`CComUnkArray`方法[開始](#begin)並[結束](#end)可用來循環 （例如，當引發事件時） 的所有連接點。

請參閱[新增連接點物件](../../atl/adding-connection-points-to-an-object.md)如需有關自動建立連接點 proxy。

> [!NOTE]
> **附註**類別[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)正由**加入類別**精靈建立具有連接點的控制項時。 如果您想要以手動方式指定連接點的數目，變更 從參考`CComDynamicUnkArray`要`CComUnkArray<` *n* `>`，其中*n*是連接點的數目必要的。

## <a name="requirements"></a>需求

**標頭：** atlcom.h

##  <a name="add"></a>  CComUnkArray::Add

呼叫這個方法來加入`IUnknown`陣列的指標。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
呼叫這個方法來加入`IUnknown`陣列的指標。

### <a name="return-value"></a>傳回值

傳回陣列是否不能夠容納新的指標，以新加入的指標或 0 相關聯的 cookie。

##  <a name="begin"></a>  CComUnkArray::begin

傳回的集合開頭的指標`IUnknown`介面指標。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>傳回值

指標`IUnknown`介面指標。

### <a name="remarks"></a>備註

集合包含儲存在本機作為的介面指標`IUnknown`。 您將每個轉換`IUnknown`介面為實際的介面型別，並透過它然後呼叫。 您不需要先查詢介面。

使用之前`IUnknown`介面，您應該檢查，它不是 NULL。

##  <a name="ccomunkarray"></a>  CComUnkArray::CComUnkArray

建構函式。

```
CComUnkArray();
```

### <a name="remarks"></a>備註

設定集合來保有`nMaxSize``IUnknown`指標，並初始化為 NULL 指標。

##  <a name="end"></a>  CComUnkArray::end

讓指標回到越過最後一個`IUnknown`集合中的指標。

```
IUnknown**
    end();
```

### <a name="return-value"></a>傳回值

指標`IUnknown`介面指標。

### <a name="remarks"></a>備註

`CComUnkArray`方法`begin`和`end`可以用來引發事件時執行迴圈的所有連接點，例如。

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

##  <a name="getcookie"></a>  CComUnkArray::GetCookie

呼叫此方法，以取得相關聯的 cookie 指定`IUnknown`指標。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>參數

*ppFind*<br/>
`IUnknown`相關聯的 cookie 是必要的指標。

### <a name="return-value"></a>傳回值

傳回具有相關聯的 cookie`IUnknown`指標或 0，如果沒有相符的`IUnknown`找到指標。

### <a name="remarks"></a>備註

如果有一個以上的執行個體的相同`IUnknown`指標，此函數會傳回第一個 cookie。

##  <a name="getunknown"></a>  CComUnkArray::GetUnknown

呼叫這個方法來取得`IUnknown`與指定的 cookie 相關聯的指標。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
Cookie 的相關聯`IUnknown`指標是必要。

### <a name="return-value"></a>傳回值

傳回`IUnknown`指標或如果找不到任何相符的 cookie 是 NULL。

##  <a name="remove"></a>  CComUnkArray::Remove

呼叫這個方法來移除`IUnknown`從陣列的指標。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
Cookie 參考`IUnknown`移除從陣列的指標。

### <a name="return-value"></a>傳回值

傳回為 true，則如果指標不移除，否則為 FALSE。

## <a name="see-also"></a>另請參閱

[CComDynamicUnkArray 類別](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
