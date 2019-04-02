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
ms.openlocfilehash: 1821532a4d5a3078202f180273b02945b8d8e4ba
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774551"
---
# <a name="catlmap-class"></a>CAtlMap 類別

這個類別提供方法來建立和管理一個 map 物件。

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
索引鍵的項目類型。

*V*<br/>
值的項目型別。

*KTraits*<br/>
程式碼，用來複製或移動索引鍵的項目。 請參閱[CElementTraits 類別](../../atl/reference/celementtraits-class.md)如需詳細資訊。

*VTraits*<br/>
若要複製或移動值的項目所使用的程式碼。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|使用索引鍵做為輸入引數傳遞時的類型|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|索引鍵會傳回做為輸出引數時所使用的類型。|
|[CAtlMap::VINARGTYPE](#vinargtype)|值會傳遞做為輸入引數時所使用的類型。|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|值會傳遞做為輸出引數時所使用的類型。|

### <a name="public-classes"></a>公用類別

|名稱|描述|
|----------|-----------------|
|[CAtlMap::CPair 類別](#cpair_class)|類別，其中包含索引鍵和值的項目。|

### <a name="cpair-data-members"></a>CPair 資料成員

|名稱|描述|
|----------|-----------------|
|[CPair::m_key](#m_key)|儲存索引鍵的項目之資料成員。|
|[CPair::m_value](#m_value)|儲存值的項目之資料成員。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|建構函式。|
|[CAtlMap::~CAtlMap](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|呼叫這個方法會造成判斷提示，如果`CAtlMap`無效。|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|呼叫這個方法，以停用的自動湊`CAtlMap`物件。|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|呼叫這個方法來啟用的自動湊`CAtlMap`物件。|
|[CAtlMap::GetAt](#getat)|呼叫此方法以傳回對應中的指定位置處的項目。|
|[CAtlMap::GetCount](#getcount)|呼叫這個方法來擷取在對應中的項目數。|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|呼叫這個方法來判斷對應的雜湊表中的分類收納數目。|
|[CAtlMap::GetKeyAt](#getkeyat)|呼叫這個方法來擷取儲存在指定的位置中的索引鍵`CAtlMap`物件。|
|[CAtlMap::GetNext](#getnext)|呼叫這個方法來取得對儲存在下一個元素的指標`CAtlMap`物件。|
|[CAtlMap::GetNextAssoc](#getnextassoc)|取得逐一查看的下一個項目。|
|[CAtlMap::GetNextKey](#getnextkey)|呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。|
|[CAtlMap::GetNextValue](#getnextvalue)|呼叫這個方法來取得下一步 的值從`CAtlMap`物件。|
|[CAtlMap::GetStartPosition](#getstartposition)|呼叫此方法以啟動對應的反覆項目。|
|[CAtlMap::GetValueAt](#getvalueat)|呼叫這個方法來擷取儲存在指定的位置中的值`CAtlMap`物件。|
|[CAtlMap::InitHashTable](#inithashtable)|呼叫這個方法來初始化雜湊表。|
|[CAtlMap::IsEmpty](#isempty)|呼叫此方法來測試空白的 map 物件。|
|[CAtlMap::Lookup](#lookup)|呼叫這個方法來查閱索引鍵或值中的`CAtlMap`物件。|
|[CAtlMap::Rehash](#rehash)|呼叫此方法以 rehash`CAtlMap`物件。|
|[CAtlMap::RemoveAll](#removeall)|呼叫這個方法來移除所有項目從`CAtlMap`物件。|
|[CAtlMap::RemoveAtPos](#removeatpos)|呼叫這個方法來移除處的指定位置中的項目`CAtlMap`物件。|
|[CAtlMap::RemoveKey](#removekey)|呼叫這個方法來移除項目從`CAtlMap`指定索引鍵的物件。|
|[CAtlMap::SetAt](#setat)|呼叫這個方法來插入對應中的項目配對。|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|呼叫這個方法來設定最佳的負載`CAtlMap`物件。|
|[CAtlMap::SetValueAt](#setvalueat)|呼叫這個方法來變更儲存在指定的位置中的值`CAtlMap`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|取代或新增新的項目`CAtlMap`。|

## <a name="remarks"></a>備註

`CAtlMap` 支援任何指定的型別，管理未排序的索引鍵的項目和其相關聯的值陣列的對應陣列。 項目 （包含索引鍵和值） 會儲存使用雜湊演算法，可讓大量的有效率地儲存和擷取資料。

*KTraits*並*VTraits*參數會包含任何複製或移動的項目所需的補充程式碼的 traits 類別。

替代`CAtlMap`提供[CRBMap](../../atl/reference/crbmap-class.md)類別。 `CRBMap` 也會儲存索引鍵/值組，但表現不同的效能特性。 要插入的項目所花費的時間查閱索引鍵，或刪除的金鑰`CRBMap`物件屬於訂單*log(n)*，其中*n*是項目數目。 針對`CAtlMap`，所有這些作業通常需要常數的時間，雖然最壞狀況案例可能會對訂單*n*。 因此，在典型的情況下，`CAtlMap`速度。

之間的差異`CRBMap`和`CAtlMap`時逐一查看儲存的項目變得顯而易見。 在  `CRBMap`，項目造訪按照排序順序。 在  `CAtlMap`、 未排序的項目，和任何順序來推斷。

當項目數量少需要儲存時，請考慮使用[CSimpleMap](../../atl/reference/csimplemap-class.md)類別。

如需詳細資訊，請參閱 < [ATL 集合類別](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標頭：** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

呼叫這個方法會造成判斷提示，如果`CAtlMap`物件無效。

```
void AssertValid() const;
```

### <a name="remarks"></a>備註

在偵錯組建中，這個方法會造成判斷提示如果`CAtlMap`物件無效。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

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

*nBins*<br/>
提供的預存的項目指標的分類收納數目。 稍後本主題適用於分類收納組的說明，請參閱備註。

*fOptimalLoad*<br/>
最佳的負載比率。

*fLoThreshold*<br/>
負載比率下限臨界值。

*fHiThreshold*<br/>
負載比率上限臨界值。

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

`CAtlMap` 參考的所有其預存的項目首先會建立索引的索引鍵上使用雜湊演算法。 此索引參考"bin"包含預存的元素的指標。 紙匣已在使用中，如果連結清單會建立來存取後續的項目。 周遊清單低於直接存取正確的項目，並因此網站導覽結構就必須對效能的儲存體需求之間取得平衡。 在大部分情況下提供很好的結果已選擇的預設參數。

負載比例為儲存在 map 物件中的元素數目的分類收納數目的比率。 網站導覽結構時， *fOptimalLoad*參數值會用來計算所需的分類收納數目。 這個值可以使用來變更[CAtlMap::SetOptimalLoad](#setoptimalload)方法。

*FLoThreshold*參數是較低的值之前的負載比率可以觸達`CAtlMap`會重新計算對應的最佳大小。

*FHiThreshold*參數是負載比率可以連線到之前的上限值`CAtlMap`物件將會重新計算對應的最佳大小。

預設為啟用 （又稱為湊） 此重新計算程序。 如果您想要時，停用此程序，可能是輸入一次呼叫資料大量[CAtlMap::DisableAutoRehash](#disableautorehash)方法。 重新啟動它[CAtlMap::EnableAutoRehash](#enableautorehash)方法。

*NBlockSize*參數是配置新的項目時所需的記憶體數量的量值。 較大的區塊大小會減少記憶體配置常式，呼叫，但使用較多資源。

可以儲存任何資料之前，就必須初始化雜湊表，藉由呼叫[CAtlMap::InitHashTable](#inithashtable)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap::~CAtlMap

解構函式。

```
~CAtlMap() throw();
```

### <a name="remarks"></a>備註

會釋放所有配置的資源。

##  <a name="cpair_class"></a>  CAtlMap::CPair 類別

類別，其中包含索引鍵和值的項目。

```
class CPair : public __POSITION
```

### <a name="remarks"></a>備註

此類別由方法[CAtlMap::GetNext](#getnext)並[CAtlMap::Lookup](#lookup)來存取儲存在對應結構的索引鍵和值的元素。

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

呼叫這個方法，以停用的自動湊`CAtlMap`物件。

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>備註

自動重新啟用時 （這是預設情況下），在雜湊表的分類收納數目會自動重新計算如果負載值 （儲存在陣列中的元素數目的分類收納數目的比率） 超過最大或最小值建立對應時所指定。

`DisableAutoRehash` 當大量項目會加入對應一次，則會是最有用。 而不是每次超過限制，請觸發 rehashing 程序，會呼叫更有效率`DisableAutoRehash`、 新增項目，以及最後呼叫[CAtlMap::EnableAutoRehash](#enableautorehash)。

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

呼叫這個方法來啟用的自動湊`CAtlMap`物件。

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>備註

自動重新啟用時 （這是預設情況下），在雜湊表的分類收納數目會自動重新計算如果負載值 （儲存在陣列中的元素數目的分類收納數目的比率） 超過最大或最小值建立對應時所指定。

`EnableAutoRefresh` 在呼叫之後最常用[CAtlMap::DisableAutoRehash](#disableautorehash)。

##  <a name="getat"></a>  CAtlMap::GetAt

呼叫此方法以傳回對應中的指定位置處的項目。

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

*key*<br/>
指定對應的索引鍵的類型樣板參數。

*value*<br/>
指定的對應值的類型樣板參數。

### <a name="return-value"></a>傳回值

讓指標回到目前的索引鍵/值儲存在 map 中的項目組。

### <a name="remarks"></a>備註

在偵錯組建中，判斷提示就會發生錯誤，如果*pos*等於 NULL。

##  <a name="getcount"></a>  CAtlMap::GetCount

呼叫這個方法來擷取在對應中的項目數。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

Map 物件中傳回的項目數。 單一項目是索引鍵/值組。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

呼叫這個方法來判斷對應的雜湊表中的分類收納數目。

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>傳回值

傳回雜湊表中的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)取得說明。

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

呼叫這個方法來擷取儲存在指定的位置中的索引鍵`CAtlMap`物件。

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>傳回值

傳回在指定的位置中儲存的索引鍵的參考`CAtlMap`物件。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getnext"></a>  CAtlMap::GetNext

呼叫這個方法來取得對儲存在下一個元素的指標`CAtlMap`物件。

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>傳回值

讓指標回到下一個配對的索引鍵/值儲存在 map 中的項目。 *Pos*位置計數器會在每次呼叫之後進行更新。 如果擷取的項目是在對應中，最後*pos*設為 NULL。

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

取得逐一查看的下一個項目。

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

*key*<br/>
指定對應的索引鍵的類型樣板參數。

*value*<br/>
指定的對應值的類型樣板參數。

### <a name="remarks"></a>備註

*Pos*位置計數器會在每次呼叫之後進行更新。 如果擷取的項目是在對應中，最後*pos*設為 NULL。

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

呼叫這個方法來擷取下一個索引鍵，從`CAtlMap`物件。

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>傳回值

傳回對應中的下一個索引鍵的參考。

### <a name="remarks"></a>備註

更新的目前位置計數器*pos*。如果在對應中有沒有更多的項目，[位置] 計數器是設為 NULL。

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

呼叫這個方法來取得下一步 的值從`CAtlMap`物件。

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>傳回值

傳回對應中的下一個值的參考。

### <a name="remarks"></a>備註

更新的目前位置計數器*pos*。如果在對應中有沒有更多的項目，[位置] 計數器是設為 NULL。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

呼叫此方法以啟動對應的反覆項目。

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>傳回值

傳回的起始位置或 NULL 會傳回如果 map 是空的。

### <a name="remarks"></a>備註

呼叫這個方法所傳回的位置啟動對應的反覆項目值可以傳遞至`GetNextAssoc`方法。

> [!NOTE]
>  反覆項目序列不是可預測

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

呼叫這個方法來擷取儲存在指定的位置中的值`CAtlMap`物件。

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="return-value"></a>傳回值

傳回儲存在指定的位置中的值的參考`CAtlMap`物件。

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

呼叫這個方法來初始化雜湊表。

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>參數

*nBins*<br/>
雜湊資料表所使用的分類收納數目。 請參閱[CAtlMap::CAtlMap](#catlmap)取得說明。

*bAllocNow*<br/>
旗標指示應該配置記憶體時。

### <a name="return-value"></a>傳回值

在成功初始化，則傳回 TRUE 失敗則為 FALSE。

### <a name="remarks"></a>備註

`InitHashTable` 雜湊表中儲存任何項目之前，必須呼叫。  如果未明確呼叫此方法，它將會自動呼叫第一次的項目加入使用所指定量化計數`CAtlMap`建構函式。  否則，對應將會使用初始化所指定新的量化計數*nBins*參數。

如果*bAllocNow*參數為 false，直到第一次所需的雜湊資料表所需的記憶體不會配置。 這可以是很有用，如果不確定，若要使用對應項目。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="isempty"></a>  CAtlMap::IsEmpty

呼叫此方法來測試空白的 map 物件。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

傳回為 true，則如果 map 是空的 FALSE 否則。

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

做為輸入引數傳遞的索引鍵時所使用的類型。

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

索引鍵會傳回做為輸出引數時所使用的類型。

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

呼叫這個方法來查閱索引鍵或值中的`CAtlMap`物件。

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別的項目，是要查閱的索引鍵。

*value*<br/>
收到的查閱值的變數。

### <a name="return-value"></a>傳回值

第一種形式的方法會傳回 true，如果找到索引鍵為，否則為 false。 第二個和第三個表單傳回的指標[CPair](#cpair_class)這可用來當做位置呼叫[CAtlMap::GetNext](#getnext) ，依此類推。

### <a name="remarks"></a>備註

`Lookup` 若要快速尋找對應項目，包含與指定的索引鍵參數完全相符的索引鍵使用雜湊演算法。

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

取代或新增新的項目`CAtlMap`。

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
要加入或取代之項目的索引鍵。

### <a name="return-value"></a>傳回值

傳回與指定的索引鍵相關聯的值的參考。

### <a name="example"></a>範例

如果金鑰已存在，則會取代項目。 如果索引鍵不存在，則會加入新項目。 範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="rehash"></a>  CAtlMap::Rehash

呼叫此方法以 rehash`CAtlMap`物件。

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>參數

*nBins*<br/>
若要使用的雜湊表的分類收納新的數目。 請參閱[CAtlMap::CAtlMap](#catlmap)取得說明。

### <a name="remarks"></a>備註

如果*nBins*為 0，`CAtlMap`計算合理數目為基礎的地圖與最佳的負載設定中的項目數。 通常 rehashing 程序會自動進行，但若是[CAtlMap::DisableAutoRehash](#disableautorehash)已呼叫，這個方法會執行必要的調整大小。

##  <a name="removeall"></a>  CAtlMap::RemoveAll

呼叫這個方法來移除所有項目從`CAtlMap`物件。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

清除`CAtlMap`物件，即釋放記憶體來儲存項目。

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

呼叫這個方法來移除處的指定位置中的項目`CAtlMap`物件。

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

### <a name="remarks"></a>備註

移除指定位置處儲存的索引鍵/值組。 用來將元素儲存的記憶體，會釋放。 所參考的位置*pos*失效，並在對應中的任何其他項目位置保持有效，就不一定保留相同的順序。

##  <a name="removekey"></a>  CAtlMap::RemoveKey

呼叫這個方法來移除項目從`CAtlMap`指定索引鍵的物件。

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>參數

*key*<br/>
您想要移除對應至項目配對的索引鍵。

### <a name="return-value"></a>傳回值

為 true，則會傳回索引鍵是否找到並移除，失敗則為 FALSE。

### <a name="example"></a>範例

範例，請參閱[CAtlMap::CAtlMap](#catlmap)。

##  <a name="setat"></a>  CAtlMap::SetAt

呼叫這個方法來插入對應中的項目配對。

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*key*<br/>
若要加入的索引鍵值`CAtlMap`物件。

*value*<br/>
要加入至值`CAtlMap`物件。

### <a name="return-value"></a>傳回值

傳回的位置中的索引鍵/值項目組`CAtlMap`物件。

### <a name="remarks"></a>備註

`SetAt` 如果找到相符的索引鍵，會取代現有的項目。 如果找不到索引鍵，則會建立新的索引鍵/值組。

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

呼叫這個方法來設定最佳的負載`CAtlMap`物件。

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>參數

*fOptimalLoad*<br/>
最佳的負載比率。

*fLoThreshold*<br/>
負載比率下限臨界值。

*fHiThreshold*<br/>
負載比率上限臨界值。

*bRehashNow*<br/>
表示是否應該重新計算雜湊表的旗標。

### <a name="remarks"></a>備註

這個方法會重新定義的最佳的負載值`CAtlMap`物件。 請參閱[CAtlMap::CAtlMap](#catlmap)討論的各種不同的參數。 如果*bRehashNow*為 true，而且項目數目超出的最小和最大值，則會重新計算雜湊表。

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

呼叫這個方法來變更儲存在指定的位置中的值`CAtlMap`物件。

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>參數

*pos*<br/>
先前呼叫所傳回的位置計數器[CAtlMap::GetNextAssoc](#getnextassoc)或是[CAtlMap::GetStartPosition](#getstartposition)。

*value*<br/>
要加入至值`CAtlMap`物件。

### <a name="remarks"></a>備註

變更儲存在指定的位置中的值項目`CAtlMap`物件。

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

值會傳遞做為輸入引數時所使用的類型。

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

值會傳遞做為輸出引數時所使用的類型。

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

儲存索引鍵的項目之資料成員。

```
const K m_key;
```

### <a name="parameters"></a>參數

*K*<br/>
索引鍵的項目類型。

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

儲存值的項目之資料成員。

```
V  m_value;
```

### <a name="parameters"></a>參數

*V*<br/>
值的項目型別。

## <a name="see-also"></a>另請參閱

[跑馬燈範例](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV 範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[類別概觀](../../atl/atl-class-overview.md)
