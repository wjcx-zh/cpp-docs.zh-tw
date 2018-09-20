---
title: CMapStringToOb 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d00faec0ac65ded0c8e4ddc9f1ab50796bdecd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396320"
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
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|在此地圖中傳回的項目數。|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|判斷目前的雜湊表中的元素數目。|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|取得逐一查看的下一個項目。|
|[CMapStringToOb::GetSize](#getsize)|在此地圖中傳回的項目數。|
|[CMapStringToOb::GetStartPosition](#getstartposition)|傳回第一個元素的位置。|
|[CMapStringToOb::HashKey](#hashkey)|計算指定的索引鍵的雜湊值。|
|[CMapStringToOb::InitHashTable](#inithashtable)|初始化雜湊表。|
|[CMapStringToOb::IsEmpty](#isempty)|空白對應條件 （沒有項目） 的測試。|
|[CMapStringToOb::Lookup](#lookup)|查閱根據 void 指標的索引鍵的 void 指標。 指標值，而不將它指向，實體用於索引鍵的比較。|
|[CMapStringToOb::LookupKey](#lookupkey)|傳回與指定的索引鍵值相關聯的索引鍵的參考。|
|[CMapStringToOb::RemoveAll](#removeall)|此對應中移除所有項目。|
|[CMapStringToOb::RemoveKey](#removekey)|移除索引鍵所指定的項目。|
|[CMapStringToOb::SetAt](#setat)|項目插入對應中;如果找到相符的索引鍵，會取代現有的項目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::operator [ ]](#operator_at)|將元素插入到 map — 運算子替代`SetAt`。|

## <a name="remarks"></a>備註

一旦您已插入`CString` -  `CObject*`配對 （項目） 到對應，您可以有效率地擷取或刪除使用字串組或`CString`做為索引鍵的值。 您也可以逐一查看對應中的所有項目。

位置類型的變數用於所有對應變化中的替代項目存取。 「 記住 」 項目，並逐一查看 map，您可以使用的位置。 您可能會認為此反覆項目是循序的索引鍵值;不存在。 擷取項目的順序為不定。

`CMapStringToOb` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果對應儲存至封存，不論是使用多載的插入依次序列化每個項目 ( **<<**) 運算子或`Serialize`成員函式。

如果您需要個別的項目在對應中的診斷傾印 (`CString`值和`CObject`內容)，您必須將傾印內容的深度設定為 1 或更大。

當`CMapStringToOb`物件被刪除，或當其項目會遭到移除，`CString`物件和`CObject`會移除指標。 所參考的物件`CObject`指標不會終結。

Map 類別的衍生是類似於清單衍生。 請參閱文章[集合](../../mfc/collections.md)取得的特殊用途清單類別衍生的說明。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb

建構空`CString`-至-`CObject*`對應。

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
指定擴充對應的記憶體配置資料粒度。

### <a name="remarks"></a>備註

隨著對應時，配置記憶體的單位*nBlockSize*項目。

下表顯示其他成員函式，類似於`CMapStringToOb:: CMapStringToOb`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

##  <a name="getcount"></a>  CMapStringToOb::GetCount

決定在對應中項目數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

在此地圖中的項目數目。

### <a name="remarks"></a>備註

下表顯示其他成員函式，類似於`CMapStringToOb::GetCount`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 INT_PTR GetCount （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize

判斷目前的雜湊表中的元素數目。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>傳回值

傳回雜湊表中的項目數目。

### <a name="remarks"></a>備註

下表顯示其他成員函式，類似於`CMapStringToOb::GetHashTableSize`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 UINT GetHashTableSize （)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 UINT GetHashTableSize （)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 UINT GetHashTableSize （)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 UINT GetHashTableSize （)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 UINT GetHashTableSize （)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 UINT GetHashTableSize （)**|

##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc

擷取對應項目，在*rNextPosition*，然後更新*rNextPosition*以指向 map 中的下一個元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*rNextPosition*<br/>
指定前一個位置值的參考`GetNextAssoc`或`GetStartPosition`呼叫。

*rKey*<br/>
指定傳回的索引鍵的擷取的項目 （字串）。

*rValue*<br/>
指定的擷取的項目傳回的值 (`CObject`指標)。 如需有關此參數的詳細資訊，請參閱 < 備註 >。

### <a name="remarks"></a>備註

此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。

如果擷取的項目是在對應中，最後則的新值*rNextPosition*設為 NULL。

針對*rValue*參數，確定您物件的類型轉換成**CObject\*&**，這是編譯器的要求，如下列範例所示：

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

這不是的則為 true`GetNextAssoc`範本為基礎的對應。

下表顯示其他成員函式，類似於`CMapStringToOb::GetNextAssoc`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (位置 &** *rNextPosition* **，void\* &**  *rKey* **，void\* &**  *右值* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (位置 （& s)** *rNextPosition*  **， void\*&** *rKey* **，文字 &** *右值* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (位置 &** *rNextPosition* **，CString &** *rKey* **，void\* &** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (位置 &** *rNextPosition* **，CString &** *rKey* **，CString &** *右值* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (位置 &** *rNextPosition* **，WORD &** *rKey* **，CObject\* &** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (位置 &** *rNextPosition* **，WORD &** *rKey* **，void\* &** *rValue* **) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

此程式的結果如下所示：

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>  CMapStringToOb::GetSize

傳回對應項目數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

在對應中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來擷取在對應中的項目數。

下表顯示其他成員函式，類似於`CMapStringToOb::GetSize`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 INT_PTR GetSize （)**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition

對應的反覆項目一開始會傳回位置的值可以傳遞至`GetNextAssoc`呼叫。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，指出逐一查看對應的開始位置或者，如果 map 是空的則為 NULL。

### <a name="remarks"></a>備註

反覆項目序列不是可預測的因此，「 第一個 map 中的元素 「 必須沒有特殊意義。

下表顯示其他成員函式，類似於`CMapStringToOb::GetStartPosition`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的位置 GetStartPosition （)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的位置 GetStartPosition （)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的位置 GetStartPosition （)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的位置 GetStartPosition （)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的位置 GetStartPosition （)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的位置 GetStartPosition （)**|

### <a name="example"></a>範例

範例，請參閱[CMapStringToOb::GetNextAssoc](#getnextassoc)。

##  <a name="hashkey"></a>  CMapStringToOb::HashKey

計算指定的索引鍵的雜湊值。

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>參數

*key*<br/>
雜湊值會計算索引鍵。

### <a name="return-value"></a>傳回值

索引鍵的雜湊值

### <a name="remarks"></a>備註

下表顯示其他成員函式，類似於`CMapStringToOb::HashKey`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const;**|

##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable

初始化雜湊表。

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>參數

*hashSize*<br/>
雜湊表中的項目數。

*bAllocNow*<br/>
如果為 TRUE，會配置的雜湊表初始化; 時否則需要時，會配置資料表。

### <a name="remarks"></a>備註

為了達到最佳效能，雜湊資料表大小應該是質數。 為了減少衝突，大小應該大約 20%超過最大預期的資料集。

下表顯示其他成員函式，類似於`CMapStringToOb::InitHashTable`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **，BOOL** `bAllocNow` **= TRUE);**|

##  <a name="isempty"></a>  CMapStringToOb::IsEmpty

決定是否是空的對應。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

此對應會不包含任何項目; 如果為非零否則為 0。

### <a name="example"></a>範例

範例，請參閱[RemoveAll](#removeall)。

### <a name="remarks"></a>備註

下表顯示其他成員函式，類似於**CMapStringToOb:: IsEmpty**。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Const; 的 BOOL IsEmpty （)**|

##  <a name="lookup"></a>  CMapStringToOb::Lookup

傳回`CObject`指標根據`CString`值。

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定字串索引鍵，識別要查閱的項目。

*rValue*<br/>
指定查閱項目傳回的值。

### <a name="return-value"></a>傳回值

非零值，如果找不到項目;否則為 0。

### <a name="remarks"></a>備註

`Lookup` 使用快速尋找地圖元素，會確實比對的索引鍵的雜湊演算法 (`CString`值)。

下表顯示其他成員函式，類似於`CMapStringToOb::LookUp`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL 查閱 (void** <strong>\*</strong> `key` **，void\* &**  `rValue` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL 查閱 (void** <strong>\*</strong> `key` **，WORD &** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL 查閱 (LPCTSTR** `key` **，void\* &**  `rValue` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL 查閱 (LPCTSTR** `key` **，CString &** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL 查閱 (WORD** `key` **，CObject\* &**  `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL 查閱 (WORD** `key` **，void\* &**  `rValue` **) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey

傳回與指定的索引鍵值相關聯的索引鍵的參考。

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>參數

*key*<br/>
指定字串索引鍵，識別要查閱的項目。

*rKey*<br/>
相關聯的索引鍵參考。

### <a name="return-value"></a>傳回值

非零值，如果找不到索引鍵;否則為 0。

### <a name="remarks"></a>備註

如果使用從對應移除相關聯的項目之後，或對應已終結後，使用索引鍵的參考並不安全的。

下表顯示其他成員函式，類似於`CMapStringToOb:: LookupKey`。

|類別|成員函式|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR &** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **，LPCTSTR &** `rKey` **) const;**|

##  <a name="operator_at"></a>  CMapStringToOb::operator]

方便替代`SetAt`成員函式。

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>傳回值

指標的參考`CObject`物件，或是如果 map 是空的則為 NULL 或*金鑰*超出範圍。

### <a name="remarks"></a>備註

因此可以使用只在指派陳述式 （左值） 的左側。 如果沒有附指定索引鍵的對應項目，則會建立新的項目。

任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。

下表顯示其他成員函式，類似於`CMapStringToOb::operator []`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& 運算子\[] (void \*</strong>  `key`  **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & 運算子\[] (void** <strong>\*</strong> `key`  **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& 運算子\[] (lpctstr** `key`  **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & 運算子\[] (lpctstr** `key`  **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& 運算子\[] (word** `key`  **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& 運算子\[] (word** `key`  **\);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

此程式的結果如下所示：

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>  CMapStringToOb::RemoveAll

此對應中移除所有項目，並終結`CString`金鑰物件。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

`CObject`每個索引鍵所參考的物件不會終結。 `RemoveAll`函式會導致記憶體流失，如果您不會確定所參考之`CObject`會終結物件。

如果 map 已經是空白，則函式會運作正常。

下表顯示其他成員函式，類似於`CMapStringToOb::RemoveAll`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll （);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll （);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll （);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll （);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll （);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>  CMapStringToOb::RemoveKey

查閱對應到所提供的索引鍵; 的對應項目然後，如果找到索引鍵，則移除的項目。

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>參數

*key*<br/>
指定用於對應查閱的字串。

### <a name="return-value"></a>傳回值

如果找到並成功移除項目，非零值。否則為 0。

### <a name="remarks"></a>備註

如果，這可能會造成記憶體流失`CObject`物件不會刪除其他位置。

下表顯示其他成員函式，類似於`CMapStringToOb::RemoveKey`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

此程式的結果如下所示：

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>  CMapStringToOb::SetAt

若要將項目插入對應中，主要表示。

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>參數

*key*<br/>
指定新項目的索引鍵的字串。

*newValue*<br/>
指定`CObject`是新的項目值的指標。

### <a name="remarks"></a>備註

首先，索引鍵查閱。 如果找到索引鍵，則會變更對應的值;否則，系統會建立新的索引鍵 / 值項目。

下表顯示其他成員函式，類似於`CMapStringToOb::SetAt`。

|類別|成員函式|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **，void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **，WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **，void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (LPCTSTR** `key` **，LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **，CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **，void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

此程式的結果如下所示：

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
