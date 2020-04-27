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
ms.openlocfilehash: b79e6cbd796569e6ba11c96158099de6c30b310a
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168055"
---
# <a name="catlmap-class"></a>CAtlMap 類別

這個類別會提供建立和管理地圖物件的方法。

## <a name="syntax"></a>語法

```cpp
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

### <a name="parameters"></a>參數

*K*<br/>
Key 元素型別。

*&*<br/>
Value 元素類型。

*KTraits*<br/>
用來複製或移動主要元素的程式碼。 如需詳細資訊，請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)。

*VTraits*<br/>
用來複製或移動 value 元素的程式碼。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|將金鑰當做輸入引數傳遞時所使用的類型|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|將索引鍵當做輸出引數傳回時所使用的類型。|
|[CAtlMap::VINARGTYPE](#vinargtype)|將值當做輸入引數傳遞時所使用的類型。|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|將值當做輸出引數傳遞時所使用的類型。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[CAtlMap：： CPair 類別](#cpair_class)|包含索引鍵和值元素的類別。|

### <a name="cpair-data-members"></a>CPair 資料成員

|名稱|描述|
|----------|-----------------|
|[CPair：： m_key](#m_key)|儲存 key 元素的資料成員。|
|[CPair：： m_value](#m_value)|儲存 value 元素的資料成員。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|建構函式。|
|[CAtlMap：： ~ CAtlMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|如果無效，請呼叫這個方法來產生`CAtlMap`判斷提示。|
|[CAtlMap：:D isableAutoRehash](#disableautorehash)|呼叫這個方法來停用`CAtlMap`物件的自動重新雜湊。|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|呼叫這個方法，以啟用`CAtlMap`物件的自動重新雜湊。|
|[CAtlMap：： GetAt](#getat)|呼叫這個方法，以傳回對應中指定位置的元素。|
|[CAtlMap：： GetCount](#getcount)|呼叫這個方法來抓取對應中的專案數。|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|呼叫這個方法，以判斷地圖的雜湊表中的 bin 數目。|
|[CAtlMap::GetKeyAt](#getkeyat)|呼叫這個方法，以取出儲存在`CAtlMap`物件中指定位置的金鑰。|
|[CAtlMap：： GetNext](#getnext)|呼叫這個方法，以取得儲存在`CAtlMap`物件中下一個元素組的指標。|
|[CAtlMap::GetNextAssoc](#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CAtlMap::GetNextKey](#getnextkey)|呼叫這個方法，以從`CAtlMap`物件取出下一個索引鍵。|
|[CAtlMap::GetNextValue](#getnextvalue)|呼叫這個方法，以從`CAtlMap`物件取得下一個值。|
|[CAtlMap::GetStartPosition](#getstartposition)|呼叫這個方法來啟動對應反復專案。|
|[CAtlMap::GetValueAt](#getvalueat)|呼叫這個方法，以抓取`CAtlMap`物件中指定位置所儲存的值。|
|[CAtlMap::InitHashTable](#inithashtable)|呼叫這個方法來初始化雜湊表。|
|[CAtlMap：： IsEmpty](#isempty)|呼叫這個方法來測試空的 map 物件。|
|[CAtlMap：： Lookup](#lookup)|呼叫這個方法，以查閱物件中的`CAtlMap`索引鍵或值。|
|[CAtlMap：： Rehash](#rehash)|呼叫這個方法以 rehash `CAtlMap`物件。|
|[CAtlMap：： RemoveAll](#removeall)|呼叫這個方法，以從`CAtlMap`物件中移除所有元素。|
|[CAtlMap::RemoveAtPos](#removeatpos)|呼叫這個方法，以移除`CAtlMap`物件中指定位置的專案。|
|[CAtlMap::RemoveKey](#removekey)|呼叫這個方法，以在指定索引鍵`CAtlMap`的情況下，從物件中移除元素。|
|[CAtlMap：： SetAt](#setat)|呼叫這個方法，將元素組插入對應中。|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|呼叫這個方法，以設定`CAtlMap`物件的最佳負載。|
|[CAtlMap::SetValueAt](#setvalueat)|呼叫這個方法，以變更儲存在`CAtlMap`物件中指定位置的值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|取代或將新的專案加入至`CAtlMap`。|

## <a name="remarks"></a>備註

`CAtlMap`提供任何給定類型的對應陣列支援、管理索引鍵專案的未排序陣列及其相關聯的值。 專案（包含索引鍵和值）會使用雜湊演算法來儲存，以有效率地儲存和抓取大量資料。

*KTraits*和*VTraits*參數是特性類別，其中包含複製或移動元素所需的任何補充程式碼。

的替代方法`CAtlMap`是由[CRBMap](../../atl/reference/crbmap-class.md)類別所提供。 `CRBMap`也會儲存索引鍵/值組，但會展現不同的效能特性。 插入專案、查詢索引鍵，或從`CRBMap`物件中刪除索引鍵的時間，都是順序*記錄（n）*，其中*n*是元素的數目。 在`CAtlMap`中，所有這些作業通常會花很長的時間，雖然最壞的情況可能是 order *n*。 因此，在一般的情況下`CAtlMap` ，速度會更快。

當逐一查看已`CRBMap`儲存`CAtlMap`的專案時，和之間的其他差異會很明顯。 在中`CRBMap`，會以排序的順序來流覽元素。 在中`CAtlMap`，不會排序元素，而且不會推斷順序。

當需要儲存少量的元素時，請考慮改用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。

如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll。h

## <a name="catlmapassertvalid"></a><a name="assertvalid"></a>CAtlMap::AssertValid

如果`CAtlMap`物件無效，請呼叫這個方法來產生判斷提示。

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>備註

在 debug 組建中，如果`CAtlMap`物件無效，這個方法會造成判斷提示。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapcatlmap"></a><a name="catlmap"></a>CAtlMap::CAtlMap

建構函式。

```cpp
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>參數

*nBins*<br/>
提供預存元素指標的 bin 數目。 如需 bin 的說明，請參閱本主題稍後的備註。

*fOptimalLoad*<br/>
最佳的載入比例。

*fLoThreshold*<br/>
負載比率的下限臨界值。

*fHiThreshold*<br/>
負載比率的上限閾值。

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

`CAtlMap`參考所有儲存的專案，方法是先使用金鑰的雜湊演算法來建立索引。 此索引會參考「bin」，其中包含預存專案的指標。 如果 bin 已在使用中，則會建立連結清單來存取後續的元素。 遍歷清單比直接存取正確的元素慢，因此對應結構必須平衡儲存需求與效能。 在大部分情況下，已選擇預設參數以提供良好的結果。

負載比率是指將 bin 數目與儲存在 map 物件中的元素數目的比率。 重新計算地圖結構時，會使用*fOptimalLoad*參數值來計算所需的 bin 數目。 您可以使用[CAtlMap：： SetOptimalLoad](#setoptimalload)方法來變更此值。

*FLoThreshold*參數是負載比率可以達到的較低值， `CAtlMap`因此會重新計算對應的最佳大小。

*FHiThreshold*參數是在`CAtlMap`物件重新計算地圖的最佳大小之前，負載比率可達到的上限值。

預設會啟用此重新計算進程（稱為重新雜湊）。 如果您想要停用此進程，也許在一次輸入大量資料時，請呼叫[CAtlMap：:D isableautorehash](#disableautorehash)方法。 使用[CAtlMap：： EnableAutoRehash](#enableautorehash)方法重新開機它。

*NBlockSize*參數是當需要新元素時所配置的記憶體數量的量值。 較大的區塊大小會減少對記憶體配置常式的呼叫，但會使用更多資源。

在可以儲存任何資料之前，必須先呼叫[CAtlMap：： InitHashTable](#inithashtable)來初始化雜湊表。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

## <a name="catlmapcatlmap"></a><a name="dtor"></a>CAtlMap：： ~ CAtlMap

解構函式。

```cpp
~CAtlMap() throw();
```

### <a name="remarks"></a>備註

釋放任何已配置的資源。

## <a name="catlmapcpair-class"></a><a name="cpair_class"></a>CAtlMap：： CPair 類別

包含索引鍵和值元素的類別。

```cpp
class CPair : public __POSITION
```

### <a name="remarks"></a>備註

這個類別是由[CAtlMap：： GetNext](#getnext)和[CAtlMap：： Lookup](#lookup)方法用來存取儲存在對應結構中的索引鍵和值元素。

## <a name="catlmapdisableautorehash"></a><a name="disableautorehash"></a>CAtlMap：:D isableAutoRehash

呼叫這個方法來停用`CAtlMap`物件的自動重新雜湊。

```cpp
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>備註

當自動重新雜湊啟用時（預設值），如果載入值（陣列數目與儲存在陣列中的專案數目的比率）超過建立對應時指定的最大或最小值，則雜湊表中的 bin 數目會自動重新計算。

`DisableAutoRehash`當一次將大量專案新增至地圖時，是最有用的。 並不會在每次超過限制時觸發重新雜湊程式，而是呼叫`DisableAutoRehash`、加入元素，最後呼叫[CAtlMap：： EnableAutoRehash](#enableautorehash)，會更有效率。

## <a name="catlmapenableautorehash"></a><a name="enableautorehash"></a>CAtlMap::EnableAutoRehash

呼叫這個方法，以啟用`CAtlMap`物件的自動重新雜湊。

```cpp
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>備註

啟用自動重新雜湊時（預設值），如果載入值（陣列數目與儲存在陣列中的元素數目的比率）超過建立對應時指定的最大或最小值，則雜湊表中的 bin 數目會自動重新計算。

`EnableAutoRefresh`在呼叫[CAtlMap：:D isableautorehash](#disableautorehash)之後，最常使用。

## <a name="catlmapgetat"></a><a name="getat"></a>CAtlMap：： GetAt

呼叫這個方法，以傳回對應中指定位置的元素。

```cpp
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

*key*<br/>
範本參數，指定地圖的索引鍵類型。

*值*<br/>
範本參數，指定對應值的類型。

### <a name="return-value"></a>傳回值

傳回儲存在對應中的目前索引鍵/值專案對的指標。

### <a name="remarks"></a>備註

在「偵錯工具組建」中，如果*pos*等於 Null，就會發生判斷提示錯誤。

## <a name="catlmapgetcount"></a><a name="getcount"></a>CAtlMap：： GetCount

呼叫這個方法來抓取對應中的專案數。

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回 map 物件中的元素數目。 單一元素是索引鍵/值組。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapgethashtablesize"></a><a name="gethashtablesize"></a>CAtlMap::GetHashTableSize

呼叫這個方法，以判斷地圖的雜湊表中的 bin 數目。

```cpp
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>傳回值

傳回雜湊表中的 bin 數目。 如需說明，請參閱[CAtlMap：： CAtlMap](#catlmap) 。

## <a name="catlmapgetkeyat"></a><a name="getkeyat"></a>CAtlMap::GetKeyAt

呼叫這個方法，以取出儲存在`CAtlMap`物件中指定位置的金鑰。

```cpp
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="return-value"></a>傳回值

傳回儲存在`CAtlMap`物件中指定位置之索引鍵的參考。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapgetnext"></a><a name="getnext"></a>CAtlMap：： GetNext

呼叫這個方法，以取得儲存在`CAtlMap`物件中下一個元素組的指標。

```cpp
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="return-value"></a>傳回值

傳回儲存在對應中的下一對索引鍵/值元素的指標。 [ *Pos*位置] 計數器會在每次呼叫之後更新。 如果所抓取的元素是對應中的最後一個， *pos*會設定為 Null。

## <a name="catlmapgetnextassoc"></a><a name="getnextassoc"></a>CAtlMap::GetNextAssoc

取得用於反覆運算的下一個專案。

```cpp
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

*key*<br/>
範本參數，指定地圖的索引鍵類型。

*值*<br/>
範本參數，指定對應值的類型。

### <a name="remarks"></a>備註

[ *Pos*位置] 計數器會在每次呼叫之後更新。 如果所抓取的元素是對應中的最後一個， *pos*會設定為 Null。

## <a name="catlmapgetnextkey"></a><a name="getnextkey"></a>CAtlMap::GetNextKey

呼叫這個方法，以從`CAtlMap`物件取出下一個索引鍵。

```cpp
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="return-value"></a>傳回值

傳回對應中下一個索引鍵的參考。

### <a name="remarks"></a>備註

更新目前的位置計數器*pos*。如果對應中沒有其他專案，則 position 計數器會設定為 Null。

## <a name="catlmapgetnextvalue"></a><a name="getnextvalue"></a>CAtlMap::GetNextValue

呼叫這個方法，以從`CAtlMap`物件取得下一個值。

```cpp
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="return-value"></a>傳回值

傳回對應中下一個值的參考。

### <a name="remarks"></a>備註

更新目前的位置計數器*pos*。如果對應中沒有其他專案，則 position 計數器會設定為 Null。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapgetstartposition"></a><a name="getstartposition"></a>CAtlMap::GetStartPosition

呼叫這個方法來啟動對應反復專案。

```cpp
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回開始位置，如果對應是空的，則傳回 Null。

### <a name="remarks"></a>備註

呼叫這個方法，藉由傳回可傳遞至`GetNextAssoc`方法的位置值來啟動對應反復專案。

> [!NOTE]
> 反復專案序列無法預測

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapgetvalueat"></a><a name="getvalueat"></a>CAtlMap::GetValueAt

呼叫這個方法，以抓取`CAtlMap`物件中指定位置所儲存的值。

```cpp
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="return-value"></a>傳回值

傳回`CAtlMap`物件中指定位置所儲存值的參考。

## <a name="catlmapinithashtable"></a><a name="inithashtable"></a>CAtlMap::InitHashTable

呼叫這個方法來初始化雜湊表。

```cpp
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>參數

*nBins*<br/>
雜湊表使用的 bin 數目。 如需說明，請參閱[CAtlMap：： CAtlMap](#catlmap) 。

*bAllocNow*<br/>
應配置記憶體時的旗標指示。

### <a name="return-value"></a>傳回值

成功初始化時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

`InitHashTable`必須先呼叫，然後才會在雜湊表中儲存任何元素。  如果未明確呼叫這個方法，則會在第一次使用此函式所指定`CAtlMap`的 bin 計數加入元素時自動呼叫。  否則，將會使用*nBins*參數所指定的新 bin 計數來初始化對應。

如果*bAllocNow*參數為 false，雜湊表所需的記憶體必須等到第一次需要時才會進行配置。 如果您不確定是否要使用對應，這會很有用。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapisempty"></a><a name="isempty"></a>CAtlMap：： IsEmpty

呼叫這個方法來測試空的 map 物件。

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果對應是空的，則傳回 TRUE，否則傳回 FALSE。

## <a name="catlmapkinargtype"></a><a name="kinargtype"></a>CAtlMap::KINARGTYPE

將金鑰當做輸入引數傳遞時所使用的類型。

```cpp
typedef KTraits::INARGTYPE KINARGTYPE;
```

## <a name="catlmapkoutargtype"></a><a name="koutargtype"></a>CAtlMap::KOUTARGTYPE

將索引鍵當做輸出引數傳回時所使用的類型。

```cpp
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

## <a name="catlmaplookup"></a><a name="lookup"></a>CAtlMap：： Lookup

呼叫這個方法，以查閱物件中的`CAtlMap`索引鍵或值。

```cpp
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別要查閱之元素的索引鍵。

*值*<br/>
接收查閱值的變數。

### <a name="return-value"></a>傳回值

如果找到索引鍵，則方法的第一個形式會傳回 true，否則傳回 false。 第二個和第三個表單會傳回[CPair](#cpair_class)的指標，可做為呼叫[CAtlMap：： GetNext](#getnext)的位置，依此類推。

### <a name="remarks"></a>備註

`Lookup`會使用雜湊演算法來快速找出包含金鑰的對應元素，此索引鍵完全符合指定的索引鍵參數。

## <a name="catlmapoperator-"></a><a name="operator_at"></a>CAtlMap：： operator\[\]

取代或將新的專案加入至`CAtlMap`。

```cpp
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
要加入或取代之元素的索引鍵。

### <a name="return-value"></a>傳回值

傳回與指定索引鍵相關聯之值的參考。

### <a name="example"></a>範例

如果索引鍵已經存在，則會取代元素。 如果索引鍵不存在，則會新增新的元素。 請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmaprehash"></a><a name="rehash"></a>CAtlMap：： Rehash

呼叫這個方法以 rehash `CAtlMap`物件。

```cpp
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>參數

*nBins*<br/>
要在雜湊表中使用的新 bin 數目。 如需說明，請參閱[CAtlMap：： CAtlMap](#catlmap) 。

### <a name="remarks"></a>備註

如果*nBins*為0， `CAtlMap`會根據對應中的專案數目和最佳的載入設定來計算合理的數位。 通常重新雜湊程式是自動的，但如果已呼叫[CAtlMap：:D isableautorehash](#disableautorehash) ，這個方法將會執行所需的調整大小。

## <a name="catlmapremoveall"></a><a name="removeall"></a>CAtlMap：： RemoveAll

呼叫這個方法，以從`CAtlMap`物件中移除所有元素。

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

清除`CAtlMap`物件，釋放用來儲存元素的記憶體。

## <a name="catlmapremoveatpos"></a><a name="removeatpos"></a>CAtlMap::RemoveAtPos

呼叫這個方法，以移除`CAtlMap`物件中指定位置的專案。

```cpp
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

### <a name="remarks"></a>備註

移除儲存在指定位置的索引鍵/值組。 釋放用來儲存元素的記憶體。 *Pos*所參考的位置變成無效，而對應中任何其他專案的位置仍然有效，不一定會保留相同的順序。

## <a name="catlmapremovekey"></a><a name="removekey"></a>CAtlMap::RemoveKey

呼叫這個方法，以在指定索引鍵`CAtlMap`的情況下，從物件中移除元素。

```cpp
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
對應至您想要移除之元素組的索引鍵。

### <a name="return-value"></a>傳回值

如果找到並移除索引鍵，則傳回 TRUE，否則會傳回 FALSE。

### <a name="example"></a>範例

請參閱[CAtlMap：： CAtlMap](#catlmap)的範例。

## <a name="catlmapsetat"></a><a name="setat"></a>CAtlMap：： SetAt

呼叫這個方法，將元素組插入對應中。

```cpp
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*key*<br/>
要加入至`CAtlMap`物件的索引鍵值。

*值*<br/>
要加入至`CAtlMap`物件的值。

### <a name="return-value"></a>傳回值

傳回`CAtlMap`物件中索引鍵/值元素組的位置。

### <a name="remarks"></a>備註

`SetAt`如果找到相符的索引鍵，則取代現有的元素。 如果找不到索引鍵，則會建立新的索引鍵/值組。

## <a name="catlmapsetoptimalload"></a><a name="setoptimalload"></a>CAtlMap::SetOptimalLoad

呼叫這個方法，以設定`CAtlMap`物件的最佳負載。

```cpp
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>參數

*fOptimalLoad*<br/>
最佳的載入比例。

*fLoThreshold*<br/>
負載比率的下限臨界值。

*fHiThreshold*<br/>
負載比率的上限閾值。

*bRehashNow*<br/>
表示是否應該重新計算雜湊表的旗標。

### <a name="remarks"></a>備註

這個方法會為`CAtlMap`物件重新定義最佳的載入值。 如需各種參數的討論，請參閱[CAtlMap：： CAtlMap](#catlmap) 。 如果*bRehashNow*為 true，而元素的數目超出最小和最大值，則會重新計算雜湊表。

## <a name="catlmapsetvalueat"></a><a name="setvalueat"></a>CAtlMap::SetValueAt

呼叫這個方法，以變更儲存在`CAtlMap`物件中指定位置的值。

```cpp
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*採購*<br/>
Position 計數器，先前對[CAtlMap：： GetNextAssoc](#getnextassoc)或[CAtlMap：： GetStartPosition](#getstartposition)的呼叫傳回。

*值*<br/>
要加入至`CAtlMap`物件的值。

### <a name="remarks"></a>備註

變更儲存在`CAtlMap`物件中指定位置的值元素。

## <a name="catlmapvinargtype"></a><a name="vinargtype"></a>CAtlMap::VINARGTYPE

將值當做輸入引數傳遞時所使用的類型。

```cpp
typedef VTraits::INARGTYPE VINARGTYPE;
```

## <a name="catlmapvoutargtype"></a><a name="voutargtype"></a>CAtlMap::VOUTARGTYPE

將值當做輸出引數傳遞時所使用的類型。

```cpp
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

## <a name="catlmapcpairm_key"></a><a name="m_key"></a>CAtlMap：： CPair：： m_key

儲存 key 元素的資料成員。

```cpp
const K m_key;
```

### <a name="parameters"></a>參數

*K*<br/>
Key 元素型別。

## <a name="catlmapcpairm_value"></a><a name="m_value"></a>CAtlMap：： CPair：： m_value

儲存 value 元素的資料成員。

```cpp
V  m_value;
```

### <a name="parameters"></a>參數

*&*<br/>
Value 元素類型。

## <a name="see-also"></a>另請參閱

[天棚範例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[類別概觀](../../atl/atl-class-overview.md)
