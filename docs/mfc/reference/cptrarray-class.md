---
title: CPtrArray 類別
ms.date: 11/04/2016
f1_keywords:
- CPtrArray
- AFXCOLL/CPtrArray
- AFXCOLL/CPtrArray::CPtrArray
- AFXCOLL/CPtrArray::Add
- AFXCOLL/CPtrArray::Append
- AFXCOLL/CPtrArray::Copy
- AFXCOLL/CPtrArray::ElementAt
- AFXCOLL/CPtrArray::FreeExtra
- AFXCOLL/CPtrArray::GetAt
- AFXCOLL/CPtrArray::GetCount
- AFXCOLL/CPtrArray::GetData
- AFXCOLL/CPtrArray::GetSize
- AFXCOLL/CPtrArray::GetUpperBound
- AFXCOLL/CPtrArray::InsertAt
- AFXCOLL/CPtrArray::IsEmpty
- AFXCOLL/CPtrArray::RemoveAll
- AFXCOLL/CPtrArray::RemoveAt
- AFXCOLL/CPtrArray::SetAt
- AFXCOLL/CPtrArray::SetAtGrow
- AFXCOLL/CPtrArray::SetSize
helpviewer_keywords:
- CPtrArray [MFC], CPtrArray
- CPtrArray [MFC], Add
- CPtrArray [MFC], Append
- CPtrArray [MFC], Copy
- CPtrArray [MFC], ElementAt
- CPtrArray [MFC], FreeExtra
- CPtrArray [MFC], GetAt
- CPtrArray [MFC], GetCount
- CPtrArray [MFC], GetData
- CPtrArray [MFC], GetSize
- CPtrArray [MFC], GetUpperBound
- CPtrArray [MFC], InsertAt
- CPtrArray [MFC], IsEmpty
- CPtrArray [MFC], RemoveAll
- CPtrArray [MFC], RemoveAt
- CPtrArray [MFC], SetAt
- CPtrArray [MFC], SetAtGrow
- CPtrArray [MFC], SetSize
ms.assetid: c23b87a3-bf84-49d6-a66b-61e999d0938a
ms.openlocfilehash: 3167c6a388ecbfefce9a72b7bfd720f83639108a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444279"
---
# <a name="cptrarray-class"></a>CPtrArray 類別

支援 void 指標的陣列。

## <a name="syntax"></a>語法

```
class CPtrArray : public CObject
```

## <a name="members"></a>成員

`CPtrArray` 的成員函式類似于[CObArray](../../mfc/reference/cobarray-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 只要您看到 `CObject` 指標做為函式參數或傳回值，請將指標替換為**void**。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPtrArray::CPtrArray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPtrArray：： Add](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CPtrArray：： Append](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CPtrArray：： Copy](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CPtrArray：： Parameters.alternatefilters.elementat](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CPtrArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CPtrArray：： GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CPtrArray：： GetCount](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CPtrArray：：操作](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 `NULL`。|
|[CPtrArray：： GetSize](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CPtrArray：： System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CPtrArray：： InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CPtrArray：： IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CPtrArray：： RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CPtrArray：： RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CPtrArray：： SetAt](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CPtrArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CPtrArray：： SetSize](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPtrArray：： operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CPtrArray` 併入 IMPLEMENT_DYNAMIC 宏，以支援執行時間類型存取和傾印至 `CDumpContext` 物件。 如果您需要個別指標陣列元素的傾印，您必須將傾印內容的深度設定為1或更大。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

無法序列化指標陣列。

當刪除指標陣列，或移除其元素時，只會移除指標，而不是所參考的實體。

如需使用 `CPtrArray`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
