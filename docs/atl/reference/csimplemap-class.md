---
title: CSimpleMap 類別
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
ms.openlocfilehash: 1c1aa34d54f5754feee238fdf12fd6e55b8c32c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666246"
---
# <a name="csimplemap-class"></a>CSimpleMap 類別

這個類別會提供簡單的對應陣列的支援。

## <a name="syntax"></a>語法

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>參數

*TKey*<br/>
索引鍵的項目類型。

*TVal*<br/>
值的項目型別。

*TEqual*<br/>
特性物件，並定義類型的項目等號比較測試`T`。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|實值類型的 Typedef。|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|索引鍵類型的 Typedef。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|建構函式。|
|[CSimpleMap:: ~ CSimpleMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleMap::Add](#add)|將金鑰和相關聯的值加入至對應陣列。|
|[CSimpleMap::FindKey](#findkey)|尋找特定的索引鍵。|
|[CSimpleMap::FindVal](#findval)|尋找特定的值。|
|[CSimpleMap::GetKeyAt](#getkeyat)|擷取指定之索引鍵。|
|[CSimpleMap::GetSize](#getsize)|傳回對應陣列中的項目數目。|
|[CSimpleMap::GetValueAt](#getvalueat)|擷取指定的值。|
|[CSimpleMap::Lookup](#lookup)|傳回與指定的索引鍵相關聯的值。|
|[CSimpleMap::Remove](#remove)|移除索引鍵和相符的值。|
|[CSimpleMap::RemoveAll](#removeall)|移除所有索引鍵和值。|
|[CSimpleMap::RemoveAt](#removeat)|移除特定索引鍵和相符的值。|
|[CSimpleMap::ReverseLookup](#reverselookup)|傳回與指定的值相關聯的金鑰。|
|[CSimpleMap::SetAt](#setat)|設定指定的索引鍵相關聯的值。|
|[CSimpleMap::SetAtIndex](#setatindex)|設定特定索引鍵和值。|

## <a name="remarks"></a>備註

`CSimpleMap` 支援任何指定類型的簡單對應陣列`T`，管理未排序的索引鍵的項目和其相關聯的值陣列。

參數`TEqual`提供方法來定義兩個項目類型的等號比較函式`T`。 藉由建立類別類似於[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)，就可以變更任何指定之陣列的等號比較測試的行為。 例如，當處理的指標陣列，可能適合用來定義為相等，取決於指標所參考的值。 預設實作會利用**operator**。

兩者`CSimpleMap`並[CSimpleArray](../../atl/reference/csimplearray-class.md)會提供與先前的 ATL 的相容性版本，並提供更完整且有效的集合實作[CAtlArray](../../atl/reference/catlarray-class.md)和[CAtlMap](../../atl/reference/catlmap-class.md)。

不同於在 ATL 和 MFC 其他對應集合，這個類別使用簡單的陣列，實作，並查閱搜尋要求的線性搜尋。 `CAtlMap` 陣列包含大量項目時，應該使用。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

##  <a name="add"></a>  CSimpleMap::Add

將金鑰和相關聯的值加入至對應陣列。

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>參數

*key*<br/>
索引鍵。

*val*<br/>
相關聯的值。

### <a name="return-value"></a>傳回值

為 true，則會傳回索引鍵和值是否已成功新增，則為 FALSE 否則。

### <a name="remarks"></a>備註

每個索引鍵和值組加入對應陣列記憶體釋出，並重新配置，以確保每個資料一律儲存連續的原因。 也就是第二個索引鍵的項目一律直接位在記憶體中的第一個索引鍵的元素，依此類推。

##  <a name="_arrayelementtype"></a>  CSimpleMap::_ArrayElementType

索引鍵類型的 typedef。

```
typedef TVal _ArrayElementType;
```

##  <a name="_arraykeytype"></a>  CSimpleMap::_ArrayKeyType

實值類型的 typedef。

```
typedef TKey _ArrayKeyType;
```

##  <a name="csimplemap"></a>  CSimpleMap::CSimpleMap

建構函式。

```
CSimpleMap();
```

### <a name="remarks"></a>備註

初始化資料成員。

##  <a name="dtor"></a>  CSimpleMap:: ~ CSimpleMap

解構函式。

```
~CSimpleMap();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="findkey"></a>  CSimpleMap::FindKey

尋找特定的索引鍵。

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
要搜尋的索引鍵。

### <a name="return-value"></a>傳回值

傳回的索引鍵，如果找到，否則會傳回-1。

##  <a name="findval"></a>  CSimpleMap::FindVal

尋找特定的值。

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>參數

*val*<br/>
要搜尋值。

### <a name="return-value"></a>傳回值

傳回值的索引並在找到，否則會傳回-1。

##  <a name="getkeyat"></a>  CSimpleMap::GetKeyAt

擷取指定之索引處的索引鍵。

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要傳回之索引鍵索引。

### <a name="return-value"></a>傳回值

傳回所參考的索引鍵*nIndex*。

### <a name="remarks"></a>備註

藉由傳遞的索引*nIndex*必須是有效的傳回值為有意義。

##  <a name="getsize"></a>  CSimpleMap::GetSize

傳回對應陣列中的項目數目。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

對應陣列中傳回的項目數 （索引鍵和值是一個項目）。

##  <a name="getvalueat"></a>  CSimpleMap::GetValueAt

擷取特定的索引處的值。

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要傳回之值的索引。

### <a name="return-value"></a>傳回值

傳回所參考的值*nIndex*。

### <a name="remarks"></a>備註

藉由傳遞的索引*nIndex*必須是有效的傳回值為有意義。

##  <a name="lookup"></a>  CSimpleMap::Lookup

傳回與指定的索引鍵相關聯的值。

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
索引鍵。

### <a name="return-value"></a>傳回值

傳回相關聯的值。 如果沒有相符的索引鍵找不到 NULL 會傳回。

##  <a name="remove"></a>  CSimpleMap::Remove

移除索引鍵和相符的值。

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>參數

*key*<br/>
索引鍵。

### <a name="return-value"></a>傳回值

傳回 TRUE，以及相符的值是否已成功移除，否則為 FALSE 否則。

##  <a name="removeall"></a>  CSimpleMap::RemoveAll

移除所有索引鍵和值。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

從對應的陣列物件中移除所有索引鍵和值。

##  <a name="removeat"></a>  CSimpleMap::RemoveAt

移除索引鍵和相關聯的值，指定索引處。

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
金鑰和相關聯的值，若要移除的索引。

### <a name="return-value"></a>傳回值

為 true，則傳回 FALSE 都成功，如果指定的索引是無效的索引。

##  <a name="reverselookup"></a>  CSimpleMap::ReverseLookup

傳回與指定的值相關聯的金鑰。

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>參數

*val*<br/>
數值。

### <a name="return-value"></a>傳回值

傳回相關聯的索引鍵。 如果沒有相符的索引鍵找不到 NULL 會傳回。

##  <a name="setat"></a>  CSimpleMap::SetAt

設定指定的索引鍵相關聯的值。

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>參數

*key*<br/>
索引鍵。

*val*<br/>
要指派新的值。

### <a name="return-value"></a>傳回值

如果找不到索引鍵和值可為已成功變更，否則為 FALSE 否則會傳回 TRUE。

##  <a name="setatindex"></a>  CSimpleMap::SetAtIndex

設定指定索引處的索引鍵和值。

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參考的索引鍵和值配對，以變更索引。

*key*<br/>
新的金鑰。

*val*<br/>
新值。

### <a name="return-value"></a>傳回值

傳回為 true，則如果成功，則為 FALSE 如果索引無效。

### <a name="remarks"></a>備註

更新索引鍵和值所指向*nIndex*。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
