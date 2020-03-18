---
title: CMapStringToOb 類別
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418535"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb 類別

字典集合類別，這個類別會將唯一的 `CString` 物件對應至 `CObject` 指標。

## <a name="syntax"></a>語法

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb：： CMapStringToOb](#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb：： GetCount](#getcount)|傳回此對應中的元素數目。|
|[CMapStringToOb：： GetHashTableSize](#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapStringToOb：： GetNextAssoc](#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapStringToOb：： GetSize](#getsize)|傳回此對應中的元素數目。|
|[CMapStringToOb：： GetStartPosition](#getstartposition)|傳回第一個元素的位置。|
|[CMapStringToOb：： HashKey](#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapStringToOb：： InitHashTable](#inithashtable)|初始化雜湊表。|
|[CMapStringToOb：： IsEmpty](#isempty)|測試空白對應條件（沒有元素）。|
|[CMapStringToOb：： Lookup](#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapStringToOb：： LookupKey](#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapStringToOb：： RemoveAll](#removeall)|移除這個對應中的所有元素。|
|[CMapStringToOb：： RemoveKey](#removekey)|移除索引鍵所指定的元素。|
|[CMapStringToOb：： SetAt](#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb：： operator \[ \]](#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

將 `CString`- `CObject*` 組（元素）插入對應之後，您就可以使用字串或 `CString` 值做為索引鍵，有效率地抓取或刪除該配對。 您也可以反復查看對應中的所有元素。

「位置」類型的變數會用於所有對應變化中的替代專案存取。 您可以使用位置「記住」專案並逐一查看對應。 您可能會認為這個反復專案是依照索引鍵值來排列;不是。 所抓取專案的順序不確定。

`CMapStringToOb` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 每個專案都會依次序列化，因為會使用多載插入（ **<<** ）運算子或 `Serialize` 成員函式來儲存對應。

如果您需要對應中個別元素的診斷傾印（`CString` 值和 `CObject` 內容），您必須將傾印內容的深度設定為1或更大。

當 `CMapStringToOb` 物件被刪除，或移除其元素時，就會移除 `CString` 物件和 `CObject` 指標。 `CObject` 指標所參考的物件並不會遭到終結。

對應類別衍生類似于清單衍生。 如需特殊用途清單類別之衍生的圖例，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

##  <a name="cmapstringtoob"></a>CMapStringToOb：： CMapStringToOb

建立空的 `CString`對 `CObject*` 對應。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
指定用於擴充對應的記憶體配置資料細微性。

### <a name="remarks"></a>備註

當對應增加時，會以*nBlockSize*專案的單位來配置記憶體。

下表顯示其他類似 `CMapStringToOb:: CMapStringToOb`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb （INT_PTR** `nBlockSize` **= 10）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr （INT_PTR** `nBlockSize` **= 10）;**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

##  <a name="getcount"></a>CMapStringToOb：： GetCount

決定地圖中有多少元素。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

這個對應中的元素數目。

### <a name="remarks"></a>備註

下表顯示其他類似 `CMapStringToOb::GetCount`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>CMapStringToOb：： GetHashTableSize

判斷雜湊表中目前的元素數目。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>傳回值

傳回雜湊表中的元素數目。

### <a name="remarks"></a>備註

下表顯示其他類似 `CMapStringToOb::GetHashTableSize`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize （） const;**|

##  <a name="getnextassoc"></a>CMapStringToOb：： GetNextAssoc

抓取*rNextPosition*的 map 元素，然後更新*rNextPosition*來參考對應中的下一個專案。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*rNextPosition*<br/>
指定前一個 `GetNextAssoc` 或 `GetStartPosition` 呼叫所傳回之位置值的參考。

*rKey*<br/>
指定所抓取元素的傳回索引鍵（字串）。

*rValue*<br/>
指定所抓取元素的傳回值（`CObject` 指標）。 如需此參數的詳細資訊，請參閱備註。

### <a name="remarks"></a>備註

此函式最適合用來逐一查看對應中的所有元素。 請注意，位置序列不一定和索引鍵值順序相同。

如果所抓取的元素是對應中的最後一個專案，則*rNextPosition*的新值會設定為 Null。

針對*右*值參數，請務必將您的物件類型轉型為**CObject\*&** ，這是編譯器所需的內容，如下列範例所示：

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

這對於以範本為基礎的對應 `GetNextAssoc` 而言並不適用。

下表顯示其他類似 `CMapStringToOb::GetNextAssoc`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，void\*&** *rKey* **，void\*&** *rValue* **） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，void\*&** *rKey* **，WORD &** *右***值） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **、CString &** *rKey* **、void\*&** *右*值 **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **，cstring &** *rKey* **，cstring &** *rValue* **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **、WORD &** *rKey* **、CObject\*&** *右*值 **） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void GetNextAssoc （POSITION &** *rNextPosition* **、WORD &** *rKey* **、void\*&** *右*值 **） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程式的結果如下：

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>CMapStringToOb：： GetSize

傳回對應元素的數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

對應中的專案數。

### <a name="remarks"></a>備註

呼叫這個方法來抓取對應中的專案數。

下表顯示其他類似 `CMapStringToOb::GetSize`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>CMapStringToOb：： GetStartPosition

藉由傳回可傳遞至 `GetNextAssoc` 呼叫的位置值，來啟動對應反復專案。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，表示反覆運算對應的開始位置。如果對應是空的，則為 Null。

### <a name="remarks"></a>備註

反復專案序列無法預測;因此，「對應」中的「第一個元素」沒有特殊意義。

下表顯示其他類似 `CMapStringToOb::GetStartPosition`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition （） const;**|

### <a name="example"></a>範例

請參閱[CMapStringToOb：： GetNextAssoc](#getnextassoc)的範例。

##  <a name="hashkey"></a>CMapStringToOb：： HashKey

計算指定之索引鍵的雜湊值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
要計算其雜湊值的索引鍵。

### <a name="return-value"></a>傳回值

索引鍵的雜湊值

### <a name="remarks"></a>備註

下表顯示其他類似 `CMapStringToOb::HashKey`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey （void** <strong>\*</strong> `key` **） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey （void** <strong>\*</strong> `key` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey （LPCTSTR** `key` **） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey （LPCTSTR** `key` **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey （WORD** `key` **） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey （WORD** `key` **） const;**|

##  <a name="inithashtable"></a>CMapStringToOb：： InitHashTable

初始化雜湊表。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>參數

*hashSize*<br/>
雜湊表中的專案數。

*bAllocNow*<br/>
如果為 TRUE，則會在初始化時配置雜湊表;否則，會在需要時配置資料表。

### <a name="remarks"></a>備註

為了達到最佳效能，雜湊表大小應該是質數。 若要將衝突降到最低，大小應該大約大於最大預期資料集的20%。

下表顯示其他類似 `CMapStringToOb::InitHashTable`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void InitHashTable （UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE）;**|

##  <a name="isempty"></a>CMapStringToOb：： IsEmpty

判斷對應是否為空的。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

若此對應不包含任何專案，則為非零值;否則為0。

### <a name="example"></a>範例

請參閱[RemoveAll](#removeall)的範例。

### <a name="remarks"></a>備註

下表顯示其他類似于**CMapStringToOb：： IsEmpty**的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty （） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty （） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty （） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty （） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty （） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty （） const;**|

##  <a name="lookup"></a>CMapStringToOb：： Lookup

根據 `CString` 值傳回 `CObject` 指標。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別要查閱之元素的字串索引鍵。

*rValue*<br/>
指定所查閱元素中的傳回值。

### <a name="return-value"></a>傳回值

如果找到元素，則為非零;否則為0。

### <a name="remarks"></a>備註

`Lookup` 使用雜湊演算法，快速找出索引鍵符合確切（`CString` 值）的 map 元素。

下表顯示其他類似 `CMapStringToOb::LookUp`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup （void** <strong>\*</strong> `key` **，void\*&** `rValue` **） const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup （void** <strong>\*</strong> `key` **，WORD &** `rValue` **） const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup （LPCTSTR** `key` **，void\*&** `rValue` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup （LPCTSTR** `key` **，CString &** `rValue` **） const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup （WORD** `key` **，CObject\*&** `rValue` **） const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup （WORD** `key` **，void\*&** `rValue` **） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>CMapStringToOb：： LookupKey

傳回與指定之索引鍵值相關聯之索引鍵的參考。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別要查閱之元素的字串索引鍵。

*rKey*<br/>
關聯索引鍵的參考。

### <a name="return-value"></a>傳回值

如果找到索引鍵，則為非零;否則為0。

### <a name="remarks"></a>備註

如果在關聯的元素從對應中移除之後，或在終結對應之後使用，則使用索引鍵的參考就不安全。

下表顯示其他類似 `CMapStringToOb:: LookupKey`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey （LPCTSTR** `key` **，LPCTSTR &** `rKey` **） const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey （LPCTSTR** `key` **，LPCTSTR &** `rKey` **） const;**|

##  <a name="operator_at"></a>CMapStringToOb：： operator []

`SetAt` 成員函式的方便替代。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>傳回值

`CObject` 物件指標的參考;如果對應是空的或索引*鍵*超出範圍，則為 Null。

### <a name="remarks"></a>備註

因此，它只能用在指派語句的左邊（左值）。 如果沒有具有指定之索引鍵的對應元素，則會建立新的元素。

沒有與這個運算子相等的「右側」（右值），因為在對應中可能找不到索引鍵。 使用 `Lookup` 成員函式進行專案抓取。

下表顯示其他類似 `CMapStringToOb::operator []`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& operator\[] （void \*</strong> `key` **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & 運算子\[] （void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator\[] （lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & 運算子\[] （lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 運算子\[] （單字**`key` **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& 運算子\[] （單字**`key` **\);**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程式的結果如下：

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>CMapStringToOb：： RemoveAll

移除這個對應中的所有專案，並終結 `CString` 的索引鍵物件。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

每個索引鍵所參考的 `CObject` 物件都不會終結。 如果您不確定參考的 `CObject` 物件已終結，`RemoveAll` 函數可能會造成記憶體流失。

如果對應已是空的，此函式就會正常運作。

下表顯示其他類似 `CMapStringToOb::RemoveAll`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll （）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll （）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll （）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll （）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll （）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>CMapStringToOb：： RemoveKey

查閱對應至所提供索引鍵的對應專案;然後，如果找到索引鍵，則會移除專案。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>參數

*key*<br/>
指定用於對應查閱的字串。

### <a name="return-value"></a>傳回值

如果找到並成功移除專案，則為非零;否則為0。

### <a name="remarks"></a>備註

如果 `CObject` 物件不會在其他地方刪除，這可能會造成記憶體流失。

下表顯示其他類似 `CMapStringToOb::RemoveKey`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey （void** <strong>\*</strong> `key` **）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey （void** <strong>\*</strong> `key` **）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey （LPCTSTR** `key` **）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey （LPCTSTR** `key` **）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey （WORD** `key` **）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey （WORD** `key` **）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程式的結果如下：

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>CMapStringToOb：： SetAt

主要的方法是將元素插入對應中。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>參數

*key*<br/>
指定做為新元素索引鍵的字串。

*newValue*<br/>
指定做為新元素值的 `CObject` 指標。

### <a name="remarks"></a>備註

首先，會查閱索引鍵。 如果找到索引鍵，則對應的值會變更;否則會建立新的索引鍵/值元素。

下表顯示其他類似 `CMapStringToOb::SetAt`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Void SetAt （void** <strong>\*</strong> `key` **，void** <strong>\*</strong> `newValue` **）;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Void SetAt （void** <strong>\*</strong> `key` **，WORD** `newValue` **）;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Void SetAt （LPCTSTR** `key` **，void** <strong>\*</strong> `newValue` **）;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Void SetAt （LPCTSTR** `key` **，LPCTSTR** `newValue` **）;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Void SetAt （WORD** `key` **，CObject** <strong>\*</strong> `newValue` **）;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Void SetAt （WORD** `key` **，void** <strong>\*</strong> `newValue` **）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的 `CAge` 類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

此程式的結果如下：

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString 類別](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb 類別](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)
