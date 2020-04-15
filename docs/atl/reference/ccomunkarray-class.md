---
title: CComUnkarray 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- connection points [C++], managing
- CComUnkArray class
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
ms.openlocfilehash: c1d2f0296394d3979ef4f152e3f902c89adf5b45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327310"
---
# <a name="ccomunkarray-class"></a>CComUnkarray 類別

此類存儲`IUnknown`指標,並設計為用作[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類的參數。

## <a name="syntax"></a>語法

```
template<unsigned int nMaxSize>
class CComUnkArray
```

#### <a name="parameters"></a>參數

*nMaxSize*<br/>
可在靜態陣列中`IUnknown`持有的指標的最大數量。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComUnkarray:CComUnkarray](#ccomunkarray)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComUnkarray:新增](#add)|調用此方法以向陣組添加`IUnknown`指標。|
|[CComUnkarray:開始](#begin)|返回指向集合中第一`IUnknown`個指標的指標。|
|[CComUnkarray:結束](#end)|返回指向集合中最後`IUnknown`一個指標的指標。|
|[CComUnkarray:取得餅乾](#getcookie)|調用此方法獲取與給定`IUnknown`指標關聯的 Cookie。|
|[CComUnkarray:取得未知](#getunknown)|調用此方法獲取與給定`IUnknown`Cookie 關聯的指標。|
|[CComUnkarray::刪除](#remove)|呼叫此方法從陣列中刪除`IUnknown`指標。|

## <a name="remarks"></a>備註

`CComUnkArray`包含固定數量的`IUnknown`指標,每個指標位於連接點上。 `CComUnkArray`可用作[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類的參數。 `CComUnkArray<1>`是已針對一個`CComUnkArray`連接點優化的範本專門化。

方法`CComUnkArray`[開始和結束](#begin)[可用於迴圈](#end)遍歷所有連接點(例如,觸發事件時)。

有關自動建立連接點代理的詳細資訊[,請參閱向物件新增連接點](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**添加**類**嚮導在創建具有連接點的控制項時使用類[CComDynamicUnkarray。](../../atl/reference/ccomdynamicunkarray-class.md) 如果要手動指定連接點的數量,請將引用從`CComDynamicUnkArray`更改`CComUnkArray<`為*n* `>`,其中*n*是所需的連接點數。

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomunkarrayadd"></a><a name="add"></a>CComUnkarray:新增

調用此方法以向陣組添加`IUnknown`指標。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*龐克*<br/>
調用此方法以向陣組添加`IUnknown`指標。

### <a name="return-value"></a>傳回值

返回與新添加的指標關聯的 Cookie,如果數位不夠大以包含新指標,則返回 0。

## <a name="ccomunkarraybegin"></a><a name="begin"></a>CComUnkarray:開始

返回指向介面指標集合開頭的`IUnknown`指標。

```
IUnknown**
    begin();
```

### <a name="return-value"></a>傳回值

指向介面指標的`IUnknown`指標。

### <a name="remarks"></a>備註

集合包含指向本地存儲為`IUnknown`的介面的指標。 將每個`IUnknown`介面強制轉換為真正的介面類型,然後通過該介面類型調用它。 您不需要首先查詢介面。

在使用介面`IUnknown`之前,應檢查該介面是否為 NULL。

## <a name="ccomunkarrayccomunkarray"></a><a name="ccomunkarray"></a>CComUnkarray:CComUnkarray

建構函式。

```
CComUnkArray();
```

### <a name="remarks"></a>備註

將集合集集用於`nMaxSize``IUnknown`保存指標,並初始化指向 NULL 的指標。

## <a name="ccomunkarrayend"></a><a name="end"></a>CComUnkarray:結束

返回指向集合中最後`IUnknown`一個指標的指標。

```
IUnknown**
    end();
```

### <a name="return-value"></a>傳回值

指向介面指標的`IUnknown`指標。

### <a name="remarks"></a>備註

`CComUnkArray`方法`begin``end`, 可用於迴圈遍曆所有連接點,例如,觸發事件時。

[!code-cpp[NVC_ATL_COM#44](../../atl/codesnippet/cpp/ccomunkarray-class_1.cpp)]

## <a name="ccomunkarraygetcookie"></a><a name="getcookie"></a>CComUnkarray:取得餅乾

調用此方法獲取與給定`IUnknown`指標關聯的 Cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>參數

*ppFind*<br/>
需要`IUnknown`關聯的 Cookie 的指標。

### <a name="return-value"></a>傳回值

返回與`IUnknown`指標關聯的 Cookie,如果未找到匹配`IUnknown`的指標,則返回 0。

### <a name="remarks"></a>備註

如果同`IUnknown`一指標有多個實例,則此函數將返回第一個指標的 Cookie。

## <a name="ccomunkarraygetunknown"></a><a name="getunknown"></a>CComUnkarray:取得未知

調用此方法獲取與給定`IUnknown`Cookie 關聯的指標。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
需要關聯`IUnknown`指標的 Cookie。

### <a name="return-value"></a>傳回值

如果未找到`IUnknown`匹配的 Cookie,則傳回指標或 NULL。

## <a name="ccomunkarrayremove"></a><a name="remove"></a>CComUnkarray::刪除

呼叫此方法從陣列中刪除`IUnknown`指標。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
引用要從陣列中刪除`IUnknown`的指標的 Cookie。

### <a name="return-value"></a>傳回值

如果刪除指標,則返回 TRUE,否則返回 FALSE。

## <a name="see-also"></a>另請參閱

[CComDynamicUnkarray 類別](../../atl/reference/ccomdynamicunkarray-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
