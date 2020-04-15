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
ms.openlocfilehash: 7b923fd9231d3652d8d2f1750a8024d15287811e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360451"
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
|[CObarray:CObarray](#cobarray)|為`CObject`指標構造一個空陣組。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObarray:新增](#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObarray::附加](#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObarray:複製](#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObarray::元素At](#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObarray::免費額外](#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObarray::取得At](#getat)|傳回給定索引的值。|
|[CObarray:取得計數](#getcount)|取得此陣列中項目的數目。|
|[CObarray:抓取資料](#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CObarray:取得 Size](#getsize)|取得此陣列中項目的數目。|
|[CObarray::取得上部](#getupperbound)|傳回最大的有效索引。|
|[CObarray::插入At](#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CObarray::是空的](#isempty)|判定陣列是否是空的。|
|[CObarray::刪除所有](#removeall)|從此陣列移除所有項目。|
|[CObarray::刪除At](#removeat)|移除特定索引處的項目。|
|[CObarray::Setat](#setat)|設定給定索引的值；不容許陣列成長。|
|[CObarray::Setat增長](#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CObarray::設定大小](#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CObArray::運算子\[\]](#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

這些物件陣列類似於 C 陣列,但它們可以根據需要動態收縮和增長。

陣列索引始終從位置 0 開始。 您可以決定是否修復上限,或者允許在將元素添加到當前綁定後展開陣列。 即使某些元素為空,記憶體也會連續分配給上限。

在 Win32`CObArray`下, 物件的大小僅限於可用記憶體。

與 C 陣列一`CObArray`樣, 索引元素的訪問時間是恆定的,並且與陣列大小無關。

`CObArray`合併IMPLEMENT_SERIAL宏以支援其元素的序列化和轉儲。 如果將`CObject`指標數組儲存在存檔中(使用重載插入運算符或`Serialize`成員函數,則每個`CObject`元素依次與其陣列索引一起序列化。

如果需要陣列中單個`CObject`元素的轉儲,則必須`CDumpContext`將物件的深度設置為 1 或更大。

刪除`CObArray`物件或刪除其元素時,將僅`CObject`刪除指標,而不是刪除它們引用的物件。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

陣列類派生類似於清單派生。 有關特殊用途清單類的派生的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

> [!NOTE]
> 如果要序列化陣列,則必須在派生類的實現中使用IMPLEMENT_SERIAL宏。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObarray:新增

將新元素添加到陣列的末尾,將陣列增加1。

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>參數

*新元素*<br/>
要`CObject`添加到此陣列的指標。

### <a name="return-value"></a>傳回值

添加元素的索引。

### <a name="remarks"></a>備註

如果[SetSize](#setsize)已使用*nGrowBy*值大於 1,則可能會分配額外的記憶體。 但是,上限僅增加 1。

下表顯示了與`CObArray::Add`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR添加(位元組**`newElement`**);**<br /><br /> **投擲(C記憶例外\*);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR添加(DWORD);** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR添加(無效**<strong>\*</strong>`newElement`**);**<br /><br /> **投擲(C記憶例外\*);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR加(LPCTSTR);** `newElement` **投擲\*( CMemoryexception )**<br /><br /> **INT_PTR添加(cString&);** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR加(UINT);** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR添加(WORD);** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|

### <a name="example"></a>範例

  有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

此程序的結果如下:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObarray::附加

調用此成員函數將另一個陣列的內容添加到給定陣列的末尾。

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要追加到陣列的元素的源。

### <a name="return-value"></a>傳回值

第一個附加元素的索引。

### <a name="remarks"></a>備註

陣列必須具有相同的類型。

如有必要,`Append`可以分配額外的記憶體以容納追加到陣列的元素。

下表顯示了與`CObArray::Append`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR附錄(cByteArray** *&src);* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR追加(cdWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR附錄(cPtrArray&** *src);* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR附錄(cStringarray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR附錄(cuIntarray** *&src);* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR附錄(cWordArray&src);** *src* **);**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObarray:複製

呼叫此成員函數,用相同類型的另一個陣列的元素覆蓋給定陣列的元素。

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>參數

*src*<br/>
要複製到陣列的元素的源。

### <a name="remarks"></a>備註

`Copy`不釋放記憶體;但是,如有必要,`Copy`可能會分配額外的記憶體以適應複製到陣列的元素。

下表顯示了與`CObArray::Copy`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**無效複製(cByteArray&** *src);* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**無效複製(cst CDWordArray&** *src);* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**不合法複製(const CPtrarray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**無效複製(cStringarray&** *src);* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**不合法複製(const CUIntarray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**無效拷貝(cWordArray&** *src);* **);**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObarray:CObarray

構造空`CObject`指標數組。

```
CObArray();
```

### <a name="remarks"></a>備註

陣列一次增加一個元素。

下表顯示了與`CObArray::CObArray`的其他建構函數的類似的 。

|類別|建構函式|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray(**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray(**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray(**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**弦樂();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntarray(**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray(**|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObarray::元素At

傳回陣列中項目指標的臨時參考。

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等`GetUpperBound`於返回的值的整數索引。

### <a name="return-value"></a>傳回值

對指標的`CObject`引用。

### <a name="remarks"></a>備註

它用於實現陣列的左側賦值運算符。 請注意,這是一個高級函數,應僅用於實現特殊陣列運算符。

下表顯示了與`CObArray::ElementAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE&元素(INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD&元素(INT_PTR);** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**無效\*&元素(INT_PTR);** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**弦&元素(INT_PTR);** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT&元素(INT_PTR);** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD&元素(INT_PTR);** `nIndex` **);**|

### <a name="example"></a>範例

  請參考[CObarray 範例::取得 Size](#getsize)。

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObarray::免費額外

釋放在陣列增長時分配的任何額外記憶體。

```
void FreeExtra();
```

### <a name="remarks"></a>備註

此函數對陣列的大小或上限沒有影響。

下表顯示了與`CObArray::FreeExtra`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**無效免費額外();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**無效免費額外();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**無效免費額外();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**無效免費額外();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**無效免費額外();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**無效免費額外();**|

### <a name="example"></a>範例

  請參考[CObarray 範例::取得資料](#getdata)。

## <a name="cobarraygetat"></a><a name="getat"></a>CObarray::取得At

在指定的索引處返回陣列元素。

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等`GetUpperBound`於返回的值的整數索引。

### <a name="return-value"></a>傳回值

當前`CObject`位於此索引的指標元素。

### <a name="remarks"></a>備註

> [!NOTE]
> 傳遞負值或大於返回`GetUpperBound`的值的值將導致斷言失敗。

下表顯示了與`CObArray::GetAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE 取得( INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD 取得( INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**獲取\*( INT_PTR** `nIndex` **) 同一點;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString Getat( INT_PTR** `nIndex` **) 同一點;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT Getat( INT_PTR** `nIndex` **) 康斯特;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD 獲取( INT_PTR** `nIndex` **) 康斯特;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObarray:取得計數

返回陣列元素的數量。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

陣列中的項目數目。

### <a name="remarks"></a>備註

調用此方法以檢索陣列中的元素數。 由於索引是零基的,因此大小大於最大索引的 1。

下表顯示了與`CObArray::GetCount`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR取得計數( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR取得計數( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR取得計數( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR取得計數( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR取得計數( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR取得計數( ) const;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObarray:抓取資料

使用此成員函數可以直接訪問陣列中的元素。

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>傳回值

指向指標數組的`CObject`指標。

### <a name="remarks"></a>備註

如果沒有可用的元素,`GetData`則傳回 null 值。

雖然直接存取陣列的元素可以説明您更快地工作,但呼`GetData`叫 時請謹慎操作 。您犯的任何錯誤都會直接影響陣列的元素。

下表顯示了與`CObArray::GetData`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**康斯特 BYTE\*獲取數據 ( ) const;字節\*獲取數據();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**康斯特DWORD\*取得資料( ) const;DWORD\*取得資料( )**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空白\*\*取得資料( )\*\*const; 空取資料 ( ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\*獲取資料 ( ) const;CString\*獲取數據();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**康斯特 UINT\*獲取數據 ( ) const;UINT\*獲取數據();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**康斯特WORD\*取得資料( )WORD\*取得資料(**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObarray:取得 Size

傳回陣列的大小。

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>備註

由於索引是零基的,因此大小大於最大索引的 1。

下表顯示了與`CObArray::GetSize`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR取得大小( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR取得大小( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR取得大小( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR取得大小( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR取得大小( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR取得大小( ) const;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObarray::取得上部

返回此陣列的當前上限。

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>傳回值

上限的索引(從零開始)。

### <a name="remarks"></a>備註

由於陣列索引是零基的,因此此函數傳回的值 1`GetSize`小於 。

條件`GetUpperBound( )`= -1 表示陣列不包含任何元素。

下表顯示了與`CObArray::GetUpperBound`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObarray::插入At

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
可能大於返回`GetUpperBound`的值的整數索引。

*新元素*<br/>
要`CObject`放置在此陣列中的指標。 允許*新的*值 NULL 元素。

*n( N) Count*<br/>
應插入此元素的次數(預設值為1)。

*nStartIndex*<br/>
可能大於返回`GetUpperBound`的值的整數索引。

*pNewArray*<br/>
另一個包含要添加到此陣列的元素的陣列。

### <a name="remarks"></a>備註

第一個版本在`InsertAt`數位中的指定索引中插入一個元素(或元素的多個副本)。 在此過程中,它向上移動(通過增加索引)此索引中的現有元素,並向上移動其上方的所有元素。

第二個版本從*nStartIndex*位置`CObArray`開始插入另一個集合中的所有元素。

相反`SetAt`,函數替換一個指定的陣列元素,並且不移動任何元素。

下表顯示了與`CObArray::InsertAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空插入At(INT_PTR,**`nIndex`**位元組**`newElement`**,int** `nCount` = **1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**);****空插入****(INT_PTR,CBytearray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空插入At(INT_PTR,DWORD,int** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**);****空插入****(INT_PTR,CDWordarray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空插入At(INT_PTR,**`nIndex`**空**<strong>\*</strong>`newElement`**,int** `nCount` = **1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**);****空插入****(INT_PTR,CPtrarray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**零空插入At(INT_PTR,LPCTSTR,int** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**空插入** **);** **(INT_PTR,CStringarray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空插入At(INT_PTR,UINT,int** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**);****空插入****(INT_PTR,CUIntarray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空插入At(INT_PTR,WORD,int** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **投擲(C記憶例外\*);**<br /><br /> <strong>\*</strong>`nStartIndex`**);****虛插入****(INT_PTR,CWordarray);** `pNewArray`<br /><br /> **投擲(C記憶例外\*);**|

### <a name="example"></a>範例

  有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

此程序的結果如下:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObarray::是空的

判定陣列是否是空的。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果陣列為空,則非零;否則 0。

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::運算符 |

這些下標運算符是 和`SetAt``GetAt`函數的方便替代。

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>備註

第一個運算符(稱為非**const**陣列)可以在賦值語句的右側(r 值)或左側(l 值)上使用。 第二個,稱為**const**陣列,只能在右側使用。

庫的調試版本斷言下標(在賦值語句的左側或右側)是否超出邊界。

下表顯示了與`CObArray::operator []`的其他運算子的類似的 。

|類別|運算子|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE&運算符 [(int_ptr** `nindex` ** \);**<br /><br /> **BYTE 運算符 [(int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD&運算符 [(int_ptr** `nindex` ** \);**<br /><br /> **DWORD 運算符 [(int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**無效\*&运算符 (int_ptr** `nindex` ** \);**<br /><br /> **無效\*運算符 [(int_ptr**`nindex`**\)同;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString&運算符 [(int_ptr** `nindex` ** \);**<br /><br /> **CString 運算符 [(int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT&運算符 [(int_ptr** `nindex` ** \);**<br /><br /> **UINT 運算符 [(int_ptr**`nindex`**\)同;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD&運算符 [(int_ptr** `nindex` ** \);**<br /><br /> **WORD 運算符 [(int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObarray::刪除所有

從該陣列中移除所有指標,但實際上不會刪除物件`CObject`。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果數組已為空,則函數仍然有效。

該`RemoveAll`函數釋放用於指標存儲的所有記憶體。

下表顯示了與`CObArray::RemoveAll`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**不合法刪除所有( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**不合法刪除所有( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**不合法刪除所有( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**不合法刪除所有( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**不合法刪除所有( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**不合法刪除所有( );**|

### <a name="example"></a>範例

有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObarray::刪除At

刪除從陣列中指定索引開始的一個或多個元素。

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等`GetUpperBound`於返回的值的整數索引。

*n( N) Count*<br/>
要移除的項目數目。

### <a name="remarks"></a>備註

在此過程中,它會向下移動刪除的元素上方的所有元素。 它會遞減陣列的上限,但不釋放記憶體。

如果嘗試刪除的元素多於刪除點上方的陣列中包含的元素,則庫的調試版本斷言。

函數`RemoveAt`從陣列中`CObject`刪除指標,但不會刪除物件本身。

下表顯示了與`CObArray::RemoveAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空移(INT_PTR,INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空移(INT_PTR,INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空移(INT_PTR,INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空移(INT_PTR,INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空移(INT_PTR,INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空刪除At(INT_PTR,INT_PTRnCount** `nIndex` **, INT_PTR** *nCount* **= 1);**|

### <a name="example"></a>範例

  有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

此程序的結果如下:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObarray::Setat

在指定的索引處設置陣列元素。

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 且小於或等`GetUpperBound`於返回的值的整數索引。

*新元素*<br/>
要在此陣列中插入的對象指標。 允許 NULL 值。

### <a name="remarks"></a>備註

`SetAt`不會導致陣組增長。 如果`SetAtGrow`希望陣列自動增長,請使用。

必須確保索引值表示陣列中的有效位置。 如果它超出邊界,則庫的調試版本斷言。

下表顯示了與`CObArray::SetAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空盤(INT_PTR,** `nIndex` **BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空設置(INT_PTR,** `nIndex` **DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空設定(INT_PTR,** `nIndex`**無效**<strong>\*</strong>`newElement`**);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空設定(INT_PTR,** `nIndex` **LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空集(INT_PTR,** `nIndex` **UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空集(INT_PTR,WORD);** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>範例

  有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

此程序的結果如下:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObarray::Setat增長

在指定的索引處設置陣列元素。

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
大於或等於 0 的整數索引。

*新元素*<br/>
要添加到此陣列的物件指標。 允許 NULL 值。

### <a name="remarks"></a>備註

如有必要,陣列會自動增長(即,調整上限以適應新元素)。

下表顯示了與`CObArray::SetAtGrow`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空塞特增長(INT_PTR,**`nIndex`**位元組**`newElement`**);**<br /><br /> **投擲(C記憶例外\*);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空集(INT_PTR,** `nIndex` **DWORD** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空(INT_PTR,** `nIndex`**空**<strong>\*</strong>`newElement`**);**<br /><br /> **投擲(C記憶例外\*);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空套(INT_PTR,LPCTSTR);** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空塞特增長(INT_PTR,UINT);** `nIndex` **, UINT** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空集(INT_PTR,WORD);** `nIndex` **, WORD** `newElement` **);**<br /><br /> **投擲(C記憶例外\*);**|

### <a name="example"></a>範例

  有關所有集合範例中使用的類的清單,`CAge`請參閱[CObList:CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

此程序的結果如下:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObarray::設定大小

建立空陣組或現有陣列的大小;如有必要,分配記憶體。

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>參數

*n 新尺寸*<br/>
新的陣列大小(元素數)。 必須大於或等於 0。

*nGrowBy*<br/>
如果需要增加大小,要分配的最小元素槽數。

### <a name="remarks"></a>備註

如果新大小小於舊大小,則陣列將被截斷,並釋放所有未使用的記憶體。 為提高效率,請`SetSize`調用在使用陣列之前設置陣列的大小。 這樣可以防止每次添加項時都需要重新分配和複製陣列。

*nGrowBy*參數在陣列增長時影響內部記憶體分配。 其使用永遠不會影響 和`GetSize``GetUpperBound`報告的陣列大小。

如果陣列的大小已成長,則所有新分配的**CObject**<strong>\*</strong>指標都設定為 NULL。

下表顯示了與`CObArray::SetSize`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**空設置大小(INT_PTR,int** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **投擲(C記憶例外\*);**|

### <a name="example"></a>範例

  請參考[CObarray 範例::取得資料](#getdata)。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStringArray 類別](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray 類別](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray 類別](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray 類別](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray 類別](../../mfc/reference/cdwordarray-class.md)
