---
title: CAtlList 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 91b1841423fe159bb5fdd0f06a112c601b1dbc83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318934"
---
# <a name="catllist-class"></a>CAtlList 類別

此類提供用於創建和管理清單物件的方法。

## <a name="syntax"></a>語法

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>參數

*E*<br/>
元素類型。

*埃特格*<br/>
複製或移動元素的代碼。 有關詳細資訊[,請參閱 CElementTraits 類別](../../atl/reference/celementtraits-class.md)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[清單::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlList:CAtlList](#catllist)|建構函式。|
|[CAtlList:_CAtlList](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlList::新增頭](#addhead)|呼叫此方法以向列表的頭部添加元素。|
|[CAtlList::新增頭清單](#addheadlist)|呼叫此方法以將現有清單添加到列表的頭部。|
|[CAtlList::新增尾](#addtail)|呼叫此方法以將元素添加到此清單的尾部。|
|[CAtlList::新增尾號](#addtaillist)|呼叫此方法以將現有清單添加到此清單的尾部。|
|[CAtlList::斷言有效](#assertvalid)|呼叫此方法以確認清單有效。|
|[CAtlList:尋找](#find)|呼叫此方法以搜尋指定元素的清單。|
|[CAtlList:尋找索引](#findindex)|調用此方法以獲取元素的位置,給定索引值。|
|[CAtlList:GetAt](#getat)|呼叫此方法以返回清單中指定位置的元素。|
|[CAtlList:取得計數](#getcount)|呼叫此方法以返回清單中的物件數。|
|[CAtlList:取得頭](#gethead)|呼叫此方法以返回清單頭的元素。|
|[CAtlList:抓取頭位置](#getheadposition)|呼叫此方法以獲取清單頭的位置。|
|[CAtlList:取得下一個](#getnext)|呼叫此方法以從清單中返回下一個元素。|
|[CAtlList:GetPrev](#getprev)|呼叫此方法以從清單中返回以前的元素。|
|[CAtlList:GetTail](#gettail)|呼叫此方法以返回清單尾部的元素。|
|[CAtlList:抓取尾部位置](#gettailposition)|呼叫此方法以獲取清單尾部的位置。|
|[CAtlList:插入後](#insertafter)|呼叫此方法以在指定位置後將新元素插入清單中。|
|[CAtlList::插入之前](#insertbefore)|呼叫此方法在指定位置之前將新元素插入清單中。|
|[CAtlList::空](#isempty)|呼叫此方法以確定清單是否為空。|
|[Catllist::移動頭](#movetohead)|呼叫此方法將指定元素移動到列表的頭部。|
|[Catllist::移動到尾](#movetotail)|呼叫此方法將指定元素移動到清單的尾部。|
|[CAtlList::刪除所有](#removeall)|呼叫此方法以從清單中刪除所有元素。|
|[CAtlList::刪除At](#removeat)|呼叫此方法從清單中刪除單個元素。|
|[CAtlList::刪除頭](#removehead)|呼叫此方法以刪除清單頭的元素。|
|[CAtlList::刪除頭無返回](#removeheadnoreturn)|呼叫此方法以刪除清單頭的元素,而不返回值。|
|[CAtlList::刪除尾](#removetail)|呼叫此方法以刪除清單尾部的元素。|
|[CAtllist::刪除尾號不返回](#removetailnoreturn)|呼叫此方法以刪除清單尾部的元素,而不返回值。|
|[CAtlList::Setat](#setat)|呼叫此方法以在清單中的給定位置設定元素的值。|
|[CAtlList::交換元素](#swapelements)|呼叫此方法以交換清單中的元素。|

## <a name="remarks"></a>備註

該`CAtlList`類支援按順序或按值訪問的非唯一物件的有序清單。 `CAtlList`清單類似於雙重連結清單。 每個清單都有一個頭和一個尾,新元素(或在某些情況下的清單)可以添加到清單的任一端,或插入特定元素之前或之後。

大多數`CAtlList`方法都使用倉位值。 方法使用此值來引用存儲元素的實際記憶體位置,不應直接計算或預測此值。 如果需要訪問清單中的第*n*個元素,方法[CAtlList:findIndex](#findindex)將返回給定索引的相應位置值。 方法[CAtlList:GetNext](#getnext)和[CAtlList:GetPrev](#getprev)可用於反覆運算清單中的物件。

有關 ATL 提供的收集類的詳細資訊,請參閱[ATL 收集類](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::新增頭

呼叫此方法以向列表的頭部添加元素。

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>參數

*元素*<br/>
新元素。

### <a name="return-value"></a>傳回值

返回新添加的元素的位置。

### <a name="remarks"></a>備註

如果使用第一個版本,則使用其預設構造函數而不是其複製構造函數創建空元素。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::新增頭清單

呼叫此方法以將現有清單添加到列表的頭部。

```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>參數

*plNew*<br/>
要加入的清單。

### <a name="remarks"></a>備註

*plNew*指向的清單將插入到現有清單的開頭。 在除錯產生中,如果*plNew*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList::新增尾

呼叫此方法以將元素添加到此清單的尾部。

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>參數

*元素*<br/>
要加入的項目。

### <a name="return-value"></a>傳回值

返回新添加的元素的位置。

### <a name="remarks"></a>備註

如果使用第一個版本,則使用其預設構造函數而不是其複製構造函數創建空元素。 元素將添加到清單的末尾,因此它現在成為尾部。 此方法可與空清單一起使用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::新增尾號

呼叫此方法以將現有清單添加到此清單的尾部。

```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>參數

*plNew*<br/>
要加入的清單。

### <a name="remarks"></a>備註

*plNew*指向的清單在列表物件中的最後一個元素(如果有)之後插入。 因此 *,plNew*清單中的最後一個元素成為尾部。 在除錯產生中,如果*plNew*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::斷言有效

呼叫此方法以確認清單有效。

```
void AssertValid() const;
```

### <a name="remarks"></a>備註

在除錯產生中,如果清單物件無效,將發生斷言失敗。 要有效,空列表必須同時顯示頭部和尾部指向 NULL,並且不為空的清單必須同時顯示頭部和尾部指向有效位址。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList:CAtlList

建構函式。

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
區塊大小。

### <a name="remarks"></a>備註

`CAtlList`對象的構造函數。 塊大小是需要新元素時分配的記憶體量的度量。 較大的塊大小減少了對記憶體分配例程的調用,但使用的資源更多。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList:_CAtlList

解構函式。

```
~CAtlList() throw();
```

### <a name="remarks"></a>備註

釋放所有已分配的資源,包括調用[CAtlList::刪除所有](#removeall)內容以從清單中刪除所有元素。

在除錯產生中,如果清單在調用`RemoveAll`後仍包含某些元素,則將發生斷言失敗。

## <a name="catllistfind"></a><a name="find"></a>CAtlList:尋找

呼叫此方法以搜尋指定元素的清單。

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>參數

*元素*<br/>
要在清單中找到的元素。

*位置啟動後*<br/>
搜索的開始位置。 如果未指定值,則搜索從頭元素開始。

### <a name="return-value"></a>傳回值

如果找到元素,則返回元素的「位置」值,否則傳回 NULL。

### <a name="remarks"></a>備註

在除錯產生中,如果清單物件無效,或者*posStartAfter*值不在範圍範圍內,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList:尋找索引

調用此方法以獲取元素的位置,給定索引值。

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>參數

*i 元素*<br/>
所需清單元素的零基索引。

### <a name="return-value"></a>傳回值

返回相應的位置值,如果*iElement*不在範圍範圍內,則傳回 NULL。

### <a name="remarks"></a>備註

此方法傳回與給定索引值對應的「位置」,允許訪問清單中的第*n*個元素。

在除錯產生中,如果清單物件無效,將發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList:GetAt

呼叫此方法以返回清單中指定位置的元素。

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
指定特定元素的定位值。

### <a name="return-value"></a>傳回值

對元素的引用或複本。

### <a name="remarks"></a>備註

如果清單是**const** `GetAt` ,則傳回元素的副本。 這允許僅在賦值語句的右側使用該方法,並保護清單免受修改。

如果清單不是**const**,`GetAt`則傳回對元素的引用。 這允許在賦值語句的任意一側使用該方法,從而允許修改清單條目。

在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例:尋找索引](#findindex)。

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList:取得計數

呼叫此方法以返回清單中的物件數。

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>傳回值

傳回清單中項目的數目。

### <a name="example"></a>範例

請參考[CAtlList 的範例:尋找](#find)。

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList:取得頭

呼叫此方法以返回清單頭的元素。

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>傳回值

返回對清單頭的元素的引用或複本。

### <a name="remarks"></a>備註

如果清單是**const,**`GetHead`則傳回列表頭的元素的複本。 這允許僅在賦值語句的右側使用該方法,並保護清單免受修改。

如果清單不是**const,**`GetHead`則傳回對列表頭的元素的引用。 這允許在賦值語句的任意一側使用該方法,從而允許修改清單條目。

在除錯產生中,如果清單的主管指向 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例::addHead](#addhead)。

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList:抓取頭位置

呼叫此方法以獲取清單頭的位置。

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>傳回值

返回與列表頭的元素對應的"位置"值。

### <a name="remarks"></a>備註

如果清單為空,則返回的值為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList:取得下一個

呼叫此方法以從清單中返回下一個元素。

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
由上一個調用返回的"位置"`GetNext`值[,CAtlList::getHeadposition](#getheadposition)或其他`CAtlList`方法。

### <a name="return-value"></a>傳回值

如果清單是**const** `GetNext` ,則傳回清單的下一個元素的副本。 這允許僅在賦值語句的右側使用該方法,並保護清單免受修改。

如果清單不是**const**,`GetNext`則傳回對清單下一個元素的參考。 這允許在賦值語句的任意一側使用該方法,從而允許修改清單條目。

### <a name="remarks"></a>備註

位置計數器*將更新*以指向清單中的下一個元素,如果不再有元素,則為 NULL。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例:抓取頭位置](#getheadposition)。

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList:GetPrev

呼叫此方法以從清單中返回以前的元素。

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
由上一個調用返回的"位置"`GetPrev`值[,CAtlList::GetTailposition](#gettailposition)或其他`CAtlList`方法。

### <a name="return-value"></a>傳回值

如果清單是**const** `GetPrev` ,則傳回清單元素的副本。 這允許僅在賦值語句的右側使用該方法,並保護清單免受修改。

如果清單不是**const**,`GetPrev`則傳回對列表元素的參考。 這允許在賦值語句的任意一側使用該方法,從而允許修改清單條目。

### <a name="remarks"></a>備註

位置計數器*將更新*以指向清單中的前一個元素,如果沒有更多元素,則為 NULL。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例:抓取尾部位置](#gettailposition)。

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList:GetTail

呼叫此方法以返回清單尾部的元素。

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>傳回值

返回對清單末尾的元素的引用或複本。

### <a name="remarks"></a>備註

如果清單是**const,**`GetTail`則傳回列表頭的元素的複本。 這允許僅在賦值語句的右側使用該方法,並保護清單免受修改。

如果清單不是**const,**`GetTail`則傳回對列表頭的元素的引用。 這允許在賦值語句的任意一側使用該方法,從而允許修改清單條目。

在除錯產生中,如果清單的尾部指向 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例::新增尾數](#addtail)。

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList:抓取尾部位置

呼叫此方法以獲取清單尾部的位置。

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>傳回值

返回與清單尾部的元素對應的"位置"值。

### <a name="remarks"></a>備註

如果清單為空,則返回的值為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>清單::INARGTYPE

當元素作為輸入參數傳遞時使用的類型。

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList:插入後

呼叫此方法以在指定位置後將新元素插入清單中。

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*Pos*<br/>
將插入新元素的「位置」 值。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>傳回值

返回新元素的"位置"值。

### <a name="remarks"></a>備註

在除錯產生中,如果清單無效、插入失敗或嘗試在尾部後插入元素,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::插入之前

呼叫此方法在指定位置之前將新元素插入清單中。

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*Pos*<br/>
新元素將插入到清單中,然後在此位置值之前。

*元素*<br/>
要插入的元素。

### <a name="return-value"></a>傳回值

返回新元素的"位置"值。

### <a name="remarks"></a>備註

在除錯產生中,如果清單無效、插入失敗或嘗試將元素插入到頭之前,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList::空

呼叫此方法以確定清單是否為空。

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>傳回值

如果清單不包含任何物件,則返回 true,否則為 false。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>Catllist::移動頭

呼叫此方法將指定元素移動到列表的頭部。

```
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
要移動的元素的定位值。

### <a name="remarks"></a>備註

指定元素從其當前位置移動到列表的頭部。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>Catllist::移動到尾

呼叫此方法將指定元素移動到清單的尾部。

```
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
要移動的元素的定位值。

### <a name="remarks"></a>備註

指定元素從其當前位置移動到清單的尾部。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例:移動頭](#movetohead)。

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::刪除所有

呼叫此方法以從清單中刪除所有元素。

```
void RemoveAll() throw();
```

### <a name="remarks"></a>備註

此方法從清單中刪除所有元素並釋放分配的記憶體。 在除錯產生中,如果未刪除所有元素或清單結構已損壞,則將引發 ATLASSERT。

### <a name="example"></a>範例

請參考[CAtlList 的範例::是空的](#isempty)。

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::刪除At

呼叫此方法從清單中刪除單個元素。

```
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>參數

*Pos*<br/>
要刪除的元素的定位值。

### <a name="remarks"></a>備註

*刪除 pos*引用的元素,並釋放記憶體。 可以使用`RemoveAt`來移除清單的頭部或尾部。

在除錯產生中,如果清單無效,或者刪除該元素導致清單訪問不屬於清單結構的記憶體,則將發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::刪除頭

呼叫此方法以刪除清單頭的元素。

```
E RemoveHead();
```

### <a name="return-value"></a>傳回值

返回清單頭的元素。

### <a name="remarks"></a>備註

頭元素將從清單中刪除,並釋放記憶體。 返回元素的副本。 在調試生成中,如果清單為空,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::刪除頭無返回

呼叫此方法以刪除清單頭的元素,而不返回值。

```
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>備註

頭元素將從清單中刪除,並釋放記憶體。 在調試生成中,如果清單為空,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例::是空的](#isempty)。

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::刪除尾

呼叫此方法以刪除清單尾部的元素。

```
E RemoveTail();
```

### <a name="return-value"></a>傳回值

返回清單尾部的元素。

### <a name="remarks"></a>備註

尾元素將從清單中刪除,並釋放記憶體。 返回元素的副本。 在調試生成中,如果清單為空,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtllist::刪除尾號不返回

呼叫此方法以刪除清單尾部的元素,而不返回值。

```
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>備註

尾元素將從清單中刪除,並釋放記憶體。 在調試生成中,如果清單為空,則會發生斷言失敗。

### <a name="example"></a>範例

請參考[CAtlList 的範例::是空的](#isempty)。

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::Setat

呼叫此方法以在清單中的給定位置設定元素的值。

```
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>參數

*Pos*<br/>
與要更改的元素對應的位置值。

*元素*<br/>
新元素值。

### <a name="remarks"></a>備註

將現有值取代為*元素*。 在除錯產生中,如果*pos*等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::交換元素

呼叫此方法以交換清單中的元素。

```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>參數

*位置1*<br/>
第一個位置值。

*pos2*<br/>
第二個位置值。

### <a name="remarks"></a>備註

交換指定兩個位置的元素。 在除錯產生中,如果任一位置值等於 NULL,則會發生斷言失敗。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>另請參閱

[CList 類別](../../mfc/reference/clist-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
