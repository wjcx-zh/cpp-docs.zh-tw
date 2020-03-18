---
title: CStringList 類別
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 9eb7a713fc02cd3e51135d1985a41688d4c885d9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447556"
---
# <a name="cstringlist-class"></a>CStringList 類別

支援 `CString` 物件的清單。

## <a name="syntax"></a>語法

```
class CStringList : public CObject
```

## <a name="members"></a>成員

`CStringList` 的成員函式類似于[CObList](../../mfc/reference/coblist-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CObList` 參考文件。 只要您看到 `CObject` 指標做為傳回值，請替代 `CString` （而不是 `CString` 指標）。 只要您看到 `CObject` 指標做為函式參數，請取代 `LPCTSTR`。

`CObject*& CObList::GetHead() const;`

例如，轉換為

`CString& CStringList::GetHead() const;`

和

`POSITION AddHead( CObject* <newElement> );`

轉換為

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStringList：： CStringList](../../mfc/reference/coblist-class.md#coblist)|建立空白清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStringList：： AddHead](../../mfc/reference/coblist-class.md#addhead)|將專案（或另一個清單中的所有元素）新增至清單的開頭（建立新的標頭）。|
|[CStringList：： AddTail](../../mfc/reference/coblist-class.md#addtail)|將專案（或另一個清單中的所有專案）新增至清單的結尾（建立新的結尾）。|
|[CStringList：： Find](../../mfc/reference/coblist-class.md#find)|取得指標值所指定之元素的位置。|
|[CStringList：： FindIndex](../../mfc/reference/coblist-class.md#findindex)|取得以零為基底的索引所指定之元素的位置。|
|[CStringList：： GetAt](../../mfc/reference/coblist-class.md#getat)|取得指定位置的元素。|
|[CStringList：： GetCount](../../mfc/reference/coblist-class.md#getcount)|傳回此清單中的元素數目。|
|[CStringList：： GetHead](../../mfc/reference/coblist-class.md#gethead)|傳回清單的標頭元素（不可以是空的）。|
|[CStringList：： GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|傳回清單 head 元素的位置。|
|[CStringList：： GetNext](../../mfc/reference/coblist-class.md#getnext)|取得用於反覆運算的下一個專案。|
|[CStringList：： GetPrev](../../mfc/reference/coblist-class.md#getprev)|取得上一個反覆運算的元素。|
|[CStringList：： GetSize](../../mfc/reference/coblist-class.md#getsize)|傳回此清單中的元素數目。|
|[CStringList：： GetTail](../../mfc/reference/coblist-class.md#gettail)|傳回清單的尾元素（不可以是空的）。|
|[CStringList：： GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|傳回清單結尾元素的位置。|
|[CStringList：： InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|在指定的位置之後插入新的元素。|
|[CStringList：： InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|在指定的位置之前插入新的元素。|
|[CStringList：： IsEmpty](../../mfc/reference/coblist-class.md#isempty)|測試空白清單條件（沒有元素）。|
|[CStringList：： RemoveAll](../../mfc/reference/coblist-class.md#removeall)|移除此清單中的所有元素。|
|[CStringList：： RemoveAt](../../mfc/reference/coblist-class.md#removeat)|從此清單中移除專案（依位置指定）。|
|[CStringList：： RemoveHead](../../mfc/reference/coblist-class.md#removehead)|將專案從清單的開頭移除。|
|[CStringList：： RemoveTail](../../mfc/reference/coblist-class.md#removetail)|從清單的結尾移除元素。|
|[CStringList：： SetAt](../../mfc/reference/coblist-class.md#setat)|設定指定位置的元素。|

## <a name="remarks"></a>備註

所有的比較都是以傳值方式來完成，這表示字串中的字元會進行比較，而不是字串的位址。

`CStringList` 包含 IMPLEMENT_SERIAL 宏，以支援其元素的序列化和傾印。 如果 `CString` 物件的清單是儲存在封存中（使用多載插入運算子或 `Serialize` 成員函式），則會依次序列化每個 `CString` 專案。

如果您需要個別 `CString` 元素的傾印，您必須將傾印內容的深度設定為1或更大。

如需使用 `CStringList`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
