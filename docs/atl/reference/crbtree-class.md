---
title: CRBTree 類別
ms.date: 11/04/2016
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
ms.openlocfilehash: 7b8e47b5cd0ac278711947abc867956333371be3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833487"
---
# <a name="crbtree-class"></a>CRBTree 類別

此類別提供建立和利用紅黑型樹狀結構的方法。

## <a name="syntax"></a>語法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBTree
```

#### <a name="parameters"></a>參數

*K*<br/>
Key 元素類型。

*V*<br/>
值元素類型。

*KTraits*<br/>
用來複製或移動主要元素的程式碼。 如需詳細資訊，請參閱 [CElementTraits 類別](../../atl/reference/celementtraits-class.md) 。

*VTraits*<br/>
用來複製或移動值元素的程式碼。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CRBTree：： KINARGTYPE](#kinargtype)|當索引鍵做為輸入引數傳遞時，所使用的型別。|
|[CRBTree：： KOUTARGTYPE](#koutargtype)|當索引鍵作為輸出引數傳回時，所使用的型別。|
|[CRBTree：： VINARGTYPE](#vinargtype)|當值當做輸入引數傳遞時，所使用的型別。|
|[CRBTree：： VOUTARGTYPE](#voutargtype)|當值當做輸出引數傳遞時，所使用的型別。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[CRBTree：： CPair 類別](#cpair_class)|包含索引鍵和值元素的類別。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRBTree：： ~ CRBTree](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)|呼叫這個方法來尋找使用下一個可用索引鍵的元素位置。|
|[CRBTree：： GetAt](#getat)|呼叫這個方法，以取得樹狀結構中指定位置的專案。|
|[CRBTree：： GetCount](#getcount)|呼叫這個方法以取得樹狀結構中的專案數目。|
|[CRBTree：： GetHeadPosition](#getheadposition)|呼叫這個方法，以取得樹狀結構開頭之專案的位置值。|
|[CRBTree：： GetKeyAt](#getkeyat)|呼叫這個方法，從樹狀結構中的指定位置取得索引鍵。|
|[CRBTree：： GetNext](#getnext)|呼叫這個方法，取得儲存在物件中之專案的指標 `CRBTree` ，並將位置前移至下一個專案。|
|[CRBTree：： GetNextAssoc](#getnextassoc)|呼叫這個方法來取得儲存在地圖中的元素索引鍵和值，並將位置前移至下一個專案。|
|[CRBTree：： GetNextKey](#getnextkey)|呼叫這個方法來取得儲存在樹狀結構中之專案的索引鍵，並將位置前移至下一個專案。|
|[CRBTree：： GetNextValue](#getnextvalue)|呼叫這個方法以取得儲存在樹狀結構中的元素值，並將位置前移至下一個專案。|
|[CRBTree：： GetPrev](#getprev)|呼叫這個方法，取得儲存在物件中之專案的指標 `CRBTree` ，然後將位置更新為前一個元素。|
|[CRBTree：： GetTailPosition](#gettailposition)|呼叫這個方法，以取得樹狀目錄結尾之專案的位置值。|
|[CRBTree：： GetValueAt](#getvalueat)|呼叫這個方法，以取出儲存在物件中指定位置的值 `CRBTree` 。|
|[CRBTree：： IsEmpty](#isempty)|呼叫這個方法以測試空的樹狀結構物件。|
|[CRBTree：： RemoveAll](#removeall)|呼叫這個方法，以移除物件中的所有元素 `CRBTree` 。|
|[CRBTree：： RemoveAt](#removeat)|呼叫這個方法，以移除物件中指定位置的元素 `CRBTree` 。|
|[CRBTree：： SetValueAt](#setvalueat)|呼叫這個方法來變更儲存在物件中指定位置的值 `CRBTree` 。|

## <a name="remarks"></a>備註

Red-黑色樹狀結構是一個二元搜尋樹狀結構，每個節點使用額外的資訊，以確保它保持「平衡」，也就是說，樹狀結構高度不會以不變的方式成長，而且會影響效能。

此範本類別是設計來供 [CRBMap](../../atl/reference/crbmap-class.md) 和 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)使用。 組成這些衍生類別的大部分方法都是由提供 `CRBTree` 。

如需各種集合類別及其功能和效能特性的完整討論，請參閱 [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>規格需求

**標頭：** atlcoll。h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a> CRBTree：： CPair 類別

包含索引鍵和值元素的類別。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>備註

[CRBTree：： GetAt](#getat)、 [CRBTree：： GetNext](#getnext)和[CRBTree：： GetPrev](#getprev)方法會使用這個類別來存取儲存在樹狀結構中的索引鍵和值元素。

成員如下所示：

|資料成員|描述|
|-|-|
|`m_key`|儲存索引鍵元素的資料成員。|
|`m_value`|儲存 value 元素的資料成員。|

## <a name="crbtreecrbtree"></a><a name="dtor"></a> CRBTree：： ~ CRBTree

解構函式。

```
~CRBTree() throw();
```

### <a name="remarks"></a>備註

釋出任何已配置的資源。 呼叫 [CRBTree：： RemoveAll](#removeall) 來刪除所有元素。

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a> CRBTree：： FindFirstKeyAfter

呼叫這個方法來尋找使用下一個可用索引鍵的元素位置。

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>參數

*key*<br/>
索引鍵值。

### <a name="return-value"></a>傳回值

傳回使用下一個可用索引鍵之元素的位置值。 如果沒有其他元素，則會傳回 Null。

### <a name="remarks"></a>備註

這個方法可讓您輕鬆地跨越樹狀結構，而不需要事先計算位置值。

## <a name="crbtreegetat"></a><a name="getat"></a> CRBTree：： GetAt

呼叫這個方法，以取得樹狀結構中指定位置的專案。

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值。

*key*<br/>
接收金鑰的變數。

*value*<br/>
接收值的變數。

### <a name="return-value"></a>傳回值

前兩種形式會傳回 [CPair](#cpair_class)的指標。 第三種形式會取得指定位置的索引鍵和值。

### <a name="remarks"></a>備註

位置值之前可透過呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： GetTailPosition](#gettailposition)之類的方法來決定。

在 debug 組建中，如果 *pos* 等於 Null，則會發生判斷提示失敗。

## <a name="crbtreegetcount"></a><a name="getcount"></a> CRBTree：： GetCount

呼叫這個方法以取得樹狀結構中的專案數目。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回元素數目 (每個索引鍵/值組都是) 儲存在樹狀結構中的一個元素。

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a> CRBTree：： GetHeadPosition

呼叫這個方法，以取得樹狀結構開頭之專案的位置值。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回樹狀結構開頭之專案的位置值。

### <a name="remarks"></a>備註

傳回的值 `GetHeadPosition` 可搭配 [CRBTree：： GetKeyAt](#getkeyat) 或 [CRBTree：： GetNext](#getnext) 之類的方法使用，以跨越樹狀結構並取得值。

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a> CRBTree：： GetKeyAt

呼叫這個方法，從樹狀結構中的指定位置取得索引鍵。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值。

### <a name="return-value"></a>傳回值

傳回 *儲存在樹狀結構中位置* 位置的索引鍵。

### <a name="remarks"></a>備註

如果 *pos* 不是有效的位置值，結果將無法預期。 在 debug 組建中，如果 *pos* 等於 Null，則會發生判斷提示失敗。

## <a name="crbtreegetnext"></a><a name="getnext"></a> CRBTree：： GetNext

呼叫這個方法，取得儲存在物件中之專案的指標 `CRBTree` ，並將位置前移至下一個專案。

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="return-value"></a>傳回值

將指標傳回至樹狀結構中的下一個 [CPair](#cpair_class) 值。

### <a name="remarks"></a>備註

*Pos*位置計數器會在每次呼叫之後更新。 如果抓取的元素是樹狀結構中的最後一個專案，則 *pos* 會設定為 Null。

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a> CRBTree：： GetNextAssoc

呼叫這個方法來取得儲存在地圖中的元素索引鍵和值，並將位置前移至下一個專案。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

*key*<br/>
範本參數，指定樹狀目錄索引鍵的類型。

*value*<br/>
範本參數，指定樹狀結構值的型別。

### <a name="remarks"></a>備註

*Pos*位置計數器會在每次呼叫之後更新。 如果抓取的元素是樹狀結構中的最後一個專案，則 *pos* 會設定為 Null。

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a> CRBTree：： GetNextKey

呼叫這個方法來取得儲存在樹狀結構中之專案的索引鍵，並將位置前移至下一個專案。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="return-value"></a>傳回值

傳回樹狀結構中下一個索引鍵的參考。

### <a name="remarks"></a>備註

更新目前的位置計數器（ *pos*）。如果樹狀結構中沒有其他專案，則 position 計數器會設定為 Null。

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a> CRBTree：： GetNextValue

呼叫這個方法以取得儲存在樹狀結構中的元素值，並將位置前移至下一個專案。

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="return-value"></a>傳回值

傳回樹狀結構中下一個值的參考。

### <a name="remarks"></a>備註

更新目前的位置計數器（ *pos*）。如果樹狀結構中沒有其他專案，則 position 計數器會設定為 Null。

## <a name="crbtreegetprev"></a><a name="getprev"></a> CRBTree：： GetPrev

呼叫這個方法，取得儲存在物件中之專案的指標 `CRBTree` ，然後將位置更新為前一個元素。

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="return-value"></a>傳回值

傳回儲存在樹狀結構中先前 [CPair](#cpair_class) 值的指標。

### <a name="remarks"></a>備註

更新目前的位置計數器（ *pos*）。如果樹狀結構中沒有其他專案，則 position 計數器會設定為 Null。

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a> CRBTree：： GetTailPosition

呼叫這個方法，以取得樹狀目錄結尾之專案的位置值。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回樹狀目錄結尾之元素的位置值。

### <a name="remarks"></a>備註

傳回的值 `GetTailPosition` 可搭配 [CRBTree：： GetKeyAt](#getkeyat) 或 [CRBTree：： GetPrev](#getprev) 之類的方法使用，以跨越樹狀結構並取得值。

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a> CRBTree：： GetValueAt

呼叫這個方法，以取出儲存在物件中指定位置的值 `CRBTree` 。

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="return-value"></a>傳回值

傳回儲存在物件中指定位置之值的參考 `CRBTree` 。

## <a name="crbtreeisempty"></a><a name="isempty"></a> CRBTree：： IsEmpty

呼叫這個方法以測試空的樹狀結構物件。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果樹狀目錄是空的，則傳回 TRUE，否則傳回 FALSE。

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a> CRBTree：： KINARGTYPE

當索引鍵做為輸入引數傳遞時，所使用的型別。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a> CRBTree：： KOUTARGTYPE

當索引鍵作為輸出引數傳回時，所使用的型別。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a> CRBTree：： RemoveAll

呼叫這個方法，以移除物件中的所有元素 `CRBTree` 。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

清除 `CRBTree` 物件，釋放用來儲存元素的記憶體。

## <a name="crbtreeremoveat"></a><a name="removeat"></a> CRBTree：： RemoveAt

呼叫這個方法，以移除物件中指定位置的元素 `CRBTree` 。

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

### <a name="remarks"></a>備註

移除儲存在指定位置的索引鍵/值組。 用來儲存元素的記憶體會被釋放。 *Pos*所參考的位置會變成無效，而樹狀結構中其他任何專案的位置會維持有效，而不一定會保留相同的順序。

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a> CRBTree：： SetValueAt

呼叫這個方法來變更儲存在物件中指定位置的值 `CRBTree` 。

```cpp
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>參數

*Pos*<br/>
Position 計數器，由先前呼叫 [CRBTree：： GetHeadPosition](#getheadposition) 或 [CRBTree：： FindFirstKeyAfter](#findfirstkeyafter)之類的方法所傳回。

*value*<br/>
要加入至物件的值 `CRBTree` 。

### <a name="remarks"></a>備註

變更儲存在物件中指定位置的 value 元素 `CRBTree` 。

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a> CRBTree：： VINARGTYPE

當值當做輸入引數傳遞時，所使用的型別。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a> CRBTree：： VOUTARGTYPE

當值當做輸出引數傳遞時，所使用的型別。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
