---
title: CUIntArray 類別
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
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
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 39d5fd4707f1c03de78cf9fd078655389c93ba17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298746"
---
# <a name="cuintarray-class"></a>CUIntArray 類別

支援不帶正負號整數的陣列。

## <a name="syntax"></a>語法

```
class CUIntArray : public CObject
```

## <a name="members"></a>成員

成員函式`CUIntArray`類別的成員函式類似[CObArray](../../mfc/reference/cobarray-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論在何處看到`CObject`指標做為函式參數或傳回值，替換單位。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CObArray::operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

帶正負號的整數或 UINT，不同於字組及雙字組，UINT 的實體大小可以根據作業環境的目標變更。 UINT 是 doubleword 相同的大小。

`CUIntArray` 併入[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)巨集，支援執行階段類型存取和傾印[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。 如果您需要個別的不帶正負號的整數的項目傾印，您必須設定為 1 或更高的傾印內容的深度。 無法序列化不帶正負號的整數陣列。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如需有關使用`CUIntArray`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
