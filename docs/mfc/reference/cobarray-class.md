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
ms.openlocfilehash: b083bf0e82f9d9b928e613f07a71d36147240cd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212367"
---
# <a name="cobarray-class"></a>CObArray 類別

支援 `CObject` 指標的陣列。

## <a name="syntax"></a>語法

```
class CObArray : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CObArray：： CObArray](#cobarray)|為指標構造空陣列 `CObject` 。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CObArray：： Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray：： Append](#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray：： Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray：： Parameters.alternatefilters.elementat](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray：： FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray：： GetAt](#getat)|傳回給定索引的值。|
|[CObArray：： GetCount](#getcount)|取得此陣列中項目的數目。|
|[CObArray：：操作](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CObArray：： GetSize](#getsize)|取得此陣列中項目的數目。|
|[CObArray：： System.array.getupperbound](#getupperbound)|傳回最大的有效索引。|
|[CObArray：： InsertAt](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CObArray：： IsEmpty](#isempty)|判定陣列是否是空的。|
|[CObArray：： RemoveAll](#removeall)|從此陣列移除所有項目。|
|[CObArray：： RemoveAt](#removeat)|移除特定索引處的項目。|
|[CObArray：： SetAt](#setat)|設定給定索引的值；不容許陣列成長。|
|[CObArray：： SetAtGrow](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CObArray：： SetSize](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CObArray：： operator \[\]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

這些物件陣列類似于 C 陣列，但它們可以視需要動態縮小和成長。

陣列索引一律從位置0開始。 您可以決定是否要修正上限，或在您加入超過目前系結的專案時，允許陣列展開。 記憶體會連續配置給上限，即使某些元素是 null 也一樣。

在 Win32 底下，物件的大小 `CObArray` 僅限於可用的記憶體。

如同 C 陣列，已編制索引之元素的存取時間 `CObArray` 是常數，而且與陣列大小無關。

`CObArray`併入 IMPLEMENT_SERIAL 宏，以支援其元素的序列化和傾印。 如果 `CObject` 指標陣列儲存在封存中（不論是使用多載插入運算子或成員函式 `Serialize` ），則每個專案 `CObject` 都會連同其陣列索引一起序列化。

如果您需要陣列中個別元素的傾印 `CObject` ，您必須將物件的深度設定 `CDumpContext` 為1或更大。

當 `CObArray` 物件被刪除，或其元素被移除時，只 `CObject` 會移除指標，而不是它們所參考的物件。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

陣列類別衍生類似于清單衍生。 如需特殊用途清單類別之衍生的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

> [!NOTE]
> 如果您想要序列化陣列，您必須在衍生類別的執行中使用 IMPLEMENT_SERIAL 宏。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray：： Add

將新的專案加入至陣列的結尾，並將陣列增加1。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>參數

*newElement*<br/>
`CObject`要加入至這個陣列的指標。

### <a name="return-value"></a>傳回值

已加入之元素的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)已用於大於1的*nGrowBy*值，則可能會配置額外的記憶體。 不過，上限只會增加1。

下表顯示其他類似的成員函式 `CObArray::Add` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 新增（BYTE** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 新增（DWORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 新增（void）** <strong>\*</strong> `newElement`**);**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 加入（LPCTSTR** `newElement` **）; throw （CMemoryException \* ）;**<br /><br /> **INT_PTR 新增（Const CString&** `newElement` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 新增（UINT** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 新增（WORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程式的結果如下：

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray：： Append

呼叫這個成員函式，將另一個陣列的內容加入至指定陣列的結尾。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要附加至陣列之元素的來源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

陣列必須是相同的類型。

如有必要， `Append` 可能會配置額外的記憶體，以容納附加至陣列的元素。

下表顯示其他類似的成員函式 `CObArray::Append` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR 附加（Const CByteArray&** *src* **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR 附加（Const CDWordArray&** *src* **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR 附加（Const CPtrArray&** *src* **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR 附加（Const CStringArray&** *src* **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR 附加（Const CUIntArray&** *src* **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR 附加（Const CWordArray&** *src* **）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray：： Copy

呼叫這個成員函式，以相同類型的另一個陣列專案來覆寫指定陣列的元素。

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列之元素的來源。

### <a name="remarks"></a>備註

`Copy`不釋放記憶體;不過，如有必要， `Copy` 可能會配置額外的記憶體來容納複製到陣列的元素。

下表顯示其他類似的成員函式 `CObArray::Copy` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Void 複本（Const CByteArray&** *src* **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Void 複本（Const CDWordArray&** *src* **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Void 複本（Const CPtrArray&** *src* **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Void 複本（Const CStringArray&** *src* **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Void 複本（Const CUIntArray&** *src* **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Void 複本（Const CWordArray&** *src* **）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray：： CObArray

構造空的 `CObject` 指標陣列。

```
CObArray();
```

### <a name="remarks"></a>備註

陣列會一次增加一個元素。

下表顯示其他類似的函數 `CObArray::CObArray` 。

|類別|建構函式|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray：： Parameters.alternatefilters.elementat

傳回陣列中項目指標的臨時參考。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

### <a name="return-value"></a>傳回值

指標的參考 `CObject` 。

### <a name="remarks"></a>備註

它是用來實作為陣列的左端指派運算子。 請注意，這是只能用來執行特殊陣列運算子的 advanced 函數。

下表顯示其他類似的成員函式 `CObArray::ElementAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& parameters.alternatefilters.elementat （INT_PTR** `nIndex` **）;**|

### <a name="example"></a>範例

  請參閱[CObArray：： GetSize](#getsize)的範例。

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray：： FreeExtra

釋放陣列成長時所配置的任何額外記憶體。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>備註

此函式不會影響陣列的大小或上限。

下表顯示其他類似的成員函式 `CObArray::FreeExtra` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra （）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra （）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra （）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra （）;**|

### <a name="example"></a>範例

  請參閱[CObArray：：執行](#getdata)程式的範例。

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray：： GetAt

傳回指定索引處的陣列元素。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

### <a name="return-value"></a>傳回值

`CObject`目前位於此索引的指標元素。

### <a name="remarks"></a>備註

> [!NOTE]
> 傳遞負值或大於所傳回之值的值， `GetUpperBound` 會導致失敗的判斷提示。

下表顯示其他類似的成員函式 `CObArray::GetAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt （INT_PTR** `nIndex` **） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt （INT_PTR** `nIndex` **） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*GetAt （INT_PTR** `nIndex` **） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt （INT_PTR** `nIndex` **） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt （INT_PTR** `nIndex` **） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt （INT_PTR** `nIndex` **） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray：： GetCount

傳回陣列元素的數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來抓取陣列中的元素數目。 因為索引是以零為起始，所以大小為1，大於最大的索引。

下表顯示其他類似的成員函式 `CObArray::GetCount` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray：：操作

使用這個成員函式，取得陣列中元素的直接存取權。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>傳回值

指標陣列的指標 `CObject` 。

### <a name="remarks"></a>備註

如果沒有可用的元素，則會傳回 `GetData` null 值。

雖然對陣列元素的直接存取可協助您更快速地工作，但在呼叫時請小心， `GetData` 您所做的任何錯誤都會直接影響陣列的元素。

下表顯示其他類似的成員函式 `CObArray::GetData` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const BYTE 量 \* 值（） const;BYTE \* （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD \* （） const; DWORD \* （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void \* \* （） const; void \* \* （）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString \* （） const;CString \* （）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT \* （） const;UINT \* （）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const 文字 \* （） const;字組 \* （）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray：： GetSize

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

因為索引是以零為起始，所以大小為1，大於最大的索引。

下表顯示其他類似的成員函式 `CObArray::GetSize` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray：： System.array.getupperbound

傳回這個陣列的目前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>傳回值

上限的索引（以零為基底）。

### <a name="remarks"></a>備註

因為陣列索引是以零為基底，所以此函式會傳回小於的值 1 `GetSize` 。

條件 `GetUpperBound( )` =-1 表示陣列未包含任何元素。

下表顯示其他類似的成員函式 `CObArray::GetUpperBound` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR System.array.getupperbound （） const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray：： InsertAt

在指定索引處插入項目 (或其他陣列中的所有項目)。

```cpp
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
可能大於所傳回之值的整數索引 `GetUpperBound` 。

*newElement*<br/>
`CObject`要放在這個陣列中的指標。 允許 Null 值的*newElement* 。

*nCount*<br/>
此元素應該插入的次數（預設為1）。

*nStartIndex*<br/>
可能大於所傳回之值的整數索引 `GetUpperBound` 。

*pNewArray*<br/>
另一個陣列，其中包含要加入至此陣列的元素。

### <a name="remarks"></a>備註

第一個版本會 `InsertAt` 在陣列中的指定索引處插入一個專案（或多個元素複本）。 在此程式中，它會在此索引上轉移現有的專案（藉由遞增索引），並向上移動其上方的所有元素。

第二個版本會從 `CObArray` *nStartIndex*位置開始，插入另一個集合中的所有元素。

`SetAt`相反地，函式會取代一個指定的陣列元素，而不會將任何元素移位。

下表顯示其他類似的成員函式 `CObArray::InsertAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，BYTE** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CByteArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，DWORD** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CDWordArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CPtrArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CStringArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，UINT** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CUIntArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt （INT_PTR** `nIndex` **，WORD** `newElement` **，INT** `nCount` **= 1）;**<br /><br /> **throw （CMemoryException \* ）;**<br /><br /> **void InsertAt （INT_PTR** `nStartIndex` **，CWordArray** <strong>\*</strong> `pNewArray` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程式的結果如下：

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray：： IsEmpty

判定陣列是否是空的。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列是空的，則為非零。否則為0。

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray：： operator []

這些注標運算子是和函式的方便替代 `SetAt` `GetAt` 。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>備註

第一個運算子（針對 not 的陣列呼叫 **`const`** ）可用於指派語句的右邊（右值）或左邊（左值）。 第二個（針對 **`const`** 陣列呼叫）只能用在右邊。

如果注標（在指派語句的左邊或右邊）超出範圍，則為該程式庫的 Debug 版本。

下表顯示其他類似的運算子 `CObArray::operator []` 。

|類別|運算子|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **BYTE 運算子 [] （int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **DWORD 運算子 [] （int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **void \* 運算子 [] （int_ptr** `nindex` ** \) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **CString 運算子 [] （int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **UINT 運算子 [] （int_ptr** `nindex` ** \) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& 運算子 [] （int_ptr** `nindex` ** \) ;**<br /><br /> **WORD operator [] （int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray：： RemoveAll

移除此陣列中的所有指標，但不會實際刪除 `CObject` 物件。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

如果陣列已經是空的，函數仍然可以運作。

函式會 `RemoveAll` 釋放用於指標儲存的所有記憶體。

下表顯示其他類似的成員函式 `CObArray::RemoveAll` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll （）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll （）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll （）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll （）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll （）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray：： RemoveAt

從陣列中的指定索引處開始移除一或多個元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

*nCount*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在進程中，它會向下移動已移除專案上方的所有元素。 它會遞減陣列的上限，但不會釋放記憶體。

如果您嘗試移除超過移除點上方陣列中所包含的更多元素，則會進行程式庫判斷提示的調試版本。

函式 `RemoveAt` `CObject` 會從陣列中移除指標，但不會刪除物件本身。

下表顯示其他類似的成員函式 `CObArray::RemoveAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** `nCount` **= 1）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt （INT_PTR** `nIndex` **，INT_PTR** *nCount* **= 1）;**|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程式的結果如下：

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray：： SetAt

設定指定索引處的陣列元素。

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0，且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

*newElement*<br/>
要插入此陣列中的物件指標。 允許 Null 值。

### <a name="remarks"></a>備註

`SetAt`不會造成陣列成長。 `SetAtGrow`如果您想要陣列自動成長，請使用。

您必須確定您的索引值代表陣列中的有效位置。 如果超出範圍，則為程式庫判斷提示的調試版本。

下表顯示其他類似的成員函式 `CObArray::SetAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt （INT_PTR** `nIndex` **，BYTE** `newElement` **）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，DWORD** `newElement` **）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，UINT** `newElement` **）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt （INT_PTR** `nIndex` **，WORD** `newElement` **）;**|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程式的結果如下：

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray：： SetAtGrow

設定指定索引處的陣列元素。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於0的整數索引。

*newElement*<br/>
要加入至這個陣列的物件指標。 允許 Null 值。

### <a name="remarks"></a>備註

如有必要，陣列會自動成長（也就是會調整上限以容納新的元素）。

下表顯示其他類似的成員函式 `CObArray::SetAtGrow` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，BYTE** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，DWORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，void** <strong>\*</strong> `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，LPCTSTR** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，UINT** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow （INT_PTR** `nIndex` **，WORD** `newElement` **）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程式的結果如下：

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray：： SetSize

建立空白或現有陣列的大小;視需要配置記憶體。

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*nNewSize*<br/>
新的陣列大小（元素數目）。 必須大於或等於 0。

*nGrowBy*<br/>
如果需要增加大小，要配置的元素位置數目下限。

### <a name="remarks"></a>備註

如果新的大小小於舊的大小，則會截斷陣列，並釋放所有未使用的記憶體。 為求效率，請呼叫 `SetSize` 來設定陣列的大小，再加以使用。 這可避免每次加入專案時重新配置和複製陣列的需求。

當陣列正在成長時， *nGrowBy*參數會影響內部記憶體配置。 其使用方式永遠不會影響和所報告的陣列大小 `GetSize` `GetUpperBound` 。

如果陣列的大小已增加，所有新配置的**CObject** <strong>\*</strong> 指標都會設定為 Null。

下表顯示其他類似的成員函式 `CObArray::SetSize` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize （INT_PTR** `nNewSize` **，INT** `nGrowBy` **=-1）;**<br /><br /> **throw （CMemoryException \* ）;**|

### <a name="example"></a>範例

  請參閱[CObArray：：執行](#getdata)程式的範例。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStringArray 類別](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray 類別](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray 類別](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray 類別](../../mfc/reference/cdwordarray-class.md)
