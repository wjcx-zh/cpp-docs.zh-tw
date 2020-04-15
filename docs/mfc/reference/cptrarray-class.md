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
ms.openlocfilehash: 7bab68fcbd2cfa4cfe44b0fcd2a1f78af886533d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363985"
---
# <a name="cptrarray-class"></a>CPtrArray 類別

支援 void 指標的陣列。

## <a name="syntax"></a>語法

```
class CPtrArray : public CObject
```

## <a name="members"></a>成員

的成員`CPtrArray`函數類似於類[CObarray](../../mfc/reference/cobarray-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 只要將`CObject`指標視為函數參數或返回值,請替換指向**void 的**指標。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`void* CPtrArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPtrArray:CPtrarray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPtrarray:新增](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CPtrArray::附加](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CPtrArray:複製](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CPtrarray::元素At](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CPtrArray:免費額外](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CPtrarray:GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CPtrarray:取得計數](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CPtrarray:取得資料](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 `NULL`。|
|[CPtrarray:取得 Size](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CPtrarray::取得上流](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CPtrarray::插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CPtrarray::是空的](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CPtrarray::刪除所有](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CPtrarray::刪除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CPtrarray::SetAt](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CPtrarray::SetAt增長](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CPtrarray::設定大小](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPtrArray::運算子\[\]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CPtrArray`合併IMPLEMENT_DYNAMIC宏以支援運行時類型訪問和對`CDumpContext`物件的轉儲。 如果需要單個指標陣列元素的轉儲,則必須將轉儲上下文的深度設置為1或更大。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

指標數組無法序列化。

刪除指標數組或刪除其元素時,將僅刪除指標,而不是刪除它們引用的實體。

有關使用`CPtrArray`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CPtrArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
