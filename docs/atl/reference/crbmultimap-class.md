---
title: CRB多對應類別
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331426"
---
# <a name="crbmultimap-class"></a>CRB多對應類別

此類表示一個映射結構,允許每個鍵可以使用紅黑二進位樹與多個值關聯。

## <a name="syntax"></a>語法

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRB多對應:CRB多映射](#crbmultimap)|建構函式。|
|[CRB多對應::*CRB多映射](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRB多對應::尋找第一鍵](#findfirstwithkey)|調用此方法以查找具有給定鍵的第一個元素的位置。|
|[CRB多對應:抓取下一個值與金鑰](#getnextvaluewithkey)|調用此方法獲取與給定鍵關聯的值,並更新位置值。|
|[CRB多對應::取得下一個與金鑰](#getnextwithkey)|調用此方法獲取與給定鍵關聯的元素,並更新位置值。|
|[CRB多對應:插入](#insert)|呼叫此方法以將元素對插入到地圖中。|
|[CRB多對應::刪除鍵](#removekey)|呼叫此方法以刪除給定鍵的所有鍵/值元素。|

## <a name="remarks"></a>備註

`CRBMultiMap`支援任何給定類型的映射陣列,管理鍵元素和值的有序陣列。 與[CRBMap](../../atl/reference/crbmap-class.md)類不同,每個鍵可以與多個值相關聯。

元素(由鍵和值組成)使用[CRBMultiMap::插入](#insert)方法存儲在二進位區塊結構中。 可以使用[CRBMultiMap::刪除Key](#removekey)方法刪除元素,該方法刪除與給定鍵匹配的所有元素。

使用[CRBTree::獲取頭位置](../../atl/reference/crbtree-class.md#getheadposition)[、CRBTree:getNext](../../atl/reference/crbtree-class.md#getnext)和[CRBTree:getNextValue](../../atl/reference/crbtree-class.md#getnextvalue)等方法可以遍歷樹。 可以使用[CRBMultiMap::尋找第一個金鑰](#findfirstwithkey)[、CRB 多映射:取得NextValue與金鑰](#getnextvaluewithkey)和[CRB 多映射:獲取NextNext與鍵](#getnextwithkey)方法,可以存取每個鍵的潛在多個值。 有關[CRBMultiMap 的範例:CRBMultiMap,](#crbmultimap)請參閱實際說明。

*KTraits*和*VTraits*參數是包含複製或移動元素所需的任何補充代碼的特徵類。

`CRBMultiMap`派生自[CRBTree](../../atl/reference/crbtree-class.md),它使用紅黑演算法實現二進制樹。 `CRBMultiMap` [CAtlMap](../../atl/reference/catlmap-class.md)類別提供的替代`CRBMap`方法 。 當只需要存儲少量元素時,請考慮改用[CSimpleMap](../../atl/reference/csimplemap-class.md)類。

有關各種集合類及其特性和性能特徵的更完整的討論,請參閱[ATL 集合類](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRB多對應:CRB多映射

建構函式。

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

*nBlockSize*參數是需要新元素時分配的內存量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。 默認值將一次為 10 個元素分配空間。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRB多對應::*CRB多映射

解構函式。

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRB多對應::尋找第一鍵

調用此方法以查找具有給定鍵的第一個元素的位置。

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指定識別要找到的元素的鍵。

### <a name="return-value"></a>傳回值

如果找到鍵,則返回第一個鍵/值元素的位置,否則返回 NULL。

### <a name="remarks"></a>備註

中的鍵`CRBMultiMap`可以具有一個或多個關聯的值。 此方法將提供與該特定鍵關聯的第一個值(實際上可能是唯一的值)的位置值。 然後,返回的位置值可與[CRBMultiMap 一起使用::獲取 NextValue 與密鑰](#getnextvaluewithkey)或[CRBMultiMap::獲取 NextNext WithKey](#getnextwithkey)以獲取值並更新位置。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

請參考[CRB 多映射的範例::CRB 多映射](#crbmultimap)。

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRB多對應:抓取下一個值與金鑰

調用此方法獲取與給定鍵關聯的值並更新位置值。

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值,透過呼叫[CRBMultiMap 取得:尋找第一與金鑰](#findfirstwithkey)或[CRB 多映射::取得NextNext WithKey,](#getnextwithkey)或以前呼叫`GetNextValueWithKey`。

*關鍵*<br/>
指定識別要找到的元素的鍵。

### <a name="return-value"></a>傳回值

返回與給定鍵關聯的元素對。

### <a name="remarks"></a>備註

位置值將更新以指向與鍵關聯的下一個值。 如果不存在更多值,則位置值設定為 NULL。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

請參考[CRB 多映射的範例::CRB 多映射](#crbmultimap)。

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRB多對應::取得下一個與金鑰

呼叫此方法取得與給定鍵關聯的元素並更新位置值。

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值,透過呼叫[CRBMultiMap 取得:尋找第一與金鑰](#findfirstwithkey)或[CRB 多映射::取得NextValue與金鑰](#getnextvaluewithkey)`GetNextWithKey`,或以前呼叫 。

*關鍵*<br/>
指定識別要找到的元素的鍵。

### <a name="return-value"></a>傳回值

返回下一個[CRBTree::CPair 類](crbtree-class.md#cpair_class)元素與給定鍵關聯。

### <a name="remarks"></a>備註

位置值將更新以指向與鍵關聯的下一個值。 如果不存在更多值,則位置值設定為 NULL。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRB多對應:插入

呼叫此方法以將元素對插入到地圖中。

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
要添加到`CRBMultiMap`物件的鍵值。

*值*<br/>
要添加到物件的值`CRBMultiMap`,與*鍵*相關聯。

### <a name="return-value"></a>傳回值

返回鍵/值元素對在物件中`CRBMultiMap`的位置。

### <a name="remarks"></a>備註

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

請參考[CRB 多映射的範例::CRB 多映射](#crbmultimap)。

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRB多對應::刪除鍵

呼叫此方法以刪除給定鍵的所有鍵/值元素。

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指定識別要刪除的元素的鍵。

### <a name="return-value"></a>傳回值

返回與給定鍵關聯的值數。

### <a name="remarks"></a>備註

`RemoveKey`刪除具有匹配*鍵*的鍵/值元素的所有鍵/值元素。

有關其他可用方法的資訊,請參閱基類[CRBTree](../../atl/reference/crbtree-class.md)的文檔。

### <a name="example"></a>範例

請參考[CRB 多映射的範例::CRB 多映射](#crbmultimap)。

## <a name="see-also"></a>另請參閱

[CRBTree 類別](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap 類別](../../atl/reference/catlmap-class.md)<br/>
[CRBMap 類別](../../atl/reference/crbmap-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
