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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416869"
---
# <a name="coblist-class"></a>CObList 類別

fSupports 順序或指標值可存取之非唯一 `CObject` 指標的排序清單。

## <a name="syntax"></a>語法

```
class CObList : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObList：： CObList](#coblist)|為 `CObject` 指標建立空白清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObList：： AddHead](#addhead)|將專案（或另一個清單中的所有元素）新增至清單的開頭（建立新的標頭）。|
|[CObList：： AddTail](#addtail)|將專案（或另一個清單中的所有專案）新增至清單的結尾（建立新的結尾）。|
|[CObList：： Find](#find)|取得指標值所指定之元素的位置。|
|[CObList：： FindIndex](#findindex)|取得以零為基底的索引所指定之元素的位置。|
|[CObList：： GetAt](#getat)|取得指定位置的元素。|
|[CObList：： GetCount](#getcount)|傳回此清單中的元素數目。|
|[CObList：： GetHead](#gethead)|傳回清單的標頭元素（不可以是空的）。|
|[CObList：： GetHeadPosition](#getheadposition)|傳回清單 head 元素的位置。|
|[CObList：： GetNext](#getnext)|取得用於反覆運算的下一個專案。|
|[CObList：： GetPrev](#getprev)|取得上一個反覆運算的元素。|
|[CObList：： GetSize](#getsize)|傳回此清單中的元素數目。|
|[CObList：： GetTail](#gettail)|傳回清單的尾元素（不可以是空的）。|
|[CObList：： GetTailPosition](#gettailposition)|傳回清單結尾元素的位置。|
|[CObList：： InsertAfter](#insertafter)|在指定的位置之後插入新的元素。|
|[CObList：： InsertBefore](#insertbefore)|在指定的位置之前插入新的元素。|
|[CObList：： IsEmpty](#isempty)|測試空白清單條件（沒有元素）。|
|[CObList：： RemoveAll](#removeall)|移除此清單中的所有元素。|
|[CObList：： RemoveAt](#removeat)|從此清單中移除專案（依位置指定）。|
|[CObList：： RemoveHead](#removehead)|將專案從清單的開頭移除。|
|[CObList：： RemoveTail](#removetail)|從清單的結尾移除元素。|
|[CObList：： SetAt](#setat)|設定指定位置的元素。|

## <a name="remarks"></a>備註

`CObList` 清單的行為就像雙向連結清單一樣。

「位置」類型的變數是清單的索引鍵。 您可以使用 POSITION 變數做為反覆運算器，以依序和以書簽的方式來瀏覽清單。 不過，位置與索引並不相同。

在清單標頭、結尾和已知的位置，插入元素非常快速。 依照值或索引來查詢元素時，必須進行順序搜尋。 如果清單很長，則此搜尋可能會變慢。

`CObList` 包含 IMPLEMENT_SERIAL 宏，以支援其元素的序列化和傾印。 如果 `CObject` 的指標清單儲存到封存中（使用多載插入運算子或 `Serialize` 成員函式），則會依次序列化每個 `CObject` 專案。

如果您需要清單中個別 `CObject` 元素的傾印，您必須將傾印內容的深度設定為1或更大。

當 `CObList` 物件被刪除，或移除其元素時，只會移除 `CObject` 指標，而不是它們所參考的物件。

您可以從 `CObList`衍生您自己的類別。 您的新清單類別是為了保存衍生自 `CObject`之物件的指標而設計，會加入新的資料成員和新的成員函式。 請注意，產生的清單並不是嚴格的型別安全，因為它允許插入任何 `CObject` 的指標。

> [!NOTE]
>  如果您想要將清單序列化，您必須在衍生類別的執行中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

如需使用 `CObList`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

##  <a name="addhead"></a>CObList：： AddHead

將新的專案或專案清單加入至此清單的開頭。

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>參數

*newElement*<br/>
要加入至此清單的 `CObject` 指標。

*pNewList*<br/>
另一個 `CObList` 清單的指標。 *PNewList*中的專案將會新增至此清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

下表顯示其他類似 `CObList::AddHead`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead （void** <strong>\*</strong> `newElement` **）;**<br /><br /> **Void AddHead （CPtrList** <strong>\*</strong> `pNewList` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead （Const CString &** `newElement` **）;**<br /><br /> **POSITION AddHead （LPCTSTR** `newElement` **）;**<br /><br /> **Void AddHead （CStringList** <strong>\*</strong> `pNewList` **）;**|

### <a name="remarks"></a>備註

此清單在作業之前可以是空的。

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

此程式的結果如下：

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList：： AddTail

將新的專案或專案清單加入至這個清單的結尾。

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>參數

*newElement*<br/>
要加入至此清單的 `CObject` 指標。

*pNewList*<br/>
另一個 `CObList` 清單的指標。 *PNewList*中的專案將會新增至此清單。

### <a name="return-value"></a>傳回值

第一個版本會傳回新插入之元素的位置值。

### <a name="remarks"></a>備註

此清單在作業之前可以是空的。

下表顯示其他類似 `CObList::AddTail`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail （void** <strong>\*</strong> `newElement` **）;**<br /><br /> **Void AddTail （CPtrList** <strong>\*</strong> `pNewList` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail （Const CString &** `newElement` **）;**<br /><br /> **POSITION AddTail （LPCTSTR** `newElement` **）;**<br /><br /> **Void AddTail （CStringList** <strong>\*</strong> `pNewList` **）;**|

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

此程式的結果如下：

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList：： CObList

建立空的 `CObject` 指標清單。

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
擴充清單的記憶體配置資料細微性。

### <a name="remarks"></a>備註

隨著清單成長，記憶體會以*nBlockSize*專案的單位來配置。 如果記憶體配置失敗，則會擲回 `CMemoryException`。

下表顯示其他類似 `CObList::CObList`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList （INT_PTR** `nBlockSize` **= 10）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList （INT_PTR** `nBlockSize` **= 10）;**|

### <a name="example"></a>範例

  以下是所有集合範例中使用的 `CObject`衍生類別 `CAge` 清單：

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

以下是 `CObList` 的使用方法範例：

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList：： Find

依序搜尋清單，找出符合指定 `CObject` 指標的第一個 `CObject` 指標。

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>參數

*searchValue*<br/>
要在此清單中找到的物件指標。

*startAfter*<br/>
搜尋的開始位置。

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果找不到物件，則為 Null。

### <a name="remarks"></a>備註

請注意，指標值會進行比較，而不是物件的內容。

下表顯示其他類似 `CObList::Find`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置尋找（void** <strong>\*</strong> `searchValue` **，位置**`startAfter` **= Null） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置尋找（LPCTSTR** `searchValue` **，位置**`startAfter` **= Null） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList：： FindIndex

會使用*nIndex*的值當做清單中的索引。

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要尋找之清單元素的以零為起始的索引。

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果*nIndex*太大，則為 Null。 （如果*nIndex*為負數，則架構會產生判斷提示）。

### <a name="remarks"></a>備註

它會從清單的開頭開始進行順序掃描，而在第*n*個元素上停止。

下表顯示其他類似 `CObList::FindIndex`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex （INT_PTR** `nIndex` **） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex （INT_PTR** `nIndex` **） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList：： GetAt

「位置」類型的變數是清單的索引鍵。

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>參數

*position*<br/>
先前 `GetHeadPosition` 或 `Find` 成員函式呼叫所傳回的位置值。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的傳回值描述。

### <a name="remarks"></a>備註

它與索引並不相同，而且您無法自行操作位置值。 `GetAt` 會抓取與指定位置相關聯的 `CObject` 指標。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

下表顯示其他類似 `CObList::GetAt`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAt （位置***位置* **） const;**<br /><br /> **void\*& GetAt （位置***位置* **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Const CString & GetAt （位置***位置* **） const;**<br /><br /> **CString & GetAt （位置***位置* **）;**|

### <a name="example"></a>範例

  請參閱[FindIndex](#findindex)的範例。

##  <a name="getcount"></a>CObList：： GetCount

取得此清單中的元素數目。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

包含元素計數的整數值。

下表顯示其他類似 `CObList::GetCount`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount （） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList：： GetHead

取得表示此清單之 head 元素的 `CObject` 指標。

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>傳回值

如果清單是透過 `const CObList`的指標存取，則 `GetHead` 會傳回 `CObject` 指標。 這可讓函式僅用於指派語句的右邊，因而保護清單不受修改。

如果清單是直接存取，或透過 `CObList`的指標，則 `GetHead` 會傳回 `CObject` 指標的參考。 這可讓函式在指派語句的任一端使用，因此可修改清單專案。

### <a name="remarks"></a>備註

呼叫 `GetHead`之前，您必須先確定清單不是空的。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

下表顯示其他類似 `CObList::GetHead`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead （） const;void\*& GetHead （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead （） const;CString & GetHead （）;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

下列範例說明如何在指派語句的左邊使用 `GetHead`。

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList：： GetHeadPosition

取得此清單之 head 元素的位置。

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果清單是空的，則為 Null。

下表顯示其他類似 `CObList::GetHeadPosition`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition （） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList：： GetNext

取得*rPosition*所識別的清單元素，然後將*rPosition*設定為清單中下一個專案的 `POSITION` 值。

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
先前 `GetNext`、`GetHeadPosition`或其他成員函式呼叫所傳回之位置值的參考。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的傳回值描述。

### <a name="remarks"></a>備註

如果您使用 `GetHeadPosition` 或 `Find`的呼叫來建立初始位置，則可以在正向反復專案迴圈中使用 `GetNext`。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

如果所抓取的專案是清單中的最後一個，則*rPosition*的新值會設為 Null。

可以在反復專案期間移除元素。 請參閱[RemoveAt](#removeat)的範例。

> [!NOTE]
>  從 MFC 8.0 起，此方法的 const 版本已變更為傳回 `const CObject*`，而不是 `const CObject*&`。  這項變更是為了讓編譯器符合C++標準。

下表顯示其他類似 `CObList::GetNext`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

此程式的結果如下：

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList：： GetPrev

取得*rPosition*所識別的清單元素，然後將*rPosition*設定為清單中前一個專案的位置值。

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
先前 `GetPrev` 或其他成員函式呼叫所傳回之位置值的參考。

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的傳回值描述。

### <a name="remarks"></a>備註

如果您在呼叫 `GetTailPosition` 或 `Find`時建立初始位置，可以在反向反復專案迴圈中使用 `GetPrev`。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

如果抓取的專案是清單中的第一個元素，則*rPosition*的新值會設定為 Null。

> [!NOTE]
>  從 MFC 8.0 起，此方法的 const 版本已變更為傳回 `const CObject*`，而不是 `const CObject*&`。  這項變更是為了讓編譯器符合C++標準。

下表顯示其他類似 `CObList::GetPrev`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

此程式的結果如下：

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList：： GetSize

傳回清單元素的數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

清單中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法，以取出清單中的專案數。

下表顯示其他類似 `CObList::GetSize`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize （） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList：： GetTail

取得 `CObject` 指標，表示此清單的尾元素。

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>傳回值

請參閱[GetHead](#gethead)的傳回值描述。

### <a name="remarks"></a>備註

呼叫 `GetTail`之前，您必須先確定清單不是空的。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

下表顯示其他類似 `CObList::GetTail`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail （） const;void\*& GetTail （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail （） const;CString & GetTail （）;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList：： GetTailPosition

取得此清單結尾元素的位置;如果清單是空的，則**為 Null** 。

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果清單是空的，則為 Null。

下表顯示其他類似 `CObList::GetTailPosition`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition （） const;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList：： InsertAfter

在指定位置的專案之後，將元素加入此清單。

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*position*<br/>
先前 `GetNext`、`GetPrev`或 `Find` 成員函式呼叫所傳回的位置值。

*newElement*<br/>
要加入至這個清單的物件指標。

下表顯示其他類似 `CObList::InsertAfter`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertAfter （位置***位置* **、void** <strong>\*</strong> `newElement` **）、**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertAfter （位置***位置* **、const CString &** `newElement` **）;**<br /><br /> **位置 InsertAfter （位置***位置* **、LPCTSTR** `newElement` **）;**|

### <a name="return-value"></a>傳回值

與*position*參數相同的位置值。

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

此程式的結果如下：

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList：： InsertBefore

將項目加入這份清單中相同項目之前的指定位置。

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*position*<br/>
先前 `GetNext`、`GetPrev`或 `Find` 成員函式呼叫所傳回的位置值。

*newElement*<br/>
要加入至這個清單的物件指標。

### <a name="return-value"></a>傳回值

可用於反復專案或物件指標抓取的位置值;如果清單是空的，則為 Null。

下表顯示其他類似 `CObList::InsertBefore`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**位置 InsertBefore （位置***位置* **、void** <strong>\*</strong> `newElement` **）、**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**位置 InsertBefore （位置***位置* **、const CString &** `newElement` **）;**<br /><br /> **位置 InsertBefore （位置***位置* **、LPCTSTR** `newElement` **）;**|

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

此程式的結果如下：

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList：： IsEmpty

指出此清單是否不包含任何元素。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此清單是空的，則為非零;否則為0。

下表顯示其他類似 `CObList::IsEmpty`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty （） const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty （） const;**|

### <a name="example"></a>範例

  請參閱[RemoveAll](#removeall)的範例。

##  <a name="removeall"></a>CObList：： RemoveAll

移除此清單中的所有元素，並釋出相關聯的 `CObList` 記憶體。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果清單已經是空的，就不會產生任何錯誤。

當您從 `CObList`移除元素時，會從清單中移除物件指標。 您必須負責刪除物件本身。

下表顯示其他類似 `CObList::RemoveAll`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll （）;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList：： RemoveAt

從這個清單中移除指定的專案。

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>參數

*position*<br/>
要從清單中移除之元素的位置。

### <a name="remarks"></a>備註

當您從 `CObList`移除元素時，會從清單中移除物件指標。 您必須負責刪除物件本身。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

下表顯示其他類似 `CObList::RemoveAt`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Void RemoveAt （位置***位置* **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Void RemoveAt （位置***位置* **）;**|

### <a name="example"></a>範例

  在清單反復專案中移除專案時，請務必小心。 下列範例顯示可保證[GetNext](#getnext)有效**位置**值的移除技術。

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

此程式的結果如下：

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList：： RemoveHead

將專案從清單的開頭移除，並傳回其指標。

```
CObject* RemoveHead();
```

### <a name="return-value"></a>傳回值

`CObject` 指標先前位於清單的開頭。

### <a name="remarks"></a>備註

呼叫 `RemoveHead`之前，您必須先確定清單不是空的。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

下表顯示其他類似 `CObList::RemoveHead`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead （）;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList：： RemoveTail

從清單的結尾移除元素，並傳回其指標。

```
CObject* RemoveTail();
```

### <a name="return-value"></a>傳回值

位於清單結尾之物件的指標。

### <a name="remarks"></a>備註

呼叫 `RemoveTail`之前，您必須先確定清單不是空的。 如果清單是空的，則 MFC 程式庫判斷提示的 Debug 版本。 使用[IsEmpty](#isempty)來驗證清單是否包含元素。

下表顯示其他類似 `CObList::RemoveTail`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail （）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail （）;**|

### <a name="example"></a>範例

如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList：： SetAt

設定指定位置的元素。

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>參數

*pos*<br/>
要設定之元素的位置。

*newElement*<br/>
要寫入清單的 `CObject` 指標。

### <a name="remarks"></a>備註

「位置」類型的變數是清單的索引鍵。 它與索引並不相同，而且您無法自行操作位置值。 `SetAt` 會將 `CObject` 指標寫入清單中的指定位置。

您必須確定您的位置值代表清單中的有效位置。 如果無效，則 MFC 程式庫判斷提示的 Debug 版本。

下表顯示其他類似 `CObList::SetAt`的成員函式。

|類別|成員函式|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Void SetAt （POSITION** `pos` **，const CString &** `newElement` **）;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Void SetAt （POSITION** `pos` **，LPCTSTR** `newElement` **）;**|

### <a name="example"></a>範例

  如需 `CAge` 類別的清單，請參閱[CObList：： CObList](#coblist) 。

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

此程式的結果如下：

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
