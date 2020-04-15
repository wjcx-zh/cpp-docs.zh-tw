---
title: CComDynamicUnkarray 類別
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
ms.openlocfilehash: 57383823897a434f649c6c4af78e71fe6ff66a6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327901"
---
# <a name="ccomdynamicunkarray-class"></a>CComDynamicUnkarray 類別

此類儲存指標陣列`IUnknown`。

## <a name="syntax"></a>語法

```
class CComDynamicUnkArray
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComDynamicUnkarray::CComDynamicUnkarray](#ccomdynamicunkarray)|建構函式。 將集合值初始化為 NULL,將集合大小初始化為零。|
|[CComDynamicUnkarray:~CComDynamicUnkarray](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComDynamicUnkarray::添加](#add)|調用此方法以向陣組添加`IUnknown`指標。|
|[CComDynamicUnkarray:開始](#begin)|返回指向集合中第一`IUnknown`個指標的指標。|
|[CComDynamicUnkarray::清除](#clear)|清空陣組。|
|[CComDynamicUnkarray::結束](#end)|返回指向集合中最後`IUnknown`一個指標的指標。|
|[CComDynamicUnkarray::GetAt](#getat)|擷取指定索引處的項目。|
|[CComDynamicUnkarray::獲取餅乾](#getcookie)|調用此方法獲取與給定`IUnknown`指標關聯的 Cookie。|
|[CComDynamicUnkarray::取得Size](#getsize)|返回陣列的長度。|
|[CComDynamicUnkarray:抓取未知](#getunknown)|調用此方法獲取與給定`IUnknown`Cookie 關聯的指標。|
|[CComDynamicUnkarray::刪除](#remove)|呼叫此方法從陣列中刪除`IUnknown`指標。|

## <a name="remarks"></a>備註

`CComDynamicUnkArray`保存動態分配的`IUnknown`指標陣列,每個指標位於連接點上的介面。 `CComDynamicUnkArray`可用作[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)範本類的參數。

方法`CComDynamicUnkArray`[開始和結束](#begin)[可用於迴圈](#end)遍歷所有連接點(例如,觸發事件時)。

有關自動建立連接點代理的詳細資訊[,請參閱向物件新增連接點](../../atl/adding-connection-points-to-an-object.md)。

> [!NOTE]
> **注意**建立具有`CComDynamicUnkArray`連接點的控制項時,「**添加類」** 精靈使用該類。 如果要手動指定連接點的數量,請將引用從`CComDynamicUnkArray`更改`CComUnkArray<`為*n* `>`,其中*n*是所需的連接點數。

## <a name="requirements"></a>需求

**標題:** atlcom.h

## <a name="ccomdynamicunkarrayadd"></a><a name="add"></a>CComDynamicUnkarray::添加

調用此方法以向陣組添加`IUnknown`指標。

```
DWORD Add(IUnknown* pUnk);
```

### <a name="parameters"></a>參數

*龐克*<br/>
要`IUnknown`添加到陣列的指標。

### <a name="return-value"></a>傳回值

返回與新添加的指標關聯的 Cookie。

## <a name="ccomdynamicunkarraybegin"></a><a name="begin"></a>CComDynamicUnkarray:開始

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

## <a name="ccomdynamicunkarrayclear"></a><a name="clear"></a>CComDynamicUnkarray::清除

清空陣組。

```
void clear();
```

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="ccomdynamicunkarray"></a>CComDynamicUnkarray::CComDynamicUnkarray

建構函式。

```
CComDynamicUnkArray();
```

### <a name="remarks"></a>備註

將集合大小設定為零,並將值初始化為 NULL。 如有必要,析構函數釋放集合。

## <a name="ccomdynamicunkarrayccomdynamicunkarray"></a><a name="dtor"></a>CComDynamicUnkarray:~CComDynamicUnkarray

解構函式。

```
~CComDynamicUnkArray();
```

### <a name="remarks"></a>備註

釋放類構造函數分配的資源。

## <a name="ccomdynamicunkarrayend"></a><a name="end"></a>CComDynamicUnkarray::結束

返回指向集合中最後`IUnknown`一個指標的指標。

```
IUnknown**
    end();
```

### <a name="return-value"></a>傳回值

指向介面指標的`IUnknown`指標。

## <a name="ccomdynamicunkarraygetat"></a><a name="getat"></a>CComDynamicUnkarray::GetAt

擷取指定索引處的項目。

```
IUnknown* GetAt(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要擷取之項目的索引。

### <a name="return-value"></a>傳回值

指向 I[未知](/windows/win32/api/unknwn/nn-unknwn-iunknown)介面的指標。

## <a name="ccomdynamicunkarraygetcookie"></a><a name="getcookie"></a>CComDynamicUnkarray::獲取餅乾

調用此方法獲取與給定`IUnknown`指標關聯的 Cookie。

```
DWORD WINAPI GetCookie(IUnknown** ppFind);
```

### <a name="parameters"></a>參數

*ppFind*<br/>
需要`IUnknown`關聯的 Cookie 的指標。

### <a name="return-value"></a>傳回值

返回與`IUnknown`指標關聯的 Cookie,如果未找到匹配`IUnknown`的指標,則返回零。

### <a name="remarks"></a>備註

如果同`IUnknown`一指標有多個實例,則此函數將返回第一個指標的 Cookie。

## <a name="ccomdynamicunkarraygetsize"></a><a name="getsize"></a>CComDynamicUnkarray::取得Size

返回陣列的長度。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

陣列的長度。

## <a name="ccomdynamicunkarraygetunknown"></a><a name="getunknown"></a>CComDynamicUnkarray:抓取未知

調用此方法獲取與給定`IUnknown`Cookie 關聯的指標。

```
IUnknown* WINAPI GetUnknown(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
需要關聯`IUnknown`指標的 Cookie。

### <a name="return-value"></a>傳回值

如果未找到`IUnknown`匹配的 Cookie,則傳回指標或 NULL。

## <a name="ccomdynamicunkarrayremove"></a><a name="remove"></a>CComDynamicUnkarray::刪除

呼叫此方法從陣列中刪除`IUnknown`指標。

```
BOOL Remove(DWORD dwCookie);
```

### <a name="parameters"></a>參數

*dwCookie*<br/>
引用要從陣列中刪除`IUnknown`的指標的 Cookie。

### <a name="return-value"></a>傳回值

如果刪除指標,則返回 TRUE;如果刪除指標,則返回 TRUE。否則 FALSE。

## <a name="see-also"></a>另請參閱

[CComUnkarray 類別](../../atl/reference/ccomunkarray-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
