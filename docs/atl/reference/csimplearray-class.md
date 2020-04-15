---
title: CSimplearray 類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: e45c9b3fd778aacd3a3e2d5d3696661afa0c6fb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330901"
---
# <a name="csimplearray-class"></a>CSimplearray 類別

此類提供了用於管理簡單陣列的方法。

## <a name="syntax"></a>語法

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在陣列中的數據類型。

*TEqual*<br/>
特徵物件,定義*T*類型元素的相等性測試。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[簡單陣列::C簡單陣列](#csimplearray)|簡單陣列的構造函數。|
|[簡單陣列::*C簡單陣列](#dtor)|簡單陣列的析構函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[簡單陣列::添加](#add)|向陣列添加新元素。|
|[簡單陣列:尋找](#find)|在陣列中尋找元素。|
|[CSimplearray:取得資料](#getdata)|返回指向陣列中儲存數據的指標。|
|[簡單陣列:取得 Size](#getsize)|返回存儲在陣列中的元素數。|
|[簡單陣列::刪除](#remove)|從陣列中移除給定元素。|
|[簡單陣列::刪除所有](#removeall)|從陣列中移除所有元素。|
|[簡單陣列::刪除At](#removeat)|從陣列中移除指定的元素。|
|[簡單陣列::設定Atindex](#setatindex)|設定陣列中的指定元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|從陣列中擷取項目。|
|[CSimpleArray::運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`CSimpleArray`提供了用於創建和管理任何給定類型的`T`簡單陣列的方法。

該參數`TEqual`提供了一種為類型`T`中的 兩個元素定義相等函數的方法。 通過創建類似於[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)的類,可以更改任何給定陣列的相等測試的行為。 例如,在處理指標陣列時,將相等性定義為根據指標引用的值可能很有用。 預設使用運算子 **_()**。

和`CSimpleArray` [CSimpleMap](../../atl/reference/csimplemap-class.md)都專為少量元素而設計。 當陣列包含大量元素時,應使用[CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap。](../../atl/reference/catlmap-class.md)

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>簡單陣列::添加

向陣列添加新元素。

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>參數

*t*<br/>
要添加到陣列的元素。

### <a name="return-value"></a>傳回值

如果元素已成功添加到陣列中,則返回 TRUE,否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>簡單陣列::C簡單陣列

陣組物件的構造函數。

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>參數

*src*<br/>
現有的 `CSimpleArray` 物件。

### <a name="remarks"></a>備註

初始化資料成員,創建新的空`CSimpleArray`物件或`CSimpleArray`現有 物件的副本。

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>簡單陣列::*C簡單陣列

解構函式。

```
~CSimpleArray();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="csimplearrayfind"></a><a name="find"></a>簡單陣列:尋找

在陣列中尋找元素。

```
int Find(const T& t) const;
```

### <a name="parameters"></a>參數

*t*<br/>
要為其搜索的元素。

### <a name="return-value"></a>傳回值

返回找到的元素的索引,如果找不到該元素,則返回 -1。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimplearray:取得資料

返回指向陣列中儲存數據的指標。

```
T* GetData() const;
```

### <a name="return-value"></a>傳回值

返回指向陣列中數據的指標。

## <a name="csimplearraygetsize"></a><a name="getsize"></a>簡單陣列:取得 Size

返回存儲在陣列中的元素數。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

返回存儲在陣列中的元素數。

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::運算子\[\]

從陣列中擷取項目。

```
T& operator[](int nindex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
元素索引。

### <a name="return-value"></a>傳回值

返回*nIndex*引用的陣列的元素。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::運算符 |

指派運算子。

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製的陣列。

### <a name="return-value"></a>傳回值

返回指向更新`CSimpleArray`物件的指標。

### <a name="remarks"></a>備註

將*src*`CSimpleArray`引用的物件中的所有元素複製到當前陣列物件中,替換所有現有資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>簡單陣列::刪除

從陣列中移除給定元素。

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>參數

*t*<br/>
要從陣列中移除的元素。

### <a name="return-value"></a>傳回值

如果找到並刪除了該元素,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

刪除元素時,將重新編號陣列中的剩餘元素以填充空白空間。

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>簡單陣列::刪除所有

從陣列中移除所有元素。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

刪除目前儲存在陣列中的所有元素。

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>簡單陣列::刪除At

從陣列中移除指定的元素。

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指向要刪除的元素的索引。

### <a name="return-value"></a>傳回值

如果刪除元素,則返回 TRUE;如果索引無效,則返回 FALSE。

### <a name="remarks"></a>備註

刪除元素時,將重新編號陣列中的剩餘元素以填充空白空間。

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>簡單陣列::設定Atindex

在陣列中設定指定元素。

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要更改的元素的索引。

*t*<br/>
要指派給指定項目的值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;如果索引無效,則返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
