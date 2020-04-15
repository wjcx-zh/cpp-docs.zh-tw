---
title: CRBMap 類別
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331395"
---
# <a name="crbmap-class"></a>CRBMap 類別

此類表示映射結構,使用紅黑二進制樹。

## <a name="syntax"></a>語法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>參數

*K*<br/>
鍵元素類型。

*五*<br/>
值元素類型。

*克瓦次克*<br/>
複製或移動關鍵元素的代碼。 有關詳細資訊[,請參閱 CElementTraits 類別](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
複製或移動值元素的代碼。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRBMap:CRBMap](#crbmap)|建構函式。|
|[CRBMap:*CRBMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRBMap::尋找](#lookup)|調用此方法以查找物件中的`CRBMap`鍵或值。|
|[CRBMap::刪除鍵](#removekey)|呼叫此方法以在給定鍵的情況下從`CRBMap`物件中刪除元素。|
|[CRBMap:setat](#setat)|呼叫此方法以將元素對插入到地圖中。|

## <a name="remarks"></a>備註

`CRBMap`支援任何給定類型的映射陣列,管理按順序排列的關鍵元素陣列及其關聯值。 每個鍵只能有一個關聯的值。 元素(由鍵和值組成)使用[CRBMap:setAt](#setat)方法存儲在二進制樹結構中。 可以使用[CRBMap::removeKey](#removekey)方法刪除元素,該方法使用給定的鍵值刪除元素。

使用[CRBTree::獲取頭位置](../../atl/reference/crbtree-class.md#getheadposition)[、CRBTree:getNext](../../atl/reference/crbtree-class.md#getnext)和[CRBTree:getNextValue](../../atl/reference/crbtree-class.md#getnextvalue)等方法可以遍歷樹。

*KTraits*和*VTraits*參數是包含複製或移動元素所需的任何補充代碼的特徵類。

`CRBMap`派生自[CRBTree](../../atl/reference/crbtree-class.md),它使用紅黑演算法實現二進制樹。 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)是一種變體,它允許每個鍵有多個值。 它也是從`CRBTree`派生的,因此`CRBMap`與共用許多功能。

和`CRBMap``CRBMultiMap`由[CAtlMap](../../atl/reference/catlmap-class.md)類提供的替代方法。 當只需要存儲少量元素時,請考慮改用[CSimpleMap](../../atl/reference/csimplemap-class.md)類。

有關各種集合類及其特性和性能特徵的更完整的討論,請參閱[ATL 集合類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap:CRBMap

建構函式。

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

*nBlockSize*參數是需要新元素時分配的內存量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。 默認值將一次為 10 個元素分配空間。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap:*CRBMap

解構函式。

```
~CRBMap() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::尋找

調用此方法以查找物件中的`CRBMap`鍵或值。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指定標識要備份的元素的鍵。

*值*<br/>
接收上值的變數。

### <a name="return-value"></a>傳回值

如果找到鍵,則方法的第一種形式返回 true,否則為 false。 第二個和第三個窗體返回指向[CPair](crbtree-class.md#cpair_class)的指標。

### <a name="remarks"></a>備註

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::刪除鍵

呼叫此方法以在給定鍵的情況下從`CRBMap`物件中刪除元素。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
與要刪除的元素對對應的鍵。

### <a name="return-value"></a>傳回值

如果找到並刪除該鍵,則返回 true,在失敗時為 false。

### <a name="remarks"></a>備註

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap:setat

呼叫此方法以將元素對插入到地圖中。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要添加到`CRBMap`物件的鍵值。

*值*<br/>
要新增到物件的值`CRBMap`。

### <a name="return-value"></a>傳回值

返回鍵/值元素對在物件中`CRBMap`的位置。

### <a name="remarks"></a>備註

`SetAt`如果找到匹配的鍵,則替換現有元素。 如果未找到該鍵,則創建新的鍵/值對。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CRBTree 類別](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 類別](../../atl/reference/catlmap-class.md)<br/>
[CRB多對應類別](../../atl/reference/crbmultimap-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
