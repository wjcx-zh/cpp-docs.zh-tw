---
title: C簡單對應類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: b8650f36ac3d190207870616754dcd596cb7cc45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330797"
---
# <a name="csimplemap-class"></a>C簡單對應類別

此類支援簡單的映射陣組。

## <a name="syntax"></a>語法

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>參數

*TKey*<br/>
鍵元素類型。

*TVal*<br/>
值元素類型。

*TEqual*<br/>
特徵物件,定義類型`T`元素的相等性測試。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSimpleMap:_ArrayElementType](#_arrayelementtype)|值類型的類型。|
|[C簡單映射:_ArrayKeyType](#_arraykeytype)|鍵類型的類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[簡單對應::C簡單映射](#csimplemap)|建構函式。|
|[簡單映射::_C 簡單映射](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[簡單映射::新增](#add)|向地圖陣組添加鍵和相關值。|
|[簡單映射::尋找金鑰](#findkey)|查找特定鍵。|
|[簡單映射::尋找Val](#findval)|查找特定值。|
|[簡單對應::取得鍵](#getkeyat)|檢索指定的金鑰。|
|[C簡單對應::取得大小](#getsize)|返回映射陣列中的條目數。|
|[簡單映射::獲取價值](#getvalueat)|檢索指定的值。|
|[C簡單映射::尋找](#lookup)|返回與給定鍵關聯的值。|
|[簡單映射::刪除](#remove)|刪除鍵和匹配值。|
|[簡單映射::刪除所有](#removeall)|刪除所有鍵和值。|
|[簡單對應::刪除 AT](#removeat)|刪除特定的鍵和匹配值。|
|[C簡單映射::反向查找](#reverselookup)|返回與給定值關聯的鍵。|
|[簡單映射::Setat](#setat)|設置與給定鍵關聯的值。|
|[簡單映射::設定Atindex](#setatindex)|設置特定的鍵和值。|

## <a name="remarks"></a>備註

`CSimpleMap`支援任何給定類型的`T`簡單映射陣列,管理鍵元素及其關聯值的無序陣列。

該參數`TEqual`提供了一種為類型`T`中的 兩個元素定義相等函數的方法。 通過創建類似於[CSimpleMapEqualHelper 的](../../atl/reference/csimplemapequalhelper-class.md)類,可以更改任何給定陣列的相等測試的行為。 例如,在處理指標陣列時,將相等性定義為根據指標引用的值可能很有用。 預設使用運算子 **_()**。

`CSimpleMap`提供和[CSimpleArray](../../atl/reference/csimplearray-class.md)與以前的 ATL 版本相容[,CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)提供了更完整、更高效的收集實現。

與 ATL 和 MFC 中的其他地圖集合不同,此類使用簡單的陣列實現,尋找搜索需要線性搜索。 `CAtlMap`當陣列包含大量元素時,應使用。

## <a name="requirements"></a>需求

**標題:** atlsimpcoll.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>簡單映射::新增

向地圖陣組添加鍵和相關值。

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
索引鍵。

*瓦爾*<br/>
關聯的值。

### <a name="return-value"></a>傳回值

如果成功添加鍵和值,則返回 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

每個鍵和值對都添加會導致映射陣列記憶體被釋放和重新分配,以確保每個鍵的數據始終連續存儲。 也就是說,第二個關鍵元素始終直接遵循記憶體中的第一個關鍵元素等。

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap:_ArrayElementType

鍵類型的類型。

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>C簡單映射:_ArrayKeyType

值類型的類型。

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>簡單對應::C簡單映射

建構函式。

```
CSimpleMap();
```

### <a name="remarks"></a>備註

初始化數據成員。

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>簡單映射::_C 簡單映射

解構函式。

```
~CSimpleMap();
```

### <a name="remarks"></a>備註

釋放所有分配的資源。

## <a name="csimplemapfindkey"></a><a name="findkey"></a>簡單映射::尋找金鑰

查找特定鍵。

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要搜尋的索引鍵。

### <a name="return-value"></a>傳回值

如果找到密鑰的索引,則返回 -1。

## <a name="csimplemapfindval"></a><a name="findval"></a>簡單映射::尋找Val

查找特定值。

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
要搜尋的值。

### <a name="return-value"></a>傳回值

如果找到值,則返回該值的索引,否則返回 -1。

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>簡單對應::取得鍵

在指定的索引處檢索密鑰。

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要傳回的索引鍵索引。

### <a name="return-value"></a>傳回值

傳回*nIndex*的字型 。

### <a name="remarks"></a>備註

*nIndex*傳遞的索引必須有效,才能使返回值有意義。

## <a name="csimplemapgetsize"></a><a name="getsize"></a>C簡單對應::取得大小

返回映射陣列中的條目數。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

返回映射陣列中的條目數(鍵和值是一個條目)。

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>簡單映射::獲取價值

檢索特定索引處的值。

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要返回的值的索引。

### <a name="return-value"></a>傳回值

返回*nIndex*引用的值。

### <a name="remarks"></a>備註

*nIndex*傳遞的索引必須有效,才能使返回值有意義。

## <a name="csimplemaplookup"></a><a name="lookup"></a>C簡單映射::尋找

返回與給定鍵關聯的值。

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>參數

*關鍵*<br/>
索引鍵。

### <a name="return-value"></a>傳回值

返回關聯的值。 如果未找到匹配的金鑰,則傳回 NULL。

## <a name="csimplemapremove"></a><a name="remove"></a>簡單映射::刪除

刪除鍵和匹配值。

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
索引鍵。

### <a name="return-value"></a>傳回值

如果成功刪除鍵和匹配值,則返回 TRUE,否則為 FALSE。

## <a name="csimplemapremoveall"></a><a name="removeall"></a>簡單映射::刪除所有

刪除所有鍵和值。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

從映射陣列對象中刪除所有鍵和值。

## <a name="csimplemapremoveat"></a><a name="removeat"></a>簡單對應::刪除 AT

刪除指定索引處的鍵和關聯的值。

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要刪除的鍵和相關值的索引。

### <a name="return-value"></a>傳回值

如果指定的索引無效,則在成功時返回 TRUE,則 FALSE。

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>C簡單映射::反向查找

返回與給定值關聯的鍵。

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>參數

*瓦爾*<br/>
值。

### <a name="return-value"></a>傳回值

返回關聯的密鑰。 如果未找到匹配的金鑰,則傳回 NULL。

## <a name="csimplemapsetat"></a><a name="setat"></a>簡單映射::Setat

設置與給定鍵關聯的值。

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
索引鍵。

*瓦爾*<br/>
要分配的新值。

### <a name="return-value"></a>傳回值

如果找到密鑰,並且該值已成功更改,則返回 TRUE,否則為 FALSE。

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>簡單映射::設定Atindex

在指定的索引處設置鍵和值。

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
索引,引用要更改的鍵和值配對。

*關鍵*<br/>
新索引鍵。

*瓦爾*<br/>
新的值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;如果索引無效,則返回 FALSE。

### <a name="remarks"></a>備註

更新*nIndex*指向的鍵和值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
