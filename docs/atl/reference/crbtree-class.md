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
ms.openlocfilehash: 56c9db9d1a7bcd7fe2a2647d8b1339d223c4b66b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331239"
---
# <a name="crbtree-class"></a>CRBTree 類別

此類提供了創建和使用紅黑樹的方法。

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
鍵元素類型。

*五*<br/>
值元素類型。

*克瓦次克*<br/>
複製或移動關鍵元素的代碼。 有關詳細資訊[,請參閱 CElementTraits 類別](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
複製或移動值元素的代碼。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CRBTree::金納格](#kinargtype)|當將鍵作為輸入參數傳遞時使用的類型。|
|[CRBTree::庫塔格格](#koutargtype)|當將鍵返回為輸出參數時使用的類型。|
|[CRBTree::維納格](#vinargtype)|當值作為輸入參數傳遞時使用的類型。|
|[CRBTree::VOUTARGTYPE](#voutargtype)|當值作為輸出參數傳遞時使用的類型。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[CRBTree:CPair 類](#cpair_class)|包含鍵和值元素的類。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRBTree:*CRBTree](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRBTree::查找第一鍵后](#findfirstkeyafter)|呼叫此方法以尋找使用下一個可用鍵的元素的位置。|
|[CRBTree::取得](#getat)|呼叫此方法以獲取樹中給定位置的元素。|
|[CRBTree:取得計數](#getcount)|呼叫此方法獲取樹中的元素數。|
|[CRBTree:取得頭位置](#getheadposition)|呼叫此方法以獲取樹頭處元素的位置值。|
|[CRBTree::獲取鍵](#getkeyat)|呼叫此方法從樹中的給定位置獲取金鑰。|
|[CRBTree::獲取下一個](#getnext)|調用此方法以獲取指向存儲在物件中的元素的`CRBTree`指標,並將位置推進到下一個元素。|
|[CRBTree::取得NextAssoc](#getnextassoc)|調用此方法獲取存儲在地圖中的元素的鍵和值,並將位置推進到下一個元素。|
|[CRBTree::取得下一個密鑰](#getnextkey)|調用此方法獲取存儲在樹中的元素的鍵,並將位置推進到下一個元素。|
|[CRBTree:取得下一個價值](#getnextvalue)|呼叫此方法取得儲存在樹中的元素的值,並將位置推進到下一個元素。|
|[CRBTree::GetPrev](#getprev)|調用此方法以獲取指向存儲在物件中的元素的`CRBTree`指標,然後將位置更新為上一個元素。|
|[CRBTree::取得尾部位置](#gettailposition)|呼叫此方法以取得樹尾處元素的位置值。|
|[CRBTree::獲取價值](#getvalueat)|調用此方法以檢索存儲在`CRBTree`物件中給定位置的值。|
|[CRBTree::空](#isempty)|調用此方法以測試空樹物件。|
|[CRBTree::刪除所有](#removeall)|呼叫此方法從`CRBTree`物件中刪除所有元素。|
|[CRBTree::刪除At](#removeat)|呼叫此方法以移除物件中給定位置的元素`CRBTree`。|
|[CRBTree::設置價值](#setvalueat)|呼叫此方法以變更儲存在物件中給定位置的值`CRBTree`。|

## <a name="remarks"></a>備註

紅黑樹是一種二進制搜索樹,它每個節點使用額外的資訊,以確保它保持"平衡",也就是說,樹的高度不會增長過大,並影響性能。

此範本類被設計為由[CRBMap](../../atl/reference/crbmap-class.md)和[CRBMultiMap](../../atl/reference/crbmultimap-class.md)使用。 構成這些派生類的大部分方法由`CRBTree`提供 。

有關各種集合類及其特性和性能特徵的更完整的討論,請參閱[ATL 集合類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="crbtreecpair-class"></a><a name="cpair_class"></a>CRBTree:CPair 類

包含鍵和值元素的類。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>備註

此類由[CRBTree:getAt、CRBTree:getNext](#getat)和[CRBTree:GetPrev](#getprev)的方法使用,以存取記憶體在樹結構中的[CRBTree::GetNext](#getnext)鍵和值元素。

成員如下:

|||
|-|-|
|`m_key`|存儲鍵元素的數據成員。|
|`m_value`|存儲值元素的數據成員。|

## <a name="crbtreecrbtree"></a><a name="dtor"></a>CRBTree:*CRBTree

解構函式。

```
~CRBTree() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。 呼叫[CRBTree::刪除所有](#removeall)元素以刪除所有元素。

## <a name="crbtreefindfirstkeyafter"></a><a name="findfirstkeyafter"></a>CRBTree::查找第一鍵后

呼叫此方法以尋找使用下一個可用鍵的元素的位置。

```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>參數

*關鍵*<br/>
索引鍵值。

### <a name="return-value"></a>傳回值

返回使用下一個可用鍵的元素的位置值。 如果沒有更多元素,則返回 NULL。

### <a name="remarks"></a>備註

此方法便於遍歷樹,而無需事先計算位置值。

## <a name="crbtreegetat"></a><a name="getat"></a>CRBTree::取得

呼叫此方法以獲取樹中給定位置的元素。

```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值。

*關鍵*<br/>
接收金鑰的變數。

*值*<br/>
接收值的變數。

### <a name="return-value"></a>傳回值

前兩個窗體返回指向[CPair](#cpair_class)的指標。 第三種形式獲取給定位置的鍵和值。

### <a name="remarks"></a>備註

位置值以前可以通過調用[CRBTree:獲取頭位置](#getheadposition)或[CRBTree::獲取尾位](#gettailposition)等方法來確定。

在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

## <a name="crbtreegetcount"></a><a name="getcount"></a>CRBTree:取得計數

呼叫此方法獲取樹中的元素數。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

返回樹中存儲的元素數(每個鍵/值對是一個元素)。

## <a name="crbtreegetheadposition"></a><a name="getheadposition"></a>CRBTree:取得頭位置

呼叫此方法以獲取樹頭處元素的位置值。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>傳回值

返回樹頭處元素的位置值。

### <a name="remarks"></a>備註

返回`GetHeadPosition`的值可用於[CRBTree:getKeyAt](#getkeyat)或[CRBTree:GetNext](#getnext)遍歷樹並檢索值等方法。

## <a name="crbtreegetkeyat"></a><a name="getkeyat"></a>CRBTree::獲取鍵

呼叫此方法從樹中的給定位置獲取金鑰。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置值。

### <a name="return-value"></a>傳回值

返回存儲在樹中*位置位置*的鍵。

### <a name="remarks"></a>備註

如果*pos*不是有效的位置值,則結果不可預測。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

## <a name="crbtreegetnext"></a><a name="getnext"></a>CRBTree::獲取下一個

調用此方法以獲取指向存儲在物件中的元素的`CRBTree`指標,並將位置推進到下一個元素。

```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="return-value"></a>傳回值

返回指向樹中下一個[CPair](#cpair_class)值的指標。

### <a name="remarks"></a>備註

每次調用後,將更新*pos*位置計數器。 如果檢索到的元素是樹中的最後一個元素,*則 pos*設定為 NULL。

## <a name="crbtreegetnextassoc"></a><a name="getnextassoc"></a>CRBTree::取得NextAssoc

調用此方法獲取存儲在地圖中的元素的鍵和值,並將位置推進到下一個元素。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

*關鍵*<br/>
指定樹鍵類型的範本參數。

*值*<br/>
指定樹值類型的範本參數。

### <a name="remarks"></a>備註

每次調用後,將更新*pos*位置計數器。 如果檢索到的元素是樹中的最後一個元素,*則 pos*設定為 NULL。

## <a name="crbtreegetnextkey"></a><a name="getnextkey"></a>CRBTree::取得下一個密鑰

調用此方法獲取存儲在樹中的元素的鍵,並將位置推進到下一個元素。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="return-value"></a>傳回值

返回對樹中下一個鍵的引用。

### <a name="remarks"></a>備註

更新目前位置計數器,*位置*。如果樹中不再有條目,則位置計數器將設置為 NULL。

## <a name="crbtreegetnextvalue"></a><a name="getnextvalue"></a>CRBTree:取得下一個價值

呼叫此方法取得儲存在樹中的元素的值,並將位置推進到下一個元素。

```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="return-value"></a>傳回值

返回對樹中下一個值的引用。

### <a name="remarks"></a>備註

更新目前位置計數器,*位置*。如果樹中不再有條目,則位置計數器將設置為 NULL。

## <a name="crbtreegetprev"></a><a name="getprev"></a>CRBTree::GetPrev

調用此方法以獲取指向存儲在物件中的元素的`CRBTree`指標,然後將位置更新為上一個元素。

```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="return-value"></a>傳回值

返回指向樹中存儲的上一個[CPair](#cpair_class)值的指標。

### <a name="remarks"></a>備註

更新目前位置計數器,*位置*。如果樹中不再有條目,則位置計數器將設置為 NULL。

## <a name="crbtreegettailposition"></a><a name="gettailposition"></a>CRBTree::取得尾部位置

呼叫此方法以取得樹尾處元素的位置值。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>傳回值

返回樹尾處元素的位置值。

### <a name="remarks"></a>備註

返回`GetTailPosition`的值可用於[CRBTree:getKeyAt](#getkeyat)或[CRBTree:GetPrev](#getprev)遍歷樹並檢索值等方法。

## <a name="crbtreegetvalueat"></a><a name="getvalueat"></a>CRBTree::獲取價值

調用此方法以檢索存儲在`CRBTree`物件中給定位置的值。

```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="return-value"></a>傳回值

返回對存儲在物件中給定位置的值的`CRBTree`引用。

## <a name="crbtreeisempty"></a><a name="isempty"></a>CRBTree::空

調用此方法以測試空樹物件。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果樹為空,則返回 TRUE,否則返回 FALSE。

## <a name="crbtreekinargtype"></a><a name="kinargtype"></a>CRBTree::金納格

當將鍵作為輸入參數傳遞時使用的類型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="crbtreekoutargtype"></a><a name="koutargtype"></a>CRBTree::庫塔格格

當將鍵返回為輸出參數時使用的類型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="crbtreeremoveall"></a><a name="removeall"></a>CRBTree::刪除所有

呼叫此方法從`CRBTree`物件中刪除所有元素。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

清除物件,`CRBTree`釋放用於儲存元素的記憶體。

## <a name="crbtreeremoveat"></a><a name="removeat"></a>CRBTree::刪除At

呼叫此方法以移除物件中給定位置的元素`CRBTree`。

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

### <a name="remarks"></a>備註

刪除存儲在指定位置的鍵/值對。 釋放用於存儲元素的記憶體。 *pos*引用的定位將變為無效,雖然樹中任何其他元素的定位仍然有效,但它們不一定保留相同的順序。

## <a name="crbtreesetvalueat"></a><a name="setvalueat"></a>CRBTree::設置價值

呼叫此方法以變更儲存在物件中給定位置的值`CRBTree`。

```
void SetValueAt(POSITION pos, VINARGTYPE value);
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由以前對[CRBTree 方法的呼叫回:取得頭位置](#getheadposition)或[CRBTree::尋找第一鍵後](#findfirstkeyafter)。

*值*<br/>
要新增到物件的值`CRBTree`。

### <a name="remarks"></a>備註

更改存儲在`CRBTree`物件中給定位置的值元素。

## <a name="crbtreevinargtype"></a><a name="vinargtype"></a>CRBTree::維納格

當值作為輸入參數傳遞時使用的類型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="crbtreevoutargtype"></a><a name="voutargtype"></a>CRBTree::VOUTARGTYPE

當值作為輸出參數傳遞時使用的類型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
