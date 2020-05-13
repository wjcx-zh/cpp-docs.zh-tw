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
ms.openlocfilehash: 6520d1c38701647ae51450b9b9800a7cd2701b7a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754589"
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
|[CmapStringToOb::CmapstringtoOb](#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::取得計數](#getcount)|返回此映射中的元素數。|
|[CMapStringToOb::取得哈希表大小](#gethashtablesize)|確定哈希表中的當前元素數。|
|[CMapStringToOb::獲取NextAssoc](#getnextassoc)|獲取下一個反覆運算元素。|
|[CMapStringToOb::取得大小](#getsize)|返回此映射中的元素數。|
|[CMapStringToOb::取得起始位置](#getstartposition)|返回第一個元素的位置。|
|[CMapStringToOb:哈希基](#hashkey)|計算指定鍵的哈希值。|
|[CMapStringtoOb::InithashTable](#inithashtable)|初始化哈希表。|
|[CMapStringToOb::空](#isempty)|測試空映射條件(無元素)。|
|[CMapStringToOb::尋找](#lookup)|根據空指標鍵查找空指標。 指標值(而不是它指向的實體)用於鍵比較。|
|[CMapStringToOb::尋找鍵](#lookupkey)|返回對與指定鍵值關聯的鍵的引用。|
|[CMapStringToOb::刪除所有](#removeall)|從此映射中刪除所有元素。|
|[CMapStringToOb::刪除鍵](#removekey)|刪除由鍵指定的元素。|
|[CMapStringToOb::Setat](#setat)|將元素插入到地圖中;如果找到匹配的鍵,則替換現有元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::運算子\[\]](#operator_at)|將元素插入到映射中, 運算子取代`SetAt`。|

## <a name="remarks"></a>備註

將對(`CString`元素)插入到地圖中后,可以使用字串或 值作為鍵有效地檢索或刪除對。`CObject*` `CString` -  您還可以反覆運算地圖中的所有元素。

位置類型的變數用於所有地圖變體中的備用條目訪問。 您可以使用「位置」來「記住」條目並遍遍地圖。 您可能認為此反覆運算按鍵值順序;因此,您可以認為此反覆運算按鍵值順序進行。它不是。 檢索的元素的順序不確定。

`CMapStringToOb` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果將地圖儲存到存檔中(使用重載插入**<<**( ) 運算子`Serialize`或使用成員函數,則依次序列化每個元素。

如果需要對地圖中的各個元素(`CString`值`CObject`和 內容)進行診斷轉儲,則必須將轉儲上下文的深度設置為 1 或更大。

刪除`CMapStringToOb`物件或刪除其元素時`CString`, 將刪除`CObject`物件和指標。 `CObject`指標引用的物件不會銷毀。

映射類派生類似於清單派生。 有關特殊用途清單類派生的插圖,請參閱文章[「集合](../../mfc/collections.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CmapStringToOb::CmapstringtoOb

構造空`CString``CObject*`到 映射。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
指定用於擴展映射的記憶體分配粒度。

### <a name="remarks"></a>備註

隨著地圖的增長,記憶體以*nBlockSize*條目的單位分配。

下表顯示了與`CMapStringToOb:: CMapStringToOb`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrPtr(INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapptrToWord(INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringtoptr(INT_PTR** `nBlockSize` **= 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringtoString(INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb(INT_PTR** `nBlockSize` **= 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**地圖WordToptr(INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb::取得計數

確定地圖中的元素數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

此映射中的元素數。

### <a name="remarks"></a>備註

下表顯示了與`CMapStringToOb::GetCount`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR取得計數( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR取得計數( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR取得計數( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR取得計數( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR取得計數( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR取得計數( ) const;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb::取得哈希表大小

確定哈希表中的當前元素數。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>傳回值

返回哈希表中的元素數。

### <a name="remarks"></a>備註

下表顯示了與`CMapStringToOb::GetHashTableSize`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT 獲取哈希表尺寸 ( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::獲取NextAssoc

在*rNext 定位*處檢索地圖元素,然後更新*rNext 定位*以引用地圖中的下一個元素。

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*r 下一個位置*<br/>
指定對前`GetNextAssoc`一個或多個`GetStartPosition`調用返回的定位值的引用。

*rKey*<br/>
指定檢索到的元素(字串)的返回鍵。

*rValue*<br/>
指定檢索到的元素(指標`CObject`)的返回值。 有關此參數的更多,請參閱備註。

### <a name="remarks"></a>備註

此函數對於反覆運算地圖中的所有元素最有用。 請注意,位置序列不一定與鍵值序列相同。

如果檢索到的元素是地圖中的最後一個元素,則*rNext定位*的新值將設置為NULL。

對於*rValue*參數,請確保將物件類型轉換為**\*CObject**,這是編譯器所需的,如下例所示:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

對於基於範本的地圖`GetNextAssoc`,情況並非如此。

下表顯示了與`CMapStringToOb::GetNextAssoc`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**空位 GetNextAssoc (位置&** *rNext位置***, 空\*** *rKey,* **空\*** *rValue)* **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空位 getNextAssoc (位置&** *rNext位置***, 空\*** 的*rKey,* WORD **&** *rValue)* **const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空位 GetNextAssoc (位置&** *rNext位置***, CString&** *rKey,* **空\*** *rValue)* **const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空位 getNextAssoc (位置&** *rNext位置***, CString&** *rKey,* **CString&** *rValue)* **const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空隙 getNextAssoc (位置&** *rNext位置***, WORD&** *rKey,* **CObject\* ** *rValue)* **const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空獲取下一個位置(位置&** *rNext位置***,WORD&** *rKey,***空\*** 隙*rValue)* **const;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程序的結果如下:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb::取得大小

返回地圖元素的數量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

地圖中的項數。

### <a name="remarks"></a>備註

調用此方法以檢索映射中的元素數。

下表顯示了與`CMapStringToOb::GetSize`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR取得大小( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR取得大小( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR取得大小( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR取得大小( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR取得大小( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR取得大小( ) const;**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToOb::取得起始位置

通過返回可以傳遞給`GetNextAssoc`調用的定位值來啟動映射反覆運算。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

指示反覆運算地圖的起始位置的定位值;如果地圖為空,則為 NULL。

### <a name="remarks"></a>備註

反覆運算序列是不可預測的;因此,「地圖中的第一個元素」沒有特殊的意義。

下表顯示了與`CMapStringToOb::GetStartPosition`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**位置抓取起始位置( )**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**位置抓取起始位置( )**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**位置抓取起始位置( )**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**位置抓取起始位置( )**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**位置抓取起始位置( )**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**位置抓取起始位置( )**|

### <a name="example"></a>範例

請參考[CMapStringToOb 範例:取得NextAssoc](#getnextassoc)。

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb:哈希基

計算指定鍵的哈希值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
要計算哈希值的鍵。

### <a name="return-value"></a>傳回值

金鑰的哈希值

### <a name="remarks"></a>備註

下表顯示了與`CMapStringToOb::HashKey`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT 哈希基 ( 空**<strong>\*</strong>`key` **) 康斯特;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT 哈希基 ( 空**<strong>\*</strong>`key` **) 康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT 哈希基 ( LPCTST** `key` **) 同;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT 哈希基 ( LPCTST** `key` **) 同;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**烏因特·哈什基( WORD** `key` **) 康斯特;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**烏因特·哈什基( WORD** `key` **) 康斯特;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringtoOb::InithashTable

初始化哈希表。

```cpp
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>參數

*哈希*<br/>
哈希表中的條目數。

*巴羅克現在*<br/>
如果為 TRUE,則在初始化時分配哈希表;如果為 TRUE,則在初始化時分配哈希錶。否則,將在需要時分配表。

### <a name="remarks"></a>備註

為了獲得最佳性能,哈希表大小應為質數。 為了盡量減少衝突,大小應比最大預期數據集大大約 20%。

下表顯示了與`CMapStringToOb::InitHashTable`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空因他表(UINT,** `hashSize` **BOOL** `bAllocNow` **= TRUE);**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToOb::空

確定地圖是否為空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此地圖不包含任何元素,則非零;否則 0。

### <a name="example"></a>範例

請參閱[刪除所有](#removeall)的範例。

### <a name="remarks"></a>備註

下表顯示了與**CMapStringToOb:: isempty**類似的其他成員函數。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 是空的( ) 康斯特;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::尋找

返回基於`CObject`值的`CString`指標。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別要備份的元素的字串鍵。

*rValue*<br/>
指定從上找元素返回的值。

### <a name="return-value"></a>傳回值

如果找到元素,則非零;否則 0。

### <a name="remarks"></a>備註

`Lookup`使用哈希演演演算法快速搜尋具有`CString`與 (value) 完全符合的鍵的映射元素。

下表顯示了與`CMapStringToOb::LookUp`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 查找(無效**<strong>\*</strong>`key`**\*、無效**`rValue`**) 同流;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 查找(空,WORD** <strong>\*</strong> `key` **&)** `rValue` **同一點;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找(LPCTSTR,**`key`**\*空**`rValue`**) 同;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找(LPCTSTR,CString** `key` **&)** `rValue` **康斯特;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 查找(WORD、** `key` ** \* CObject)** `rValue` **同一點;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 查找(WORD,**`key`**\*空**`rValue`**) 康斯特;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::尋找鍵

返回對與指定鍵值關聯的鍵的引用。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定識別要備份的元素的字串鍵。

*rKey*<br/>
對關聯金鑰的引用。

### <a name="return-value"></a>傳回值

如果找到密鑰,則非零;否則 0。

### <a name="remarks"></a>備註

如果在從地圖中刪除關聯元素后或地圖被銷毀後使用對鍵的引用,則使用引用密鑰不安全。

下表顯示了與`CMapStringToOb:: LookupKey`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查找鍵(LPCTSTR,LPCTSTR** `key` **&)** `rKey` **康斯特;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查找鍵(LPCTSTR,LPCTSTR** `key` **&)** `rKey` **康斯特;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::運算符 |

成員函數的`SetAt`方便替代品。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>傳回值

對指向物件的指標的`CObject`引用;對物件的引用如果地圖為空或*鍵*範圍不範圍,則為 NULL。

### <a name="remarks"></a>備註

因此,它只能在賦值語句(l值)的左側使用。 如果沒有具有指定鍵的地圖元素,則創建新元素。

沒有等效於此運算符的「右側」(r 值),因為在地圖中可能找不到鍵。 使用`Lookup`成員函數進行元素檢索。

下表顯示了與`CMapStringToOb::operator []`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>不\*合法\[的&运算符\**( 不合法</strong>`key`**\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD\[& 運算子 *(無效**<strong>\*</strong>`key`**\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空\*\[&运算符 *(lpctstr** `key` ** \);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString&運算符\[_(lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject&\*運算子\[_(單詞**`key`**\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**無效\*\[&运算符 *(val;**`key`**\)**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程序的結果如下:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb::刪除所有

從此映射中刪除所有元素並銷毀`CString`關鍵物件。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

不會`CObject`銷毀每個鍵引用的物件。 如果不`RemoveAll`確保`CObject`引用的對象被銷毀,則該函數可能會導致記憶體洩漏。

如果地圖已為空,則函數工作正常。

下表顯示了與`CMapStringToOb::RemoveAll`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**不合法刪除所有( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**不合法刪除所有( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**不合法刪除所有( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**不合法刪除所有( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**不合法刪除所有( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**不合法刪除所有( );**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb::刪除鍵

查找與提供的鍵對應的地圖條目;然後,如果找到該鍵,則刪除該條目。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>參數

*key*<br/>
指定用於地圖搜尋的字串。

### <a name="return-value"></a>傳回值

如果發現並成功刪除條目,則非零;否則 0。

### <a name="remarks"></a>備註

如果未在其他地方刪除物件,`CObject`則可能導致記憶體洩漏。

下表顯示了與`CMapStringToOb::RemoveKey`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 刪除鍵(空**<strong>\*</strong>`key`**);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 刪除鍵(空**<strong>\*</strong>`key`**);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 刪除鍵 ( LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 刪除鍵 ( LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 刪除鍵 (WORD);** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 刪除鍵 (WORD);** `key` **);**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程序的結果如下:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToOb::Setat

主要是指在地圖中插入元素。

```cpp
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>參數

*key*<br/>
指定為新元素鍵的字串。

*newValue*<br/>
指定`CObject`作為新元素值的指標。

### <a name="remarks"></a>備註

首先,鍵被抬起來。 如果找到該鍵,則更改相應的值;如果找到該鍵,則更改相應的值。否則將創建新的鍵值元素。

下表顯示了與`CMapStringToOb::SetAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**無效(無效**<strong>\*</strong>`key`**,無效**<strong>\*</strong>`newValue`**);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**空設置(空**<strong>\*</strong>`key`**,WORD);** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**空位(LPCTSTR,** `key`**空**<strong>\*</strong>`newValue`**);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**空集(LPCTSTR,LPCTSTR);** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**空集(WORD,** `key` **Cobject);** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**空集(WORD,** `key`**空**<strong>\*</strong>`newValue`**);**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

此程序的結果如下:

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
