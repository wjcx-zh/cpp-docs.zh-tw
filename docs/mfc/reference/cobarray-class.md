---
title: CObArray 類別
description: 將 `CObArray` `MFC` 指標儲存在陣列中之類別的 API 參考 `CObject` 。
ms.date: 08/27/2020
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
ms.openlocfilehash: cbc1799a9634b3d8c09077b755b8a097289460fd
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062142"
---
# <a name="cobarray-class"></a>CObArray 類別

支援 `CObject` 指標的陣列。

## <a name="syntax"></a>Syntax

```cpp
class CObArray : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObArray：： CObArray](#cobarray)|為指標建立空的陣列 `CObject` 。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObArray：： Add](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray：： Append](#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray：： Copy](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray：： Parameters.alternatefilters.elementat](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray：： FreeExtra](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray：： GetAt](#getat)|傳回給定索引的值。|
|[CObArray：： GetCount](#getcount)|取得此陣列中項目的數目。|
|[CObArray：：：：的](#getdata)|容許存取陣列中的項目。 可以是 `NULL`。|
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

|名稱|描述|
|----------|-----------------|
|[CObArray：： operator \[\]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

這些物件陣列與 C 陣列相似，但可以視需要動態壓縮和成長。

陣列索引一律在位置0開始。 您可以決定是否要修正上限，或在您新增超過目前系結的專案時，允許陣列展開。 記憶體會連續配置至上限，即使某些元素為 `NULL` 。

在 Win32 下，物件的大小 `CObArray` 只受限於可用的記憶體。

如同 C 陣列，索引項目的存取時間 `CObArray` 是常數，而且與陣列大小無關。

`CObArray` 併入 IMPLEMENT_SERIAL 宏，以支援其元素的序列化和傾印。 如果指標的陣列 `CObject` 儲存在封存中（使用多載插入運算子或成員函式 `Serialize` ），則每個專案 `CObject` 都會接著序列化，以及其陣列索引。

如果您需要 `CObject` 在陣列中的個別元素傾印，則必須將物件的深度設定 `CDumpContext` 為1或更大。

當 `CObArray` 物件被刪除，或移除其專案時，只 `CObject` 會移除指標，而不會移除它們所參考的物件。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

陣列類別衍生類似于清單衍生。 如需特殊用途清單類別之衍生的詳細資訊，請參閱文章 [集合](../../mfc/collections.md)。

> [!NOTE]
> 如果您想要序列化陣列，您必須在衍生類別的執行中使用 IMPLEMENT_SERIAL 宏。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>規格需求

**標頭：** afxcoll。h

## <a name="cobarrayadd"></a><a name="add"></a> CObArray：： Add

將新的專案加入至陣列的結尾，並將陣列增加1。

```cpp
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>參數

*newElement*\
`CObject`要加入至這個陣列的指標。

### <a name="return-value"></a>傳回值

已加入專案的索引。

### <a name="remarks"></a>備註

如果 [SetSize](#setsize) 使用的 *nGrowBy* 值大於1，則可能會配置額外的記憶體。 不過，上限只會增加1。

下表顯示其他類似的成員函式 `CObArray::Add` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Add(BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Add(DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Add(void* newElement);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Add(LPCTSTR newElement); throw(CMemoryException*);`<br /><br />`INT_PTR Add(const CString& newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Add(UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Add(WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程式的結果如下所示：

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a> CObArray：： Append

呼叫這個成員函式，將另一個陣列的內容加入至指定陣列的結尾。

```cpp
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>參數

*Src*\
要附加至陣列的元素來源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

陣列必須是相同的類型。

如有必要， `Append` 可能會配置額外的記憶體來容納附加至陣列的元素。

下表顯示其他類似的成員函式 `CObArray::Append` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR Append(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR Append(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR Append(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR Append(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR Append(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR Append(const CWordArray& src);`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a> CObArray：： Copy

呼叫這個成員函式，以相同型別的另一個陣列的元素，覆寫指定陣列的專案。

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>參數

*Src*\
要複製到陣列的元素來源。

### <a name="remarks"></a>備註

`Copy` 不會釋放記憶體。 如有必要， `Copy` 可能會配置額外的記憶體來容納複製到陣列的元素。

下表顯示其他類似的成員函式 `CObArray::Copy` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void Copy(const CByteArray& src);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void Copy(const CDWordArray& src);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void Copy(const CPtrArray& src);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void Copy(const CStringArray& src);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void Copy(const CUIntArray& src);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void Copy(const CWordArray& src);`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a> CObArray：： CObArray

結構空白 `CObject` 指標陣列。

```cpp
CObArray();
```

### <a name="remarks"></a>備註

陣列會一次增加一個元素。

下表顯示其他類似的函數 `CObArray::CObArray` 。

|類別|建構函式|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`CByteArray();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`CDWordArray();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`CPtrArray();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CStringArray();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`CUIntArray();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`CWordArray();`|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a> CObArray：： Parameters.alternatefilters.elementat

傳回陣列中項目指標的臨時參考。

```cpp
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*nIndex*\
大於或等於0且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

### <a name="return-value"></a>傳回值

指標的參考 `CObject` 。

### <a name="remarks"></a>備註

它是用來針對陣列執行左方指派運算子。 這是只能用來執行特殊陣列運算子的 advanced 函數。

下表顯示其他類似的成員函式 `CObArray::ElementAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& ElementAt(INT_PTR nIndex);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& ElementAt(INT_PTR nIndex);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& ElementAt(INT_PTR nIndex);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& ElementAt(INT_PTR nIndex);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& ElementAt(INT_PTR nIndex);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& ElementAt(INT_PTR nIndex);`|

### <a name="example"></a>範例

請參閱 [CObArray：： GetSize](#getsize)的範例。

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a> CObArray：： FreeExtra

釋放陣列成長時配置的任何額外記憶體。

```cpp
void FreeExtra();
```

### <a name="remarks"></a>備註

此函數不會影響陣列的大小或上限。

下表顯示其他類似的成員函式 `CObArray::FreeExtra` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void FreeExtra();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void FreeExtra();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void FreeExtra();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void FreeExtra();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void FreeExtra();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void FreeExtra();`|

### <a name="example"></a>範例

  請參閱 [CObArray：：](#getdata)的範例。

## <a name="cobarraygetat"></a><a name="getat"></a> CObArray：： GetAt

傳回指定索引處的陣列元素。

```cpp
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*\
大於或等於0且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

### <a name="return-value"></a>傳回值

`CObject`目前位於此索引的指標元素。

### <a name="remarks"></a>備註

> [!NOTE]
> 傳遞負數值或大於所傳回值的值， `GetUpperBound` 將會產生失敗的判斷提示。

下表顯示其他類似的成員函式 `CObArray::GetAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE GetAt(INT_PTR nIndex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD GetAt(INT_PTR nIndex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void* GetAt(INT_PTR nIndex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString GetAt(INT_PTR nIndex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT GetAt(INT_PTR nIndex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD GetAt(INT_PTR nIndex) const;`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a> CObArray：： GetCount

傳回陣列元素的數目。

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法，以抓取陣列中的元素數目。 因為索引是以零為基底，所以大小是大於最大索引的1。

下表顯示其他類似的成員函式 `CObArray::GetCount` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetCount() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetCount() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetCount() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetCount() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetCount() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetCount() const;`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a> CObArray：：：：的

您可以使用這個成員函式，直接存取陣列中的元素。

```cpp
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>傳回值

指標陣列的指標 `CObject` 。

### <a name="remarks"></a>備註

如果沒有可用的元素，會傳回 `GetData` `NULL` 值。

雖然直接存取陣列的專案可協助您更快速地工作，但是在呼叫時請務必小心 `GetData` ; 您直接進行的任何錯誤都會影響陣列的元素。

下表顯示其他類似的成員函式 `CObArray::GetData` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`const BYTE* GetData() const; BYTE* GetData();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`const DWORD* GetData() const; DWORD* GetData();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`const void** GetData() const; void** GetData();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`const CString* GetData() const; CString* GetData();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`const UINT* GetData() const; UINT* GetData();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`const WORD* GetData() const; WORD* GetData();`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a> CObArray：： GetSize

傳回陣列的大小。

```cpp
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

因為索引是以零為基底，所以大小是大於最大索引的1。

下表顯示其他類似的成員函式 `CObArray::GetSize` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetSize() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetSize() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetSize() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetSize() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetSize() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetSize() const;`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a> CObArray：： System.array.getupperbound

傳回這個陣列的目前上限。

```cpp
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>傳回值

以零為基底之) 的上限 (索引。

### <a name="remarks"></a>備註

因為陣列索引是以零為基底，此函數會傳回小於的值 1 `GetSize` 。

條件 `GetUpperBound() = -1` 指出陣列未包含任何元素。

下表顯示其他類似的成員函式 `CObArray::GetUpperBound` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`INT_PTR GetUpperBound() const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`INT_PTR GetUpperBound() const;`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a> CObArray：： InsertAt

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

*nIndex*\
可能大於所傳回之值的整數索引 `GetUpperBound` 。

*newElement*\
`CObject`要放置在此陣列中的指標。 允許*newElement*值的 newElement `NULL` 。

*nCount*\
此元素的插入次數 (預設為 1) 。

*nStartIndex*\
可能大於所傳回之值的整數索引 `GetUpperBound` 。

*pNewArray*\
另一個陣列，其中包含要加入至這個陣列的元素。

### <a name="remarks"></a>備註

第一個版本會在 `InsertAt` 陣列中的指定索引處插入一個元素 (或多個專案複本) 。 在此程式中，它會將索引) 現有元素的索引遞增，以向上移動 (，並將其上方的所有元素向上移動。

第二個版本會從 `CObArray` *nStartIndex* 位置開始插入另一個集合中的所有元素。

`SetAt`相反地，函式會取代一個指定的陣列元素，且不會轉移任何專案。

下表顯示其他類似的成員函式 `CObArray::InsertAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void InsertAt(INT_PTR nIndex, BYTE newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CByteArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void InsertAt(INT_PTR nIndex, DWORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CDWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void InsertAt(INT_PTR nIndex, void* newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CPtrArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void InsertAt(INT_PTR nIndex, LPCTSTR newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CStringArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void InsertAt(INT_PTR nIndex, UINT newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CUIntArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void InsertAt(INT_PTR nIndex, WORD newElement, int nCount = 1);`<br /><br />`throw(CMemoryException*);`<br /><br />`void InsertAt(INT_PTR nStartIndex, CWordArray* pNewArray);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程式的結果如下所示：

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a> CObArray：： IsEmpty

判定陣列是否是空的。

```cpp
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列是空的，則為非零;否則為0。

## <a name="cobarrayoperator--"></a><a name="operator_at"></a> CObArray：： operator []

這些注標運算子是和函數的方便 `SetAt` 替代 `GetAt` 。

```cpp
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>備註

第一個運算子（針對不是的陣列） **`const`** 可用於右邊的 (r--值) 或左邊 (左值) 指派語句。 第二個（針對 **`const`** 陣列呼叫）只能用在右邊。

如果在指派) 語句的左側或右側 (的注標是否超出範圍，就會判斷提示程式庫的偵錯工具版本。

下表顯示與類似的其他運算子 `CObArray::operator []` 。

|類別|運算子|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`BYTE& operator [](INT_PTR nindex);`<br /><br />`BYTE operator [](INT_PTR nindex) const;`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`DWORD& operator [](INT_PTR nindex);`<br /><br />`DWORD operator [](INT_PTR nindex) const;`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void*& operator [](INT_PTR nindex);`<br /><br />`void* operator [](INT_PTR nindex) const;`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`CString& operator [](INT_PTR nindex);`<br /><br />`CString operator [](INT_PTR nindex) const;`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`UINT& operator [](INT_PTR nindex);`<br /><br />`UINT operator [](INT_PTR nindex) const;`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`WORD& operator [](INT_PTR nindex);`<br /><br />`WORD operator [](INT_PTR nindex) const;`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a> CObArray：： RemoveAll

移除這個陣列中的所有指標，但不會實際刪除 `CObject` 物件。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

如果陣列已經是空的，函數仍可運作。

`RemoveAll`函數會釋出用於指標儲存的所有記憶體。

下表顯示其他類似的成員函式 `CObArray::RemoveAll` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAll();`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAll();`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAll();`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAll();`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAll();`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAll();`|

### <a name="example"></a>範例

如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a> CObArray：： RemoveAt

從陣列中的指定索引處移除一或多個元素。

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*\
大於或等於0且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

*nCount*\
要移除的項目數目。

### <a name="remarks"></a>備註

在此程式中，它會將已移除元素上方的所有專案往下移 (s) 。 它會遞減陣列的上限，但不會釋放記憶體。

如果您嘗試移除的專案數目超過移除點上方的陣列中所包含的專案，就會是程式庫的偵錯工具判斷提示。

函式 `RemoveAt` `CObject` 會從陣列中移除指標，但不會刪除物件本身。

下表顯示其他類似的成員函式 `CObArray::RemoveAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void RemoveAt(INT_PTR nIndex, INT_PTR nCount = 1);`|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程式的結果如下所示：

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a> CObArray：： SetAt

設定位於指定索引位置的陣列元素。

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*\
大於或等於0且小於或等於所傳回之值的整數索引 `GetUpperBound` 。

*newElement*\
要插入此陣列中的物件指標。 `NULL`允許值。

### <a name="remarks"></a>備註

`SetAt` 不會導致陣列成長。 `SetAtGrow`如果您希望陣列自動成長，請使用。

確定您的索引值代表陣列中的有效位置。 如果超出範圍，則為程式庫判斷提示的偵錯工具版本。

下表顯示其他類似的成員函式 `CObArray::SetAt` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAt(INT_PTR nIndex, BYTE newElement);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAt(INT_PTR nIndex, DWORD newElement);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAt(INT_PTR nIndex, void* newElement);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAt(INT_PTR nIndex, LPCTSTR newElement);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAt(INT_PTR nIndex, UINT newElement);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAt(INT_PTR nIndex, WORD newElement);`|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程式的結果如下所示：

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a> CObArray：： SetAtGrow

設定位於指定索引位置的陣列元素。

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*\
大於或等於0的整數索引。

*newElement*\
要加入至這個陣列的物件指標。 `NULL`允許值。

### <a name="remarks"></a>備註

如有必要，此陣列會自動成長 (也就是調整上限以容納新元素) 。

下表顯示其他類似的成員函式 `CObArray::SetAtGrow` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetAtGrow(INT_PTR nIndex, BYTE newElement);`<br /><br />`throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, DWORD newElement);`<br /><br />`throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetAtGrow(INT_PTR nIndex, void* newElement);`<br /><br />`throw( CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetAtGrow(INT_PTR nIndex, LPCTSTR newElement);`<br /><br />`throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetAtGrow(INT_PTR nIndex, UINT newElement);`<br /><br />`throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetAtGrow(INT_PTR nIndex, WORD newElement);`<br /><br />`throw(CMemoryException*);`|

### <a name="example"></a>範例

  如需所有集合範例中使用的類別清單，請參閱 [CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` 。

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程式的結果如下所示：

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a> CObArray：： SetSize

建立空的或現有陣列的大小;視需要配置記憶體。

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*nNewSize*\
新陣列大小 () 的元素數目。 必須大於或等於 0。

*nGrowBy*\
需要增加大小時要配置的元素位置數目下限。

### <a name="remarks"></a>備註

如果新的大小小於舊的大小，則會截斷陣列，並釋放所有未使用的記憶體。 為了提高效率，請 `SetSize` 先呼叫來設定陣列的大小，然後再使用它。 這可避免在每次新增專案時都需要重新配置和複製陣列。

當陣列成長時， *nGrowBy* 參數會影響內部記憶體配置。 其使用方式絕不會影響和所報告的陣列大小 `GetSize` `GetUpperBound` 。

如果陣列的大小增加，則所有新配置的 `CObject *` 指標都會設定為 `NULL` 。

下表顯示其他類似的成員函式 `CObArray::SetSize` 。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|`void SetSize(INT_PTR nNewSize, int nGrowBy = -1);`<br /><br /> `throw(CMemoryException*);`|

### <a name="example"></a>範例

  請參閱 [CObArray：：](#getdata)的範例。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)\
[階層架構圖表](../../mfc/hierarchy-chart.md)\
[CStringArray 類別](../../mfc/reference/cstringarray-class.md)\
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)\
[CByteArray 類別](../../mfc/reference/cbytearray-class.md)\
[CWordArray 類別](../../mfc/reference/cwordarray-class.md)\
[CDWordArray 類別](../../mfc/reference/cdwordarray-class.md)
