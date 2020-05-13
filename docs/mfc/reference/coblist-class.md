---
title: CObList 類別
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749680"
---
# <a name="coblist-class"></a>CObList 類別

f 支援按順序或按`CObject`指標值可訪問的非唯一指標的有序清單。

## <a name="syntax"></a>語法

```
class CObList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COblist:COblist](#coblist)|為`CObject`指標構造空清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COblist::新增頭](#addhead)|將元素(或其他清單中的所有元素)添加到列表的頭部(製作新頭)。|
|[COblist::新增尾數](#addtail)|將元素(或其他清單中的所有元素)添加到清單的尾部(製作新尾部)。|
|[CObList:尋找](#find)|獲取指標值指定的元素的位置。|
|[COblist:尋找索引](#findindex)|獲取由零基索引指定的元素的位置。|
|[COblist::取得At](#getat)|獲取給定位置的元素。|
|[COblist:取得計數](#getcount)|傳回此清單中的元素數。|
|[COblist:抓取頭](#gethead)|返回清單的頭元素(不能為空)。|
|[COblist:抓取頭位置](#getheadposition)|返回清單頭元素的位置。|
|[COblist:抓取下一個](#getnext)|獲取下一個反覆運算元素。|
|[COblist:GetPrev](#getprev)|獲取用於反覆運算的前一個元素。|
|[COblist:取得 Size](#getsize)|傳回此清單中的元素數。|
|[COblist:取得尾翼](#gettail)|返回清單的尾部元素(不能為空)。|
|[COblist::取得尾部位置](#gettailposition)|返回清單尾部元素的位置。|
|[COblist::插入後](#insertafter)|在給定位置后插入新元素。|
|[COblist::插入之前](#insertbefore)|在給定位置之前插入新元素。|
|[COblist::是空的](#isempty)|測試空清單條件(無元素)。|
|[COblist::刪除所有](#removeall)|從此清單中刪除所有元素。|
|[COblist::刪除At](#removeat)|刪除由位置指定的元素。|
|[COblist::刪除頭](#removehead)|從清單的頭部中移除元素。|
|[COblist::刪除尾帶](#removetail)|從清單尾部中移除元素。|
|[COblist::Setat](#setat)|將元素設置在給定位置。|

## <a name="remarks"></a>備註

`CObList`清單類似於雙連結清單。

位置類型的變數是清單的鍵。 可以使用位置變數作為反覆運算器按順序遍歷清單,也可以用作保留位置的書籤。 但是,位置與索引不同。

元素插入在清單頭、尾部和已知位置非常快速。 需要按值或索引查找元素的順序搜索。 如果清單很長,則此搜索速度可能會很慢。

`CObList`合併IMPLEMENT_SERIAL宏以支援其元素的序列化和轉儲。 如果將`CObject`指標清單儲存到存檔(使用重載插入運算子或`Serialize`成員函數)時,則依次序列化每個`CObject`元素。

如果需要清單中單個`CObject`元素的轉儲,則必須將轉儲上下文的深度設置為 1 或更大。

刪除`CObList`物件或刪除其元素時,將僅`CObject`刪除指標,而不是刪除它們引用的物件。

可以從 派`CObList`生 您自己的類。 新的清單類,旨在保存指向派生自`CObject`的物件的指標,添加新的數據成員和新成員函數。 請注意,生成的清單不是嚴格鍵入安全,因為它允許插入任何`CObject`指標。

> [!NOTE]
> 如果要序列化清單,則必須在派生類的實現中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

有關使用`CObList`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>COblist::新增頭

將新元素或元素清單添加到此列表的主管。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>參數

*新元素*<br/>
要`CObject`新增到此清單的指標。

*pNewlist*<br/>
指向另一個`CObList`清單的指標。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

下表顯示了與`CObList::AddHead`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置加入頭(空**<strong>\*</strong>`newElement`**);**<br /><br /> **空添加頭( CPtrlist);** <strong>\*</strong> `pNewList` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置添加頭(cString&** `newElement` **);**<br /><br /> **位置加頭(LPCTSTR);** `newElement` **);**<br /><br /> **無效添加頭(CStringlist);** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>備註

在操作之前,清單可以為空。

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

此程序的結果如下:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>COblist::新增尾數

將新元素或元素清單添加到此清單的尾部。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>參數

*新元素*<br/>
要`CObject`新增到此清單的指標。

*pNewlist*<br/>
指向另一個`CObList`清單的指標。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>備註

在操作之前,清單可以為空。

下表顯示了與`CObList::AddTail`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置新增尾數(空**<strong>\*</strong>`newElement`**);**<br /><br /> **虛無添加目錄(CPtrlist);** <strong>\*</strong> `pNewList` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置新增尾數(const CString&** `newElement` **);**<br /><br /> **位置加尾(LPCTSTR);** `newElement` **);**<br /><br /> **虛無添加尾數(CStringlist);** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

此程序的結果如下:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>COblist:COblist

建構空`CObject`指標清單。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
用於擴展清單的記憶體分配粒度。

### <a name="remarks"></a>備註

隨著清單的增長,記憶體以*nBlockSize*條目的單位分配。 如果記憶體配置失敗,將引發`CMemoryException`。

下表顯示了與`CObList::CObList`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList(INT_PTR** `nBlockSize` **= 10 );**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CStringlist(INT_PTR** `nBlockSize` **= 10 );**|

### <a name="example"></a>範例

  下面是所有集合範例中使用的`CObject`派生`CAge`類 的清單:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

下面是`CObList`建構函式使用的範例:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CObList:尋找

依順序搜索清單以查找與指定`CObject``CObject`指標匹配的第一個指標。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*搜尋價值*<br/>
要在此清單中找到的物件指標。

*啟動後*<br/>
搜索的開始位置。

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果未找到物件,則為 NULL。

### <a name="remarks"></a>備註

請注意,將比較指標值,而不是對象的內容。

下表顯示了與`CObList::Find`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 尋找(空**<strong>\*</strong>`searchValue`**隙、位置**`startAfter` **= 空) 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置查找(LPCTSTR,**`searchValue`**位置**`startAfter` **= NULL)const;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>COblist:尋找索引

將*nIndex*的值用作清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要找到的清單元素的零基索引。

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果*nIndex*太大,則為 NULL。 (如果*nIndex*為負,則框架將生成斷言。

### <a name="remarks"></a>備註

它從清單的頭部開始順序掃描,在第*n*個元素上停止。

下表顯示了與`CObList::FindIndex`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置尋找索引( INT_PTR** `nIndex` **) 康斯特;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置尋找索引( INT_PTR** `nIndex` **) 康斯特;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>COblist::取得At

位置類型的變數是清單的鍵。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*位置*<br/>
由上一個`GetHeadPosition``Find`或成員函數調用返回的定位值。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的返回值說明。

### <a name="remarks"></a>備註

它與索引不同,並且不能自己對位置值進行操作。 `GetAt`檢索與`CObject`給定位置關聯的指標。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

下表顯示了與`CObList::GetAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&空隙\*( 位置***position***位置) 同;**<br /><br /> **空\*&获取(位置***位置***);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**const CString&取得位置***position***位置)**<br /><br /> **CString&獲取位置***position***);**|

### <a name="example"></a>範例

  請參閱[FindIndex](#findindex)的範例。

## <a name="coblistgetcount"></a><a name="getcount"></a>COblist:取得計數

取得此清單中的元素數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

包含元素計數的整數值。

下表顯示了與`CObList::GetCount`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR取得計數( ) const;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**INT_PTR取得計數( ) const;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>COblist:抓取頭

獲取`CObject`表示此列表頭元素的指標。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>傳回值

如果清單通過指向`const CObList`的指標訪問,則`GetHead`返回一個`CObject`指標。 這允許函數僅在賦值語句的右側使用,從而保護清單不進行修改。

如果直接或通過指向的`CObList`指標訪問清單,則`GetHead`返回對指標的`CObject`引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

在調用`GetHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

下表顯示了與`CObList::GetHead`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&获取头\*的空隙;空\*&拿头( );**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**康斯特·克斯特林&獲取頭( ) const;CString&獲取頭( );**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

下面的示例說明瞭賦值語句左側`GetHead`的使用。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>COblist:抓取頭位置

取得此清單頭元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果清單為空,則為 NULL。

下表顯示了與`CObList::GetHeadPosition`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置取得頭位置( ) 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置取得頭位置( ) 同;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>COblist:抓取下一個

取得*r定位*識別的清單元素,然後將*r 定位*設定到清單中`POSITION`下一個條目的值。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*r 定位*<br/>
對前`GetNext``GetHeadPosition`一個成員函數調用返回的"位置"值的引用。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的返回值說明。

### <a name="remarks"></a>備註

如果使用`GetNext`調`GetHeadPosition`用`Find`或 建立初始位置,則可以在轉發反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的最後一個元素,則*rValue*的新值將設置為 NULL。

可以在反覆運算期間刪除元素。 請參閱[RemoveAt](#removeat)的範例。

> [!NOTE]
> 從 MFC 8.0 開始,此方法的`const CObject*`const`const CObject*&`版本 已更改為傳回而不是 。  進行此更改是為了使編譯器符合C++標準。

下表顯示了與`CObList::GetNext`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

此程序的結果如下:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>COblist:GetPrev

取得*rPosition*識別的清單元素,然後將*r 定位*設定到清單中上一個條目的" 位置"

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*r 定位*<br/>
對前`GetPrev`一個成員或其他成員函數調用返回的定位值的引用。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的返回值說明。

### <a name="remarks"></a>備註

如果使用`GetPrev`調`GetTailPosition`用`Find`或 建立初始位置,則可以在反向反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的第一個元素,則*rValue*的新值將設置為 NULL。

> [!NOTE]
> 從 MFC 8.0 開始,此方法的`const CObject*`const`const CObject*&`版本 已更改為傳回而不是 。  進行此更改是為了使編譯器符合C++標準。

下表顯示了與`CObList::GetPrev`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

此程序的結果如下:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>COblist:取得 Size

返回清單元素的數量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數目。

### <a name="remarks"></a>備註

呼叫此方法以檢索清單中的元素數。

下表顯示了與`CObList::GetSize`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR取得大小( ) const;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**INT_PTR取得大小( ) const;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>COblist:取得尾翼

獲取`CObject`表示此清單尾部元素的指標。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的返回值說明。

### <a name="remarks"></a>備註

在調用`GetTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

下表顯示了與`CObList::GetTail`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**&获取的\*空隙;空\*&拿太子;(**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**康斯特CString&獲取泰斯特;CString&GetTail();**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>COblist::取得尾部位置

獲取此清單尾部元素的位置;如果清單為空,**則為 NULL。**

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果清單為空,則為 NULL。

下表顯示了與`CObList::GetTailPosition`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置取得位置( ) 同;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置取得位置( ) 同;**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>COblist::插入後

在指定位置的元素之後向此清單添加元素。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
由前`GetNext`一個、`GetPrev``Find`或成員函數調用返回的定位值。

*新元素*<br/>
要添加到此清單的物件指標。

下表顯示了與`CObList::InsertAfter`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置插入後(位置***位置***,空隙**<strong>\*</strong>`newElement`**);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置插入后(位置***位置***,康斯特CString&);** `newElement` **);**<br /><br /> **位置插入后(位置***位置***,LPCTSTR);** `newElement` **);**|

### <a name="return-value"></a>傳回值

與*位置*參數相同的位置值。

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

此程序的結果如下:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>COblist::插入之前

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
由前`GetNext`一個、`GetPrev``Find`或成員函數調用返回的定位值。

*新元素*<br/>
要添加到此清單的物件指標。

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果清單為空,則為 NULL。

下表顯示了與`CObList::InsertBefore`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置插入之前(位置***位置***,空隙**<strong>\*</strong>`newElement`**);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**位置插入之前(位置***位置***,const CString&);** `newElement` **);**<br /><br /> **位置插入之前(位置***位置***,LPCTSTR);** `newElement` **);**|

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

此程序的結果如下:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>COblist::是空的

指示此清單是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此清單為空,則為非零;否則 0。

下表顯示了與`CObList::IsEmpty`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL 是空的( ) 康斯特;**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**BOOL 是空的( ) 康斯特;**|

### <a name="example"></a>範例

  請參閱[刪除所有](#removeall)的範例。

## <a name="coblistremoveall"></a><a name="removeall"></a>COblist::刪除所有

從此清單中刪除所有元素並釋放關聯的`CObList`記憶體。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已為空,則不生成錯誤。

從 中刪除`CObList`元素時 ,將從清單中刪除物件指標。 您有責任刪除物件本身。

下表顯示了與`CObList::RemoveAll`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**不合法刪除所有( );**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**不合法刪除所有( );**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>COblist::刪除At

從該清單中移除指定的元素。

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*位置*<br/>
要從清單中刪除的元素的位置。

### <a name="remarks"></a>備註

從 中刪除`CObList`元素時 ,將從清單中刪除物件指標。 您有責任刪除物件本身。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

下表顯示了與`CObList::RemoveAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**空刪除At(位置***位置***);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**空刪除At(位置***位置***);**|

### <a name="example"></a>範例

  在清單反覆運算期間刪除元素時要小心。 下面的示例顯示了一種刪除技術,該技術保證[GetNext](#getnext)的有效**位置**值。

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

此程序的結果如下:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>COblist::刪除頭

從清單的頭部刪除元素並返回指向該元素的指標。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>傳回值

以前`CObject`位於清單頭的指標。

### <a name="remarks"></a>備註

在調用`RemoveHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

下表顯示了與`CObList::RemoveHead`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**無效\*刪除頭();**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CString 刪除頭();**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>COblist::刪除尾帶

從清單的尾部刪除元素,並返回指向該元素的指標。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>傳回值

指向清單尾部的物件的指標。

### <a name="remarks"></a>備註

在調用`RemoveTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

下表顯示了與`CObList::RemoveTail`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**無效\*去除尾數();**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**CString 刪除尾帶();**|

### <a name="example"></a>範例

有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>COblist::Setat

將元素設置在給定位置。

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*Pos*<br/>
要設置的元素的位置。

*新元素*<br/>
要`CObject`寫入清單的指標。

### <a name="remarks"></a>備註

位置類型的變數是清單的鍵。 它與索引不同,並且不能自己對位置值進行操作。 `SetAt`將`CObject`指標寫入清單中的指定位置。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

下表顯示了與`CObList::SetAt`的其他成員函數類似的。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**空設置(位置**`pos`**,const CString&);** `newElement` **);**|
|[CStringlist](../../mfc/reference/cstringlist-class.md)|**空位(位置**`pos`**,LPCTSTR);** `newElement` **);**|

### <a name="example"></a>範例

  有關`CAge`類的清單,請參閱[CObList:CObList。](#coblist)

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

此程序的結果如下:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStringlist 類別](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList 類別](../../mfc/reference/cptrlist-class.md)
