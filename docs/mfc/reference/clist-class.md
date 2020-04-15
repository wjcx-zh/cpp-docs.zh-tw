---
title: CList 類別
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372238"
---
# <a name="clist-class"></a>CList 類別

支援可循序或依值存取之非唯一物件的排序清單。

## <a name="syntax"></a>語法

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CList:CList](#clist)|建構一個空有序的清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CList::新增頭](#addhead)|將元素(或其他清單中的所有元素)添加到列表的頭部(製作新頭)。|
|[CList::新增尾數](#addtail)|將元素(或其他清單中的所有元素)添加到清單的尾部(製作新尾部)。|
|[C清單::尋找](#find)|獲取指標值指定的元素的位置。|
|[C 清單:尋找索引](#findindex)|獲取由零基索引指定的元素的位置。|
|[CList:取得At](#getat)|獲取給定位置的元素。|
|[C 清單:抓取計數](#getcount)|傳回此清單中的元素數。|
|[C 清單:抓取頭](#gethead)|返回清單的頭元素(不能為空)。|
|[CList:取得頭位置](#getheadposition)|返回清單頭元素的位置。|
|[CList:取得下一個](#getnext)|獲取下一個反覆運算元素。|
|[CList:GetPrev](#getprev)|獲取用於反覆運算的前一個元素。|
|[C 清單:抓取大小](#getsize)|傳回此清單中的元素數。|
|[C 清單::抓取尾數](#gettail)|返回清單的尾部元素(不能為空)。|
|[C 清單::抓取尾部位置](#gettailposition)|返回清單尾部元素的位置。|
|[CList::插入後](#insertafter)|在給定位置后插入新元素。|
|[CList::InsertBefore](#insertbefore)|在給定位置之前插入新元素。|
|[CList::空](#isempty)|測試空清單條件(無元素)。|
|[CList::全部刪除](#removeall)|從此清單中刪除所有元素。|
|[CList::刪除AT](#removeat)|刪除由位置指定的元素。|
|[C 清單::刪除頭](#removehead)|從清單的頭部中移除元素。|
|[C 清單::刪除尾數](#removetail)|從清單尾部中移除元素。|
|[CList::Setat](#setat)|將元素設置在給定位置。|

#### <a name="parameters"></a>參數

*類型*<br/>
儲存在清單中的物件的類型。

*ARG_TYPE*<br/>
類型用於引用存儲在清單中的物件。 可以是參考。

## <a name="remarks"></a>備註

`CList`清單類似於雙連結清單。

位置類型的變數是清單的鍵。 可以使用位置變數作為反覆運算器按順序遍歷清單,也可以用作保留位置的書籤。 但是,位置與索引不同。

元素插入在清單頭、尾部和已知位置非常快速。 需要按值或索引查找元素的順序搜索。 如果清單很長,則此搜索速度可能會很慢。

如果需要清單中單個元素的轉儲,則必須將轉儲上下文的深度設置為 1 或更大。

此類的某些成員函數調用全域説明器函數,這些函數必須針對`CList`類的大多數用途進行自定義。 請參考「宏和全域」部分中的[收集類別說明器](../../mfc/reference/collection-class-helpers.md)。

有關使用`CList`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList::新增頭

將新元素或元素清單添加到此列表的主管。

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*新元素*<br/>
新元素。

*pNewlist*<br/>
指向另一個`CList`清單的指標。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>備註

在操作之前,清單可以為空。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList::新增尾數

將新元素或元素清單添加到此清單的尾部。

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*新元素*<br/>
要加入這份清單中的項目。

*pNewlist*<br/>
指向另一個`CList`清單的指標。 *pNewList*中的元素將添加到此清單中。

### <a name="return-value"></a>傳回值

第一個版本返回新插入的元素的"位置"值。

### <a name="remarks"></a>備註

在操作之前,清單可以為空。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList:CList

建構一個空有序的清單。

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
用於擴展清單的記憶體分配粒度。

### <a name="remarks"></a>備註

隨著清單的增長,記憶體以*nBlockSize*條目的單位分配。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>C清單::尋找

依順序搜尋清單,以尋找與指定*搜尋值*匹配的第一個元素。

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*搜尋價值*<br/>
要在清單中找到的值。

*啟動後*<br/>
搜索的開始位置。 如果未指定值,則搜索從頭元素開始。

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果未找到物件,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>C 清單:尋找索引

將*nIndex*的值用作清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要找到的清單元素的零基索引。

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果*nIndex*為負或太大,則為 NULL。

### <a name="remarks"></a>備註

它從清單的頭部開始順序掃描,在第*n*個元素上停止。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList:取得At

取得給定位置的清單元素。

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定清單中的物件類型。

*位置*<br/>
要取得的元素清單中的位置。

### <a name="return-value"></a>傳回值

請參閱`GetHead`的返回值說明。

### <a name="remarks"></a>備註

`GetAt`返回與給定位置關聯的元素(或對元素的引用)。 它與索引不同,並且不能自己對位置值進行操作。 位置類型的變數是清單的鍵。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

### <a name="example"></a>範例

  請參考[CList 範例:抓取頭位置](#getheadposition)。

## <a name="clistgetcount"></a><a name="getcount"></a>C 清單:抓取計數

取得此清單中的元素數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

包含元素計數的整數值。

### <a name="remarks"></a>備註

調用此方法將生成與[CList:getSize](#getsize)方法相同的結果。

### <a name="example"></a>範例

  請參考[CList 範例::刪除頭](#removehead)。

## <a name="clistgethead"></a><a name="gethead"></a>C 清單:抓取頭

獲取此清單的頭元素(或對頭元素的引用)。

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定清單中的物件類型。

### <a name="return-value"></a>傳回值

如果清單是**const,**`GetHead`則傳回列表頭的元素的複本。 這允許函數僅在賦值語句的右側使用,並保護清單不進行修改。

如果清單不是**const,**`GetHead`則傳回對列表頭的元素的引用。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

在調用`GetHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList:取得頭位置

取得此清單頭元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果清單為空,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList:取得下一個

取得*r定位*識別的清單元素,然後將*r 定位*設定到清單中下一個條目的" 位置"

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定清單中元素的類型。

*r 定位*<br/>
對前`GetNext`一個[(GetHead定位](#getheadposition)) 或其他成員函數調用返回的定位值的引用。

### <a name="return-value"></a>傳回值

如果清單是**const** `GetNext` ,則傳回清單元素的副本。 這允許函數僅在賦值語句的右側使用,並保護清單不進行修改。

如果清單不是**const**,`GetNext`則傳回對列表元素的參考。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

如果使用`GetNext`調`GetHeadPosition`用`Find`或 建立初始位置,則可以在轉發反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的最後一個元素,則的新`rPosition`值將設置為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList:GetPrev

取得`rPosition`識別的清單項目,然後`rPosition`設置 到清單中上一個條目的"位置"值。

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*類型*<br/>
樣本參數,指定清單中元素的類型。

*r 定位*<br/>
對前`GetPrev`一個成員或其他成員函數調用返回的定位值的引用。

### <a name="return-value"></a>傳回值

如果清單是**const,**`GetPrev`則傳回列表頭的元素的複本。 這允許函數僅在賦值語句的右側使用,並保護清單不進行修改。

如果清單不是**const**,`GetPrev`則傳回對列表元素的參考。 這允許在賦值語句的任意一側使用函數,從而允許修改清單條目。

### <a name="remarks"></a>備註

如果使用`GetPrev`調`GetTailPosition`用`Find`或 建立初始位置,則可以在反向反覆運算迴圈中使用。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

如果檢索到的元素是清單中的第一個元素,則*rValue*的新值將設置為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>C 清單:抓取大小

返回清單元素的數量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數目。

### <a name="remarks"></a>備註

呼叫此方法以檢索清單中的元素數。  調用此方法將生成與[CList::GetCount](#getcount)方法相同的結果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>C 清單::抓取尾數

獲取`CObject`表示此清單尾部元素的指標。

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>參數

*類型*<br/>
指定清單中元素類型的範本參數。

### <a name="return-value"></a>傳回值

請參閱[GetHead](../../mfc/reference/coblist-class.md#gethead)的返回值說明。

### <a name="remarks"></a>備註

在調用`GetTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](../../mfc/reference/coblist-class.md#isempty)驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>C 清單::抓取尾部位置

獲取此清單尾部元素的位置;如果清單為空,則為 NULL。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反覆運算或對象指標檢索的定位值;如果清單為空,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::插入後

在指定位置的元素之後向此清單添加元素。

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
由前`GetNext`一個、`GetPrev``Find`或成員函數調用返回的定位值。

*ARG_TYPE*<br/>
指定清單元素類型的範本參數。

*新元素*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取的 POSITION 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::插入之前

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
由前`GetNext`一個、`GetPrev``Find`或成員函數調用返回的定位值。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*新元素*<br/>
要加入這份清單中的項目。

### <a name="return-value"></a>傳回值

可用於反覆項目或清單項目擷取的 POSITION 值。

### <a name="remarks"></a>備註

如果*位置*為 NULL,則元素將插入到列表的頭部。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::空

指示此清單是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此清單為空,則為非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::全部刪除

從此清單中刪除所有元素並釋放關聯的記憶體。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已為空,則不生成錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList::刪除AT

從該清單中移除指定的元素。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*位置*<br/>
要從清單中刪除的元素的位置。

### <a name="remarks"></a>備註

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>C 清單::刪除頭

從清單的頭部刪除元素並返回指向該元素的指標。

```
TYPE RemoveHead();
```

### <a name="parameters"></a>參數

*類型*<br/>
指定清單中元素類型的範本參數。

### <a name="return-value"></a>傳回值

以前位於清單頭的元素。

### <a name="remarks"></a>備註

在調用`RemoveHead`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>C 清單::刪除尾數

從清單的尾部刪除元素,並返回指向該元素的指標。

```
TYPE RemoveTail();
```

### <a name="parameters"></a>參數

*類型*<br/>
指定清單中元素類型的範本參數。

### <a name="return-value"></a>傳回值

位於清單尾部的元素。

### <a name="remarks"></a>備註

在調用`RemoveTail`之前,必須確保清單不為空。 如果清單為空,則Microsoft基礎類庫的調試版本斷言。 使用[IsEmpty](#isempty)驗證清單是否包含元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList::Setat

位置類型的變數是清單的鍵。

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>參數

*Pos*<br/>
要設置的元素的位置。

*ARG_TYPE*<br/>
指定清單項目 (可以是參考) 之類型的樣板參數。

*新元素*<br/>
要加入清單中的元素。

### <a name="remarks"></a>備註

它與索引不同,並且不能自己對位置值進行操作。 `SetAt`將元素寫入清單中的指定位置。

您必須確保您的「位置」值表示清單中的有效位置。 如果無效,則Microsoft基礎類庫的調試版本斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMap 類別](../../mfc/reference/cmap-class.md)<br/>
[CArray 類別](../../mfc/reference/carray-class.md)
