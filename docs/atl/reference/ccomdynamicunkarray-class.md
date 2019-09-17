---
title: CComDynamicUnkArray 類別
ms.date: 11/04/2016
f1_keywords:
- CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::CComDynamicUnkArray
- ATLCOM/ATL::CComDynamicUnkArray::Add
- ATLCOM/ATL::CComDynamicUnkArray::begin
- ATLCOM/ATL::CComDynamicUnkArray::clear
- ATLCOM/ATL::CComDynamicUnkArray::end
- ATLCOM/ATL::CComDynamicUnkArray::GetAt
- ATLCOM/ATL::CComDynamicUnkArray::GetCookie
- ATLCOM/ATL::CComDynamicUnkArray::GetSize
- ATLCOM/ATL::CComDynamicUnkArray::GetUnknown
- ATLCOM/ATL::CComDynamicUnkArray::Remove
helpviewer_keywords:
- connection points [C++], managing
- CComDynamicUnkArray class
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
ms.openlocfilehash: d55a6d6bfbcc6921fa0633753365f5799388dc27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497236"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkArray 類別

這個類別會儲存指標的`IUnknown`陣列。

## <a name="syntax"></a>語法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComDynamicUnkArray::CComDynamicUnkArray](#ccomdynamicunkarray)|建構函式。 將集合值初始化為 Null，並將集合大小初始化為零。|
|[CComDynamicUnkArray：： ~ CComDynamicUnkArray](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComDynamicUnkArray：： Add](#add)|呼叫這個方法，將`IUnknown`指標加入至陣列。|
|[CComDynamicUnkArray：： begin](#begin)|傳回集合中第一個`IUnknown`指標的指標。|
|[CComDynamicUnkArray：： clear](#clear)|清空陣列。|
|[CComDynamicUnkArray：： end](#end)|傳回集合中最後`IUnknown`一個指標之後的指標。|
|[CComDynamicUnkArray::GetAt](#getat)|抓取位於指定索引處的專案。|
|[CComDynamicUnkArray::GetCookie](#getcookie)|呼叫這個方法，以取得與指定`IUnknown`指標相關聯的 cookie。|
|[CComDynamicUnkArray::GetSize](#getsize)|傳回陣列的長度。|
|[CComDynamicUnkArray::GetUnknown](#getunknown)|呼叫這個方法，以取得`IUnknown`與指定 cookie 相關聯的指標。|
|[CComDynamicUnkArray::Remove](#remove)|呼叫這個方法，從陣列`IUnknown`中移除指標。|

## <a name="remarks"></a>備註

`CComDynamicUnkArray`保留動態配置的`IUnknown`指標陣列，每個都是連接點上的介面。 `CComDynamicUnkArray`可以當做[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類別的參數使用。

[Begin](#begin) 和 [end](#end)方法可以用來在所有連接點上執行迴圈（例如，引發事件時）。`CComDynamicUnkArray`

如需自動建立連接點 proxy 的詳細資訊，請參閱[新增連接點至物件](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**建立具有`CComDynamicUnkArray`連接點的控制項時，[**加入類別**] wizard 會使用類別。 如果您想要手動指定連接點的數目，請將的參考從`CComDynamicUnkArray`變更`CComUnkArray<`為*n* `>`，其中*n*是所需的連接點數目。

## <a name="requirements"></a>需求

**標頭：** atlcom.h。h

##  <a name="add"></a>CComDynamicUnkArray：： Add

呼叫這個方法，將`IUnknown`指標加入至陣列。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*pUnk*<br/>
要`IUnknown`加入至陣列的指標。

### <a name="return-value"></a>傳回值

傳回與新加入指標相關聯的 cookie。

##  <a name="begin"></a>CComDynamicUnkArray：： begin

將指標傳回到`IUnknown`介面指標集合的開頭。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>傳回值

`IUnknown`介面指標的指標。

### <a name="remarks"></a>備註

集合包含以形式儲存在`IUnknown`本機之介面的指標。 您會將`IUnknown`每個介面轉換成實際介面類別型，然後呼叫它。 您不需要先查詢介面。

使用`IUnknown`介面之前，您應該先檢查它是否不是 Null。

##  <a name="clear"></a>CComDynamicUnkArray：： clear

清空陣列。

```
void clear();
```

##  <a name="ccomdynamicunkarray"></a>CComDynamicUnkArray::CComDynamicUnkArray

建構函式。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>備註

將集合大小設定為零，並將值初始化為 Null。 如有需要，此函式會釋放集合。

##  <a name="dtor"></a>CComDynamicUnkArray：： ~ CComDynamicUnkArray

解構函式。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>備註

釋放類別的函式所配置的資源。

##  <a name="end"></a>CComDynamicUnkArray：： end

傳回集合中最後`IUnknown`一個指標之後的指標。

```
IUnknown**
    end();
```

### <a name="return-value"></a>傳回值

`IUnknown`介面指標的指標。

##  <a name="getat"></a>CComDynamicUnkArray：： GetAt

抓取位於指定索引處的專案。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取之項目的索引。

### <a name="return-value"></a>傳回值

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面的指標。

##  <a name="getcookie"></a>CComDynamicUnkArray：： System.windows.application.getcookie

呼叫這個方法，以取得與指定`IUnknown`指標相關聯的 cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>參數

*ppFind*<br/>
需要其相關聯 cookie 的指標。`IUnknown`

### <a name="return-value"></a>傳回值

傳回與`IUnknown`指標相關聯的 cookie，如果找不到相符`IUnknown`的指標，則為零。

### <a name="remarks"></a>備註

如果同`IUnknown`一個指標有多個實例，則此函式會傳回第一個的 cookie。

##  <a name="getsize"></a>CComDynamicUnkArray：： GetSize

傳回陣列的長度。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

陣列的長度。

##  <a name="getunknown"></a>CComDynamicUnkArray::GetUnknown

呼叫這個方法，以取得`IUnknown`與指定 cookie 相關聯的指標。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
需要相關聯`IUnknown`指標的 cookie。

### <a name="return-value"></a>傳回值

`IUnknown`傳回指標，如果找不到相符的 cookie，則為 Null。

##  <a name="remove"></a>CComDynamicUnkArray：： Remove

呼叫這個方法，從陣列`IUnknown`中移除指標。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
參考要從陣列`IUnknown`中移除之指標的 cookie。

### <a name="return-value"></a>傳回值

如果指標已移除，則傳回 TRUE;否則為 FALSE。

## <a name="see-also"></a>另請參閱

[CComUnkArray 類別](../../atl/reference/ccomunkarray-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
