---
title: CObList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fbf635b2f6d07486a6a8961305e0b218b3c24926
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429678"
---
# <a name="coblist-class"></a>CObList 類別

排序清單的非唯一的 fSupports`CObject`指標可循序或依指標值。

## <a name="syntax"></a>語法

```
class CObList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObList::CObList](#coblist)|建構空的清單，如`CObject`指標。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObList::AddHead](#addhead)|將 （讓新的標頭） 清單的標頭中的項目 （或另一個清單中的所有項目）。|
|[CObList::AddTail](#addtail)|將 （讓新的結尾） 的清單結尾的項目 （或另一個清單中的所有項目）。|
|[CObList::Find](#find)|取得指標值所指定項目的位置。|
|[CObList::FindIndex](#findindex)|取得項目以零為起始的索引所指定的位置。|
|[CObList::GetAt](#getat)|取得的項目中指定的位置。|
|[CObList::GetCount](#getcount)|這份清單中傳回的項目數。|
|[CObList::GetHead](#gethead)|傳回 （不能是空的） 清單的標頭的項目。|
|[CObList::GetHeadPosition](#getheadposition)|傳回清單的標頭項目的位置。|
|[CObList::GetNext](#getnext)|取得逐一查看的下一個項目。|
|[CObList::GetPrev](#getprev)|取得逐一查看的上一個項目。|
|[CObList::GetSize](#getsize)|這份清單中傳回的項目數。|
|[CObList::GetTail](#gettail)|傳回 （不能是空的） 清單的結尾項目。|
|[CObList::GetTailPosition](#gettailposition)|傳回清單的結尾元素的位置。|
|[CObList::InsertAfter](#insertafter)|之後，指定位置插入新項目。|
|[CObList::InsertBefore](#insertbefore)|插入新項目指定的位置之前。|
|[CObList::IsEmpty](#isempty)|空白清單條件 （沒有項目） 的測試。|
|[CObList::RemoveAll](#removeall)|從這個清單中移除所有項目。|
|[CObList::RemoveAt](#removeat)|從這個位置所指定的清單中移除項目。|
|[CObList::RemoveHead](#removehead)|移除清單的標頭中的項目。|
|[CObList::RemoveTail](#removetail)|移除清單結尾的項目。|
|[CObList::SetAt](#setat)|設定的項目中指定的位置。|

## <a name="remarks"></a>備註

`CObList` 清單的行為類似雙向連結清單。

位置類型的變數是索引鍵的清單。 迭代器，依序周遊清單作為和書籤，以便保留圖形的位置，您可以使用位置的變數。 位置不是相同的索引，不過。

插入項目是非常快速，在清單開頭、 結尾，在和的已知位置。 值或索引來查閱元素必須循序搜尋。 此搜尋可能會很慢，如果清單很長的。

`CObList` 納入 IMPLEMENT_SERIAL 巨集，以支援序列化和傾印其項目。 如果一份`CObject`指標會儲存至封存，或是利用多載的插入運算子`Serialize`成員函式，每個`CObject`依次序列化項目。

如果您需要個別的傾印`CObject`清單中的項目，您必須將傾印內容的深度大於或等於 1。

當`CObList`物件被刪除，或當其項目會遭到移除，只有`CObject`會移除指標，它們會參考不是物件。

您可以衍生自己的類別，從`CObList`。 新清單類別，設計用來保存衍生自物件的指標`CObject`，加入新的資料成員和新的成員函式。 請注意，產生的清單不完全是型別安全，因為它可讓任何插入`CObject`指標。

> [!NOTE]
>  您必須使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)巨集，如果您想要將清單序列化程式在衍生類別實作中的。

如需有關使用`CObList`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

##  <a name="addhead"></a>  CObList::AddHead

將此清單的標頭中的新項目或項目清單。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>參數

*newElement*<br/>
`CObject`可以加入至這份清單的指標。

*pNewList*<br/>
另一個指標`CObList`清單。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

下表顯示其他成員函式，類似於`CObList::AddHead`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddHead (const CString &** `newElement` **);**<br /><br /> **位置 AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>備註

清單可以是空的作業之前。

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

此程式的結果如下所示：

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>  CObList::AddTail

這份清單的結尾加入新項目或項目清單。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>參數

*newElement*<br/>
`CObject`可以加入至這份清單的指標。

*pNewList*<br/>
另一個指標`CObList`清單。 中的項目*pNewList*會新增至清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

清單可以是空的作業之前。

下表顯示其他成員函式，類似於`CObList::AddTail`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 AddTail (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 AddTail (const CString &** `newElement` **);**<br /><br /> **位置 AddTail (LPCTSTR** `newElement` **);**<br /><br /> **void AddTail (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

此程式的結果如下所示：

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>  CObList::CObList

建構空`CObject`指標清單。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
用於擴充清單的記憶體配置資料粒度。

### <a name="remarks"></a>備註

隨著清單時，配置記憶體的單位*nBlockSize*項目。 如果記憶體配置失敗，`CMemoryException`就會擲回。

下表顯示其他成員函式，類似於`CObList::CObList`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>範例

  以下是 列表`CObject`-衍生的類別`CAge`集合的所有範例中使用：

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

以下是範例`CObList`建構函式使用方式：

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>  CObList::Find

搜尋清單以循序方式來尋找第一個`CObject`符合指定的指標`CObject`指標。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*searchValue*<br/>
要在這份清單中找到的物件指標。

*startAfter*<br/>
搜尋開始位置。

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果找不到物件，則為 NULL。

### <a name="remarks"></a>備註

請注意，比較指標值，而非物件的內容。

下表顯示其他成員函式，類似於`CObList::Find`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置尋找 (void** <strong>\*</strong> `searchValue` **，位置** `startAfter` **= NULL) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置尋找 (LPCTSTR** `searchValue` **，位置** `startAfter` **= NULL) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>  CObList::FindIndex

會使用值*nIndex*為清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要找的清單項目以零為起始的索引。

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果*nIndex*太大。 (如果 framework 會產生判斷提示*nIndex*為負數。)

### <a name="remarks"></a>備註

從清單中，停止上的開頭開始循序掃描*n*個項目。

下表顯示其他成員函式，類似於`CObList::FindIndex`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 FindIndex (INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>  CObList::GetAt

位置類型的變數是索引鍵的清單。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*位置*<br/>
傳回先前的位置值`GetHeadPosition`或`Find`成員函式呼叫。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述[GetHead](#gethead)。

### <a name="remarks"></a>備註

它不相同索引中，而且您無法處理您自己的位置值。 `GetAt` 擷取`CObject`相關聯的指定位置的指標。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

下表顯示其他成員函式，類似於`CObList::GetAt`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt (位置***位置* **) const;**<br /><br /> **void\*& GetAt (位置***位置* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAt (位置***位置* **) const;**<br /><br /> **CString & GetAt (位置***位置* **);**|

### <a name="example"></a>範例

  範例，請參閱[FindIndex](#findindex)。

##  <a name="getcount"></a>  CObList::GetCount

這份清單中取得的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

整數值，其中包含項目計數。

下表顯示其他成員函式，類似於`CObList::GetCount`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; 的 INT_PTR GetCount （)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; 的 INT_PTR GetCount （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>  CObList::GetHead

取得`CObject`指標，表示此清單的標頭的項目。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>傳回值

如果清單透過指標來存取`const CObList`，然後`GetHead`傳回`CObject`指標。 這可讓函式只能用在指派陳述式的右邊，並因此防止修改的清單。

如果清單直接或透過指標存取`CObList`，然後`GetHead`傳回的參考`CObject`指標。 這允許用在指派陳述式的任一邊函式，並因此可讓要修改之清單項目。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

下表顯示其他成員函式，類似於`CObList::GetHead`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead （) const; void\*& GetHead （);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead （) const;CString & GetHead （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

下列範例示範如何將`GetHead`指派陳述式的左邊。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>  CObList::GetHeadPosition

取得此清單的標頭項目的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

下表顯示其他成員函式，類似於`CObList::GetHeadPosition`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; 的位置 GetHeadPosition （)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; 的位置 GetHeadPosition （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>  CObList::GetNext

取得所識別的清單項目*rPosition*，然後設定*rPosition*到`POSITION`下一步 清單中項目的值。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
前一個位置值的參考`GetNext`， `GetHeadPosition`，或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述[GetHead](#gethead)。

### <a name="remarks"></a>備註

您可以使用`GetNext`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetHeadPosition`或`Find`。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，最後一則新值*rPosition*設為 NULL。

您可在反覆運算期間移除項目。 範例，請參閱[RemoveAt](#removeat)。

> [!NOTE]
>  從 MFC 8.0 const 的版本，這個方法已變更為傳回`const CObject*`而不是`const CObject*&`。  這項變更的目的是為了讓編譯器符合 c + + 標準。

下表顯示其他成員函式，類似於`CObList::GetNext`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

此程式的結果如下所示：

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>  CObList::GetPrev

取得所識別的清單項目*rPosition*，然後設定*rPosition*先前的項目清單中的位置值。

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
前一個位置值的參考`GetPrev`或其他成員函式呼叫。

### <a name="return-value"></a>傳回值

請參閱的傳回值描述[GetHead](#gethead)。

### <a name="remarks"></a>備註

您可以使用`GetPrev`反向反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetTailPosition`或`Find`。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

如果擷取的項目是在清單中，第一則新值*rPosition*設為 NULL。

> [!NOTE]
>  從 MFC 8.0 const 的版本，這個方法已變更為傳回`const CObject*`而不是`const CObject*&`。  這項變更的目的是為了讓編譯器符合 c + + 標準。

下表顯示其他成員函式，類似於`CObList::GetPrev`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

此程式的結果如下所示：

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>  CObList::GetSize

傳回清單項目數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數。

### <a name="remarks"></a>備註

呼叫這個方法來擷取在清單中的項目數。

下表顯示其他成員函式，類似於`CObList::GetSize`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; 的 INT_PTR GetSize （)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; 的 INT_PTR GetSize （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>  CObList::GetTail

取得`CObject`指標，表示此清單的結尾項目。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>傳回值

請參閱的傳回值描述[GetHead](#gethead)。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`GetTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

下表顯示其他成員函式，類似於`CObList::GetTail`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail （) const; void\*& GetTail （);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail （) const;CString & GetTail （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>  CObList::GetTailPosition

取得此清單的結尾元素的位置**NULL**如果清單是空的。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

下表顯示其他成員函式，類似於`CObList::GetTailPosition`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; 的位置 GetTailPosition （)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; 的位置 GetTailPosition （)**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>  CObList::InsertAfter

將這份清單的項目之後的指定位置處的項目。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
傳回先前的位置值`GetNext`， `GetPrev`，或`Find`成員函式呼叫。

*newElement*<br/>
要新增至此清單的物件指標。

下表顯示其他成員函式，類似於`CObList::InsertAfter`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertAfter (位置***位置* **，void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertAfter (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertAfter (位置***位置* **，LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>傳回值

這是相同的位置值作為*位置*參數。

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

此程式的結果如下所示：

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>  CObList::InsertBefore

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*位置*<br/>
傳回先前的位置值`GetNext`， `GetPrev`，或`Find`成員函式呼叫。

*newElement*<br/>
要新增至此清單的物件指標。

### <a name="return-value"></a>傳回值

位置值，可用來反覆項目或物件指標擷取、如果清單是空的則為 NULL。

下表顯示其他成員函式，類似於`CObList::InsertBefore`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertBefore (位置***位置* **，void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertBefore (位置***位置* **，const CString &** `newElement` **);**<br /><br /> **位置 InsertBefore (位置***位置* **，LPCTSTR** `newElement` **);**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

此程式的結果如下所示：

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>  CObList::IsEmpty

指出此清單是否包含任何項目。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果這份清單是空的則為非零否則為 0。

下表顯示其他成員函式，類似於`CObList::IsEmpty`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Const; 的 BOOL IsEmpty （)**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const; 的 BOOL IsEmpty （)**|

### <a name="example"></a>範例

  範例，請參閱[RemoveAll](#removeall)。

##  <a name="removeall"></a>  CObList::RemoveAll

從這個清單中移除所有項目，並釋放相關聯`CObList`記憶體。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已經是空的則會不產生任何錯誤。

當您移除項目從`CObList`，從清單中移除物件的指標。 您必須負責刪除物件本身。

下表顯示其他成員函式，類似於`CObList::RemoveAll`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll （);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>  CObList::RemoveAt

從這個清單中移除指定的項目。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*位置*<br/>
要從清單中移除之項目的位置。

### <a name="remarks"></a>備註

當您移除的項目從`CObList`，從清單中移除的物件指標。 您必須負責刪除物件本身。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

下表顯示其他成員函式，類似於`CObList::RemoveAt`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (位置***位置* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (位置***位置* **);**|

### <a name="example"></a>範例

  在清單中的反覆項目時移除一個項目時要小心。 下列範例顯示可保證有效的移除技巧**位置**值[GetNext](#getnext)。

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

此程式的結果如下所示：

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>  CObList::RemoveHead

移除清單的標頭中的項目，並傳回的指標。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>傳回值

`CObject`先前的清單開頭的指標。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveHead`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

下表顯示其他成員函式，類似於`CObList::RemoveHead`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead （);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>  CObList::RemoveTail

移除清單結尾的項目，並傳回的指標。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>傳回值

在清單結尾的物件指標。

### <a name="remarks"></a>備註

您必須確定清單不是空的再呼叫`RemoveTail`。 如果清單是空的 Mfc 程式庫的偵錯版本判斷提示。 使用[IsEmpty](#isempty)若要驗證清單包含項目。

下表顯示其他成員函式，類似於`CObList::RemoveTail`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail （);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail （);**|

### <a name="example"></a>範例

請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>  CObList::SetAt

設定的項目中指定的位置。

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*pos*<br/>
要設定之項目的位置。

*newElement*<br/>
`CObject`寫入清單的指標。

### <a name="remarks"></a>備註

位置類型的變數是索引鍵的清單。 它不相同索引中，而且您無法處理您自己的位置值。 `SetAt` 寫入`CObject`清單中指定位置的指標。

您必須確定您位置的值，代表在清單中的有效位置。 如果無效，偵錯版本的 Mfc 程式庫判斷提示。

下表顯示其他成員函式，類似於`CObList::SetAt`。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (位置** `pos` **，const CString &** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (位置** `pos` **，LPCTSTR** `newElement` **);**|

### <a name="example"></a>範例

  請參閱[CObList::CObList](#coblist)如需清單`CAge`類別。

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

此程式的結果如下所示：

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CStringList 類別](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList 類別](../../mfc/reference/cptrlist-class.md)
