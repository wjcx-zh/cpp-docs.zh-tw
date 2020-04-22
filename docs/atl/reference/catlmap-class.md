---
title: CAtlMap 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 8954eeae28f13fb50643646b41c032588ecc278f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748661"
---
# <a name="catlmap-class"></a>CAtlMap 類別

此類提供創建和管理地圖物件的方法。

## <a name="syntax"></a>語法

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
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
|[CAtlMap::金納格](#kinargtype)|當輸入參數的參數來傳遞時使用的類型|
|[CAtlMap:庫塔格格](#koutargtype)|當將鍵返回為輸出參數時使用的類型。|
|[CAtlMap::維納格](#vinargtype)|當值作為輸入參數傳遞時使用的類型。|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|當值作為輸出參數傳遞時使用的類型。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[CAtlMap:CPair 類](#cpair_class)|包含鍵和值元素的類。|

### <a name="cpair-data-members"></a>CPair 資料成員

|名稱|描述|
|----------|-----------------|
|[CPair::m_key](#m_key)|存儲鍵元素的數據成員。|
|[CPair:m_value](#m_value)|存儲值元素的數據成員。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlMap:CAtlMap](#catlmap)|建構函式。|
|[CAtlMap:_CAtlMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlMap::斷言有效](#assertvalid)|如果不合法`CAtlMap`, 請呼叫此方法以引起 ASSERT。|
|[CAtlMap::D可自動重新哈希](#disableautorehash)|調用此方法以禁用`CAtlMap`物件的自動重新哈希。|
|[CAtlMap:開啟自動復原哈希](#enableautorehash)|呼叫此方法以啟用`CAtlMap`物件的自動重新哈希。|
|[CAtlMap:GetAt](#getat)|呼叫此方法以在地圖中指定位置返回元素。|
|[CAtlMap:取得計數](#getcount)|調用此方法以檢索映射中的元素數。|
|[CAtlMap:取得哈希表大小](#gethashtablesize)|調用此方法以確定地圖哈希表中的條柱數。|
|[CAtlMap:取得鍵](#getkeyat)|調用此方法以檢索存儲在物件中給定位置的`CAtlMap`鍵。|
|[CAtlMap:取得下一個](#getnext)|呼叫此方法以獲取指向存儲在物件中的下一個元素對的`CAtlMap`指標。|
|[CAtlMap:getNextAssoc](#getnextassoc)|獲取下一個反覆運算元素。|
|[CAtlMap:取得下一個鍵](#getnextkey)|調用此方法從物件檢索下一個`CAtlMap`鍵。|
|[CAtlMap:取得下一個值](#getnextvalue)|調用此方法從`CAtlMap`物件獲取下一個值。|
|[CAtlMap:取得起始位置](#getstartposition)|調用此方法以啟動映射反覆運算。|
|[CAtlMap:取得價值At](#getvalueat)|調用此方法以檢索存儲在`CAtlMap`物件中給定位置的值。|
|[CAtlMap:initHashTable](#inithashtable)|調用此方法以初始化哈希表。|
|[CAtlMap::空](#isempty)|調用此方法以測試空地圖物件。|
|[CAtlMap::尋找](#lookup)|調用此方法以查找物件中的`CAtlMap`鍵或值。|
|[CAtlMap:rehash](#rehash)|調用此方法以重新哈希`CAtlMap`物件。|
|[CAtlMap:移除所有](#removeall)|呼叫此方法從`CAtlMap`物件中刪除所有元素。|
|[CAtlMap::刪除AtPos](#removeatpos)|呼叫此方法以移除物件中給定位置的元素`CAtlMap`。|
|[CAtlMap::刪除鍵](#removekey)|呼叫此方法以在給定鍵的情況下從`CAtlMap`物件中刪除元素。|
|[CAtlMap:setat](#setat)|呼叫此方法以將元素對插入到地圖中。|
|[CAtlMap::設定最佳載入](#setoptimalload)|調用此方法以設置`CAtlMap`物件的最佳負載。|
|[CAtlMap::設定價值At](#setvalueat)|呼叫此方法以變更儲存在物件中給定位置的值`CAtlMap`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|替換 或向`CAtlMap`添加新元素。|

## <a name="remarks"></a>備註

`CAtlMap`支援任何給定類型的映射陣列,管理鍵元素及其關聯值的無序陣列。 元素(由鍵和值組成)使用哈希演演演算法存儲,從而能夠高效地存儲和檢索大量數據。

*KTraits*和*VTraits*參數是包含複製或移動元素所需的任何補充代碼的特徵類。

`CAtlMap` [CRBMap](../../atl/reference/crbmap-class.md)類提供了替代項。 `CRBMap`還存儲鍵/值對,但表現出不同的性能特徵。 插入項目、尋找鍵或從`CRBMap`物件中移除鍵所花時間是順序*日誌(n),* 其中*n*是元素數。 對於`CAtlMap`,所有這些操作通常需要恆定的時間,儘管最壞情況可能是順序*為 n*。 因此,在典型情況下,`CAtlMap`速度更快。

和`CRBMap``CAtlMap`之間的另一個區別在遍歷存儲的元素時變得明顯。 在`CRBMap`中,按排序的順序訪問元素。 在`CAtlMap`中,元素未排序,無法推斷任何順序。

當需要存儲少量元素時,請考慮改用[CSimpleMap](../../atl/reference/csimplemap-class.md)類。

有關詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::斷言有效

如果物件無效,`CAtlMap`呼叫此方法以導致 ASSERT。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>備註

在除錯產生中,如果物件無效,`CAtlMap`此方法將導致 ASSERT。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap:CAtlMap

建構函式。

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>參數

*n賓斯*<br/>
提供指向存儲元素的指標的條柱數。 有關 bin的說明,請參閱本主題後面的備註。

*f優負荷*<br/>
最佳負載比。

*fLo 閾值*<br/>
負載比的較低閾值。

*fHiThreshold*<br/>
負載比的上限。

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

`CAtlMap`通過首先在鍵上使用哈希演演演算法創建索引來引用其所有存儲的元素。 此索引引用包含指向存儲元素的指標的「bin」。。 如果 bin 已在使用中,則創建連結列表以訪問後續元素。 遍歷清單比直接存取正確的元素要慢,因此映射結構需要平衡存儲要求和性能。 在大多數情況下,選擇默認參數以提供良好的結果。

負載比率是條柱數與存儲在地圖物件中的元素數的比率。 重新計算地圖結構時 *,fOptimalLoad*參數值將用於計算所需的條柱數。 可以使用[CAtlMap:set 優載入](#setoptimalload)方法更改此值。

*fLoThreshold*參數是負載比可以達到的較低值,在`CAtlMap`重新 計算地圖的最佳大小之前。

*fHiThreshold*參數是負載比`CAtlMap`在 物件重新計算地圖的最佳大小之前可以達到的上限值。

默認情況下,此重新計算過程(稱為重新哈希)處於啟用狀態。 如果要禁用此過程(也許在一次輸入大量數據時),請調用[CAtlMap::D可自動重新哈希](#disableautorehash)方法。 使用[CAtlMap::啟用自動重哈希](#enableautorehash)方法重新啟動它。

*nBlockSize*參數是需要新元素時分配的內存量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。

在存儲任何數據之前,必須使用調用[CAtlMap:::init HashTable](#inithashtable)來初始化哈希錶。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap:_CAtlMap

解構函式。

```
~CAtlMap() throw();
```

### <a name="remarks"></a>備註

釋放任何分配的資源。

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap:CPair 類

包含鍵和值元素的類。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>備註

類由[CAtlMap::GetNext](#getnext)和[CAtlMap:查找](#lookup)來存取映射結構中儲存的鍵和值元素的方法。

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap::D可自動重新哈希

調用此方法以禁用`CAtlMap`物件的自動重新哈希。

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>備註

啟用自動重新哈希時(預設情況下,如果負載值(條柱數與陣列中存儲的元素數的比率)超過創建映射時指定的最大值或最小值,則哈希表中的條柱數將自動重新計算。

`DisableAutoRehash`當大量元素一次添加到地圖中時,最有用。 在每次超出限制時,不要觸發重新哈希過程,而是更高效地調用`DisableAutoRehash`、添加元素,最後調用[CAtlMap::啟用AutoRehash](#enableautorehash)。

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap:開啟自動復原哈希

呼叫此方法以啟用`CAtlMap`物件的自動重新哈希。

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>備註

啟用自動重新哈希時(預設情況下,如果負載值(條柱數與陣列中存儲的元素數的比率)超過創建地圖時指定的最大值或最小值,則哈希表中的條柱數將自動重新計算。

`EnableAutoRefresh`最常在調用[CAtlMap::D可自動復原哈希](#disableautorehash)後使用。

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap:GetAt

呼叫此方法以在地圖中指定位置返回元素。

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

*key*<br/>
指定地圖鍵類型的範本參數。

*value*<br/>
指定地圖值類型的範本參數。

### <a name="return-value"></a>傳回值

返回指向地圖中存儲的當前鍵/值元素對的指標。

### <a name="remarks"></a>備註

在除錯產生中,如果*pos*等於 NULL,則會發生斷言錯誤。

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap:取得計數

調用此方法以檢索映射中的元素數。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

返回地圖物件中的元素數。 單個元素是鍵/值對。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap:取得哈希表大小

調用此方法以確定地圖哈希表中的條柱數。

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>傳回值

返回哈希表中的條柱數。 有關說明,請參閱[CAtlMap:CAtlMap。](#catlmap)

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap:取得鍵

調用此方法以檢索存儲在物件中給定位置的`CAtlMap`鍵。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="return-value"></a>傳回值

返回對存儲在物件中給定位置的鍵的`CAtlMap`引用。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap:取得下一個

呼叫此方法以獲取指向存儲在物件中的下一個元素對的`CAtlMap`指標。

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="return-value"></a>傳回值

返回指向存儲在地圖中的下一對鍵/值元素的指標。 每次調用後,將更新*pos*位置計數器。 如果檢索到的元素是地圖中的最後一個元素,*則 pos*設定為 NULL。

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap:getNextAssoc

獲取下一個反覆運算元素。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

*key*<br/>
指定地圖鍵類型的範本參數。

*value*<br/>
指定地圖值類型的範本參數。

### <a name="remarks"></a>備註

每次調用後,將更新*pos*位置計數器。 如果檢索到的元素是地圖中的最後一個元素,*則 pos*設定為 NULL。

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap:取得下一個鍵

調用此方法從物件檢索下一個`CAtlMap`鍵。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="return-value"></a>傳回值

返回對地圖中下一個鍵的引用。

### <a name="remarks"></a>備註

更新目前位置計數器,*位置*。如果地圖中沒有更多的條目,則位置計數器將設置為 NULL。

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap:取得下一個值

調用此方法從`CAtlMap`物件獲取下一個值。

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="return-value"></a>傳回值

返回對地圖中下一個值的引用。

### <a name="remarks"></a>備註

更新目前位置計數器,*位置*。如果地圖中沒有更多的條目,則位置計數器將設置為 NULL。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap:取得起始位置

調用此方法以啟動映射反覆運算。

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>傳回值

返回起始位置,如果地圖為空,則返回 NULL。

### <a name="remarks"></a>備註

呼叫此方法通過返回可以傳遞給`GetNextAssoc`方法的"位置"值來啟動映射反覆運算。

> [!NOTE]
> 反覆序列是不可預測的

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap:取得價值At

調用此方法以檢索存儲在`CAtlMap`物件中給定位置的值。

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="return-value"></a>傳回值

返回對存儲在物件中給定位置的值的`CAtlMap`引用。

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap:initHashTable

調用此方法以初始化哈希表。

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>參數

*n賓斯*<br/>
哈希表使用的條柱數。 有關說明,請參閱[CAtlMap:CAtlMap。](#catlmap)

*巴羅克現在*<br/>
應分配記憶體的標誌指示。

### <a name="return-value"></a>傳回值

成功初始化時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

`InitHashTable`在哈希表中存儲任何元素之前,必須調用。  如果未顯式調用此方法,則首次使用`CAtlMap`建構函數指定的 bin 計數添加元素時將自動調用它。  否則,將使用*nBins*參數指定的新 bin 計數初始化地圖。

如果*bAllocNow*參數為 false,則哈希表所需的記憶體在首次需要之前不會分配。 如果不確定是否將使用地圖,則此功能非常有用。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap::空

調用此方法以測試空地圖物件。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果地圖為空,則返回 TRUE,否則返回 FALSE。

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::金納格

當將鍵作為輸入參數傳遞時使用的類型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap:庫塔格格

當將鍵返回為輸出參數時使用的類型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap::尋找

調用此方法以查找物件中的`CAtlMap`鍵或值。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
指定標識要備份的元素的鍵。

*value*<br/>
接收上值的變數。

### <a name="return-value"></a>傳回值

如果找到鍵,則方法的第一種形式返回 true,否則為 false。 第二個和第三個窗體返回指向[CPair](#cpair_class)的指標,該指標可用作調用[CAtlMap::getNext](#getnext)等的位置。

### <a name="remarks"></a>備註

`Lookup`使用散列演演演算法快速查找包含與給定鍵參數完全匹配的鍵的映射元素。

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap::運算子\[\]

替換 或向`CAtlMap`添加新元素。

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
要添加或替換的元素的鍵。

### <a name="return-value"></a>傳回值

返回對與給定鍵關聯的值的引用。

### <a name="example"></a>範例

如果金鑰已存在,則替換該元素。 如果金鑰不存在,則添加新元素。 請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap:rehash

調用此方法以重新哈希`CAtlMap`物件。

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>參數

*n賓斯*<br/>
要在哈希表中使用的新條柱數。 有關說明,請參閱[CAtlMap:CAtlMap。](#catlmap)

### <a name="remarks"></a>備註

如果*nBins*為`CAtlMap`0,則根據地圖中的元素數和最佳負載設置計算合理的數位。 通常,重新哈希過程是自動的,但如果調用[了 CAtlMap::D可自動重新哈希](#disableautorehash),則此方法將執行必要的調整大小。

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap:移除所有

呼叫此方法從`CAtlMap`物件中刪除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

清除物件,`CAtlMap`釋放用於儲存元素的記憶體。

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::刪除AtPos

呼叫此方法以移除物件中給定位置的元素`CAtlMap`。

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

### <a name="remarks"></a>備註

刪除存儲在指定位置的鍵/值對。 釋放用於存儲元素的記憶體。 *pos*引用的定位將變為無效,雖然地圖中任何其他元素的定位仍然有效,但它們不一定保留相同的順序。

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::刪除鍵

呼叫此方法以在給定鍵的情況下從`CAtlMap`物件中刪除元素。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
與要刪除的元素對對應的鍵。

### <a name="return-value"></a>傳回值

如果找到並刪除金鑰,則返回 TRUE,在發生故障時返回 FALSE。

### <a name="example"></a>範例

請參閱[CAtlMap::CAtlMap](#catlmap)的範例。

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap:setat

呼叫此方法以將元素對插入到地圖中。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*key*<br/>
要添加到`CAtlMap`物件的鍵值。

*value*<br/>
要新增到物件的值`CAtlMap`。

### <a name="return-value"></a>傳回值

返回鍵/值元素對在物件中`CAtlMap`的位置。

### <a name="remarks"></a>備註

`SetAt`如果找到匹配的鍵,則替換現有元素。 如果未找到該鍵,則創建新的鍵/值對。

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::設定最佳載入

調用此方法以設置`CAtlMap`物件的最佳負載。

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>參數

*f優負荷*<br/>
最佳負載比。

*fLo 閾值*<br/>
負載比的較低閾值。

*fHiThreshold*<br/>
負載比的上限。

*b 雷哈什現在*<br/>
指示是否應重新計算哈希表的標誌。

### <a name="remarks"></a>備註

此方法重新定義`CAtlMap`物件的最佳負載值。 有關各種參數的討論,請參閱[CAtlMap:CAtlMap。](#catlmap) 如果*bRehashNow*為 true,並且元素數超出最小值和最大值,則重新計算哈希表。

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::設定價值At

呼叫此方法以變更儲存在物件中給定位置的值`CAtlMap`。

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*Pos*<br/>
位置計數器,由之前呼叫[CAtlMap 傳回::取得NextAssoc](#getnextassoc)或[CAtlMap::取得起始位置](#getstartposition)。

*value*<br/>
要新增到物件的值`CAtlMap`。

### <a name="remarks"></a>備註

更改存儲在`CAtlMap`物件中給定位置的值元素。

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::維納格

當值作為輸入參數傳遞時使用的類型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

當值作為輸出參數傳遞時使用的類型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap:CPair::m_key

存儲鍵元素的數據成員。

```
const K m_key;
```

### <a name="parameters"></a>參數

*K*<br/>
鍵元素類型。

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap:CPair::m_value

存儲值元素的數據成員。

```
V  m_value;
```

### <a name="parameters"></a>參數

*五*<br/>
值元素類型。

## <a name="see-also"></a>另請參閱

[選取方塊範例](../../overview/visual-cpp-samples.md)<br/>
[更新PV範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[類別概觀](../../atl/atl-class-overview.md)
