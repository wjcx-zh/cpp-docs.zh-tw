---
title: CSimpleArray 類別
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
ms.openlocfilehash: 6395e324d5efdba208a7f77d86ca466fb7cdbb5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460459"
---
# <a name="csimplearray-class"></a>CSimpleArray 類別

這個類別提供方法來管理簡單的陣列。

## <a name="syntax"></a>語法

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>參數

*T*<br/>
若要儲存在陣列中的資料型別。

*TEqual*<br/>
特性物件，並定義等號比較測試類型的項目*T*。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|簡單陣列建構函式。|
|[CSimpleArray:: ~ CSimpleArray](#dtor)|簡單陣列解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleArray::Add](#add)|將新的項目加入至陣列。|
|[CSimpleArray::Find](#find)|陣列中尋找的項目。|
|[CSimpleArray::GetData](#getdata)|傳回陣列中儲存的資料指標。|
|[CSimpleArray::GetSize](#getsize)|傳回儲存在陣列中的項目數目。|
|[CSimpleArray::Remove](#remove)|從陣列中移除指定的項目。|
|[CSimpleArray::RemoveAll](#removeall)|從陣列移除所有項目。|
|[CSimpleArray::RemoveAt](#removeat)|從陣列中移除指定的項目。|
|[CSimpleArray::SetAtIndex](#setatindex)|設定指定的項目陣列中。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|從陣列中擷取項目。|
|[CSimpleArray::operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

`CSimpleArray` 提供方法來建立及管理簡單的陣列，任何指定類型的`T`。

參數`TEqual`提供方法來定義兩個項目類型的等號比較函式`T`。 藉由建立類別類似於[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)，就可以變更任何指定之陣列的等號比較測試的行為。 例如，當處理的指標陣列，可能適合用來定義為相等，取決於指標所參考的值。 預設實作會利用**operator=()**。

兩者`CSimpleArray`並[CSimpleMap](../../atl/reference/csimplemap-class.md)專為少量的項目。 [CAtlArray](../../atl/reference/catlarray-class.md)並[CAtlMap](../../atl/reference/catlmap-class.md)陣列包含大量項目時，應使用。

## <a name="requirements"></a>需求

**標頭：** atlsimpcoll.h

## <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

##  <a name="add"></a>  CSimpleArray::Add

將新的項目加入至陣列。

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>參數

*t*<br/>
要加入至陣列的項目。

### <a name="return-value"></a>傳回值

如果項目已成功新增至陣列，也就是 FALSE 否則為 true，則傳回。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray

陣列物件的建構函式。

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>參數

*src*<br/>
現有的 `CSimpleArray` 物件。

### <a name="remarks"></a>備註

初始化資料成員，建立新的空`CSimpleArray`物件或將現有的複本`CSimpleArray`物件。

##  <a name="dtor"></a>  CSimpleArray:: ~ CSimpleArray

解構函式。

```
~CSimpleArray();
```

### <a name="remarks"></a>備註

釋放所有配置的資源。

##  <a name="find"></a>  CSimpleArray::Find

陣列中尋找的項目。

```
int Find(const T& t) const;
```

### <a name="parameters"></a>參數

*t*<br/>
要搜尋項目。

### <a name="return-value"></a>傳回值

傳回找到的項目，則為-1 的索引; 如果找不到項目。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

##  <a name="getdata"></a>  CSimpleArray::GetData

傳回陣列中儲存的資料指標。

```
T* GetData() const;
```

### <a name="return-value"></a>傳回值

傳回陣列中的資料指標。

##  <a name="getsize"></a>  CSimpleArray::GetSize

傳回儲存在陣列中的項目數目。

```
int GetSize() const;
```

### <a name="return-value"></a>傳回值

傳回儲存在陣列中的項目數目。

##  <a name="operator_at"></a>  CSimpleArray::operator \[\]

從陣列中擷取項目。

```
T& operator[](int nindex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
項目索引。

### <a name="return-value"></a>傳回值

傳回所參考的陣列的項目*nIndex*。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

##  <a name="operator_eq"></a>  CSimpleArray::operator =

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

讓指標回到更新`CSimpleArray`物件。

### <a name="remarks"></a>備註

複製所有項目從`CSimpleArray`所參考的物件*src*成目前的陣列物件，取代所有現有的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

##  <a name="remove"></a>  CSimpleArray::Remove

從陣列中移除指定的項目。

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>參數

*t*<br/>
要從陣列中移除的項目。

### <a name="return-value"></a>傳回值

為 true，則會傳回項目是否找到並移除，否則為 FALSE 否則。

### <a name="remarks"></a>備註

移除項目時，陣列中其餘的項目會重新編號，以填滿空的空間。

##  <a name="removeall"></a>  CSimpleArray::RemoveAll

從陣列移除所有項目。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

移除目前儲存在陣列中的所有項目。

##  <a name="removeat"></a>  CSimpleArray::RemoveAt

從陣列中移除指定的項目。

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指向要移除之元素的索引。

### <a name="return-value"></a>傳回值

為 true，則會傳回項目是否已移除，則為 FALSE 的索引無效。

### <a name="remarks"></a>備註

移除項目時，陣列中其餘的項目會重新編號，以填滿空的空間。

##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex

設定指定的項目陣列中。

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
若要變更項目的索引。

*t*<br/>
要指派給指定項目的值。

### <a name="return-value"></a>傳回值

傳回為 true，則如果成功，則為 FALSE 如果索引無效。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
