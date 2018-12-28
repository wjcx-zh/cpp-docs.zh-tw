---
title: CObArray 類別
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: 031f163a5a4b5663b296dc6615712fe7dd5dbc56
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657600"
---
# <a name="cobarray-class"></a>CObArray 類別

支援 `CObject` 指標的陣列。

## <a name="syntax"></a>語法

```
class CObArray : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|建構空的陣列`CObject`指標。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObArray::Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray::Append](#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray::Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray::ElementAt](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray::FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray::GetAt](#getat)|傳回給定索引的值。|
|[CObArray::GetCount](#getcount)|取得此陣列中項目的數目。|
|[CObArray::GetData](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CObArray::GetSize](#getsize)|取得此陣列中項目的數目。|
|[CObArray::GetUpperBound](#getupperbound)|傳回最大的有效索引。|
|[CObArray::InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CObArray::IsEmpty](#isempty)|判定陣列是否是空的。|
|[CObArray::RemoveAll](#removeall)|從此陣列移除所有項目。|
|[CObArray::RemoveAt](#removeat)|移除特定索引處的項目。|
|[CObArray::SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CObArray::SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CObArray::SetSize](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CObArray::operator \[ \]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

這些物件的陣列會類似 C 陣列，但是它們可以動態壓縮，並需要增大。

陣列索引一律從開始位置 0。 您可以決定是否要修正的上限，或允許展開，當您新增超過目前的繫結的項目陣列。 記憶體配置，連續的上限，即使某些項目都是 null。

在 Win32 中，大小`CObArray`物件只限於可用記憶體。

如同 C 陣列，存取時間`CObArray`索引的項目為常數，而且是獨立的陣列大小。

`CObArray` 納入 IMPLEMENT_SERIAL 巨集，以支援序列化和傾印其項目。 如果陣列`CObject`指標會儲存至封存，或是利用多載的插入運算子`Serialize`成員函式，每個`CObject`序列化項目，接著，以及其陣列索引。

如果您需要個別的傾印`CObject`陣列中的項目，您必須設定的深度`CDumpContext`為 1 或更高的物件。

當`CObArray`物件被刪除，或當其項目會遭到移除，只有`CObject`會移除指標，它們會參考不是物件。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

陣列類別衍生是類似於清單衍生。 如需特殊用途清單類別衍生的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

> [!NOTE]
>  如果您想要序列化的陣列，您必須在衍生類別的實作中使用 IMPLEMENT_SERIAL 巨集。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

##  <a name="add"></a>  CObArray::Add

加入新元素的陣列，陣列成長 1 結尾。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>參數

*newElement*<br/>
`CObject`可以加入至這個陣列的指標。

### <a name="return-value"></a>傳回值

加入之項目的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)已*nGrowBy*可能配置大於 1，則額外的記憶體值。 不過，只有 1 將增加上限。

下表顯示其他成員函式，類似於`CObArray::Add`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 新增 (位元組** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 新增 (DWORD** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 新增 (void** <strong>\*</strong> `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 新增 (LPCTSTR** `newElement` **)，會擲回 (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 新增 (UINT** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 新增 (WORD** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程式的結果如下所示：

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

##  <a name="append"></a>  CObArray::Append

呼叫此成員函式，將另一個陣列的內容新增至指定陣列的結尾。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要附加至陣列項目的來源。

### <a name="return-value"></a>傳回值

第一個附加的項目索引。

### <a name="remarks"></a>備註

陣列必須是相同的型別。

如有必要，`Append`可能會配置額外的記憶體來容納附加至陣列的項目。

下表顯示其他成員函式，類似於`CObArray::Append`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 附加 (const CByteArray &** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 附加 (const CDWordArray &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 附加 (const CPtrArray &** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 附加 (const CStringArray &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 附加 (const CUIntArray &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 附加 (const CWordArray &** *src* **);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

##  <a name="copy"></a>  CObArray::Copy

呼叫此成員函式，以覆寫相同類型的另一個陣列的項目與指定的陣列項目。

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列之項目的來源。

### <a name="remarks"></a>備註

`Copy` 不會釋放記憶體;不過，如果有必要，`Copy`可能會配置額外的記憶體來容納的項目複製到陣列。

下表顯示其他成員函式，類似於`CObArray::Copy`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void 複製 (const CByteArray &** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void 複製 (const CDWordArray &** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void 複製 (const CPtrArray &** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void 複製 (const CStringArray &** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void 複製 (const CUIntArray &** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void 複製 (const CWordArray &** *src* **);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

##  <a name="cobarray"></a>  CObArray::CObArray

建構空`CObject`指標陣列。

```
CObArray();
```

### <a name="remarks"></a>備註

陣列會增加一個項目，一次。

下表顯示類似於其他建構函式`CObArray::CObArray`。

|類別|建構函式|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray （);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray （);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray （);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray （);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray （);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray （);**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

##  <a name="elementat"></a>  CObArray::ElementAt

傳回陣列中項目指標的臨時參考。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`GetUpperBound`。

### <a name="return-value"></a>傳回值

參考`CObject`指標。

### <a name="remarks"></a>備註

它用來實作陣列的左邊的指派運算子。 請注意，這是進階的功能，應該只能用來實作特殊陣列運算子。

下表顯示其他成員函式，類似於`CObArray::ElementAt`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**位元組 & ElementAt (INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & ElementAt (INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD 與 ElementAt (INT_PTR** `nIndex` **);**|

### <a name="example"></a>範例

  範例，請參閱[CObArray::GetSize](#getsize)。

##  <a name="freeextra"></a>  CObArray::FreeExtra

釋放任何額外的記憶體配置時已成長的陣列。

```
void FreeExtra();
```

### <a name="remarks"></a>備註

此函式無效的大小或陣列的上限。

下表顯示其他成員函式，類似於`CObArray::FreeExtra`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra （);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra （);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra （);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra （);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra （);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra （);**|

### <a name="example"></a>範例

  範例，請參閱[CObArray::GetData](#getdata)。

##  <a name="getat"></a>  CObArray::GetAt

傳回指定索引處的陣列元素。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`GetUpperBound`。

### <a name="return-value"></a>傳回值

`CObject`指標目前在這個索引處的項目。

### <a name="remarks"></a>備註

> [!NOTE]
>  傳遞負數的值所傳回的值大於`GetUpperBound`會導致失敗的判斷提示。

下表顯示其他成員函式，類似於`CObArray::GetAt`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**位元組 GetAt (INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

##  <a name="getcount"></a>  CObArray::GetCount

傳回陣列元素數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來擷取陣列中的項目數。 因為是以零起始的索引，大小為 1 大於最大的索引。

下表顯示其他成員函式，類似於`CObArray::GetCount`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; 的 INT_PTR GetCount （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

##  <a name="getdata"></a>  CObArray::GetData

您可以使用此成員函式來直接存取陣列中的項目。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>傳回值

陣列指標`CObject`指標。

### <a name="remarks"></a>備註

如果沒有項目可供使用，`GetData`傳回 null 值。

而直接存取陣列的項目可協助您更快速地運作，請呼叫時使用注意`GetData`; 您直接提出任何錯誤會影響您陣列的元素。

下表顯示其他成員函式，類似於`CObArray::GetData`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const 位元組\*const; GetData （)位元組\*GetData （);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData （） 的常數; DWORD\* GetData （);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void\* \* GetData （) const; void\* \* GetData （);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* const; GetData （)CString\* GetData （);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* const; GetData （)UINT\* GetData （);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const WORD\* const; GetData （)WORD\* GetData （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

##  <a name="getsize"></a>  CObArray::GetSize

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

因為是以零起始的索引，大小為 1 大於最大的索引。

下表顯示其他成員函式，類似於`CObArray::GetSize`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; 的 INT_PTR GetSize （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

##  <a name="getupperbound"></a>  CObArray::GetUpperBound

傳回目前的上限，此陣列。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>傳回值

上限 （以零為起始） 索引。

### <a name="remarks"></a>備註

因為是以零為起始的陣列索引，此函數會傳回 1 的值小於`GetSize`。

條件`GetUpperBound( )`=-1 表示陣列是否包含任何項目。

下表顯示其他成員函式，類似於`CObArray::GetUpperBound`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const; 的 INT_PTR GetUpperBound （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

##  <a name="insertat"></a>  CObArray::InsertAt

在指定索引處插入項目 (或其他陣列中的所有項目)。

```
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
可能會大於所傳回的值的整數索引`GetUpperBound`。

*newElement*<br/>
`CObject`放在這個陣列的指標。 A *newElement*允許 NULL 的值。

*nCount*<br/>
次數，此項目應該插入 （預設值為 1）。

*nStartIndex*<br/>
可能會大於所傳回的值的整數索引`GetUpperBound`。

*pNewArray*<br/>
另一個陣列，包含要加入至這個陣列的項目。

### <a name="remarks"></a>備註

第一版`InsertAt`陣列中指定索引處插入一個項目 （或多個項目複本）。 在過程中，它會往上移動這個索引，並在現有的項目移位其上方的所有項目 （依遞增的索引）。

第二個版本會將所有項目插入從另一個`CObArray`集合，從開始*nStartIndex*位置。

`SetAt`函式，相較之下，取代一個指定的陣列項目，並不會不位移任何項目。

下表顯示其他成員函式，類似於`CObArray::InsertAt`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，位元組** `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，DWORD** `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，UINT** `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **，WORD** `newElement` **，int** `nCount` **= 1);**<br /><br /> **擲回 (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **，CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **擲回 (CMemoryException\* );**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程式的結果如下所示：

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

##  <a name="isempty"></a>  CObArray::IsEmpty

判定陣列是否是空的。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列是空的則為非零否則為 0。

##  <a name="operator_at"></a>  CObArray::operator]

這些註標運算子會很方便的替代`SetAt`和`GetAt`函式。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>備註

陣列未呼叫的第一個運算子**const**，可用於上的權限 （右值） 或指派陳述式左邊 （左值）。 第二個，呼叫**const**陣列可能只能用在右邊。

偵錯版本的程式庫判斷提示的註標 （請在左邊或右邊則在指派陳述式） 是否超出範圍。

下表顯示類似於其他運算子`CObArray::operator []`。

|類別|運算子|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**位元組 & 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **運算子 byte (int_ptr** `nindex`  **\) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **DWORD 運算子 [] (int_ptr** `nindex`  **\) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **void\* operator [] (int_ptr** `nindex`  **\) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString & 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **CString operator [] (int_ptr** `nindex`  **\) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **UINT operator [] (int_ptr** `nindex`  **\) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & 運算子 [] (int_ptr** `nindex`  **\);**<br /><br /> **WORD operator [] (int_ptr** `nindex`  **\) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

##  <a name="removeall"></a>  CObArray::RemoveAll

從這個陣列中移除所有的指標，但不會實際刪除`CObject`物件。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果已經為空陣列，此函式仍能運作。

`RemoveAll`函式會釋放所有記憶體的指標儲存區使用。

下表顯示其他成員函式，類似於`CObArray::RemoveAll`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll （);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll （);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll （);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll （);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll （);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

##  <a name="removeat"></a>  CObArray::RemoveAt

移除陣列中的指定索引處開始的一或多個項目。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`GetUpperBound`。

*nCount*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在過程中，它會進入關閉已移除的項目上方的所有項目。 它遞減右上角的陣列繫結，但不會釋放記憶體。

如果您嘗試移除比上述移除點陣列中包含的項目，然後判斷提示的程式庫的偵錯版本。

`RemoveAt`函式移除`CObject`指標陣列，但它並不會刪除物件本身。

下表顯示其他成員函式，類似於`CObArray::RemoveAt`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **，INT_PTR** *nCount* **= 1);**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程式的結果如下所示：

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

##  <a name="setat"></a>  CObArray::SetAt

設定指定索引處的陣列項目。

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
一個整數的索引大於或等於 0 且小於或等於所傳回的值`GetUpperBound`。

*newElement*<br/>
要插入此陣列中的物件指標。 允許 NULL 值。

### <a name="remarks"></a>備註

`SetAt` 不會造成要成長的陣列。 使用`SetAtGrow`如果您想要自動成長的陣列。

您必須確定您的索引值代表陣列中的有效位置。 如果它超出範圍時，偵錯版本的程式庫判斷提示。

下表顯示其他成員函式，類似於`CObArray::SetAt`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **，位元組** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **，WORD** `newElement` **);**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程式的結果如下所示：

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

##  <a name="setatgrow"></a>  CObArray::SetAtGrow

設定指定索引處的陣列項目。

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*newElement*<br/>
要加入至這個陣列的物件指標。 允許 NULL 值。

### <a name="remarks"></a>備註

陣列在必要時自動成長 （亦即，以容納新的項目調整上限）。

下表顯示其他成員函式，類似於`CObArray::SetAtGrow`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，位元組** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，DWORD** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，LPCTSTR** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，UINT** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **，WORD** `newElement` **);**<br /><br /> **擲回 (CMemoryException\* );**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)如需清單`CAge`集合的所有範例中所使用的類別。

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程式的結果如下所示：

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

##  <a name="setsize"></a>  CObArray::SetSize

建立空的或現有陣列; 的大小如有必要，請配置記憶體。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*nNewSize*<br/>
新陣列的大小 （數字的項目）。 必須是大於或等於 0。

*nGrowBy*<br/>
如果是必要的大小增加配置的項目位置的數目下限。

### <a name="remarks"></a>備註

如果新的大小小於舊的大小，然後陣列會被截斷，並釋放所有未使用的記憶體。 為了提高效率，呼叫`SetSize`使用它之前，請先設定陣列的大小。 這可避免需要重新配置和複製陣列每個項目加入的時間。

*NGrowBy*參數會影響內部記憶體配置，而陣列成長。 其用途並不會影響陣列大小所回報`GetSize`和`GetUpperBound`。

如果陣列的大小成長，所有新配置**CObject** <strong>\*</strong>指標都會設定為 NULL。

下表顯示其他成員函式，類似於`CObArray::SetSize`。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **，int** `nGrowBy` **=-1);**<br /><br /> **擲回 (CMemoryException\* );**|

### <a name="example"></a>範例

  範例，請參閱[CObArray::GetData](#getdata)。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStringArray 類別](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray 類別](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray 類別](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray 類別](../../mfc/reference/cdwordarray-class.md)
