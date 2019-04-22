---
title: CStringList 類別
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
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
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 08e481f010be688fb0b9c219caa1954c9960846f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767271"
---
# <a name="cstringlist-class"></a>CStringList 類別

支援 `CString` 物件的清單。

## <a name="syntax"></a>語法

```
class CStringList : public CObject
```

## <a name="members"></a>成員

成員函式`CStringList`類別的成員函式類似[CObList](../../mfc/reference/coblist-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObList` 參考文件。 無論在何處看到`CObject`指標做為傳回的值，取代`CString`(不`CString`指標)。 無論在何處看到`CObject`指標做為函式參數，以取代`LPCTSTR`。

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
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|建構空的清單。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|將 （讓新的標頭） 清單的標頭中的項目 （或另一個清單中的所有項目）。|
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|將 （讓新的結尾） 的清單結尾的項目 （或另一個清單中的所有項目）。|
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|取得指標值所指定項目的位置。|
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|取得項目以零為起始的索引所指定的位置。|
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|取得的項目中指定的位置。|
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|這份清單中傳回的項目數。|
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|傳回 （不能是空的） 清單的標頭的項目。|
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|傳回清單的標頭項目的位置。|
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|取得逐一查看的下一個項目。|
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|取得逐一查看的上一個項目。|
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|這份清單中傳回的項目數。|
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|傳回 （不能是空的） 清單的結尾項目。|
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|傳回清單的結尾元素的位置。|
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|之後，指定位置插入新項目。|
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|插入新項目指定的位置之前。|
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|空白清單條件 （沒有項目） 的測試。|
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|從這個清單中移除所有項目。|
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|從這個位置所指定的清單中移除項目。|
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|移除清單的標頭中的項目。|
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|移除清單結尾的項目。|
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|設定的項目中指定的位置。|

## <a name="remarks"></a>備註

值，這表示字串中的字元會比較而不是字串的位址會完成所有的比較。

`CStringList` 納入 IMPLEMENT_SERIAL 巨集，以支援序列化和傾印其項目。 如果一份`CString`物件會儲存至封存，或是利用多載的插入運算子`Serialize`成員函式，每個`CString`依次序列化項目。

如果您需要個別的傾印`CString`項目，您必須將傾印內容的深度大於或等於 1。

如需有關使用`CStringList`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
