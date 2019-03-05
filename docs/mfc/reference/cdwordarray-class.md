---
title: CDWordArray 類別
ms.date: 11/04/2016
f1_keywords:
- CDWordArray
- AFXCOLL/CDWordArray
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
ms.assetid: 581be11e-ced6-47d1-8679-e0b8e7d99494
ms.openlocfilehash: 8cc67e62d905710ba5d63bf93c7b8aa1bf50f69c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298566"
---
# <a name="cdwordarray-class"></a>CDWordArray 類別

支援 32 位元雙字組陣列。

## <a name="syntax"></a>語法

```
class CDWordArray : public CObject
```

## <a name="members"></a>成員

成員函式`CDWordArray`類別的成員函式類似[CObArray](../../mfc/reference/cobarray-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論在何處看到`CObject`指標為函式參數或傳回值，取代`DWORD`。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`DWORD CDWordArray::GetAt( int <nIndex> ) const;`

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
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|傳回的位元組陣列中的臨時參考。|
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

`CDWordArray` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果雙字組的陣列儲存封存，不論是使用多載的插入 ( **<<**) 運算子或`Serialize`成員函式，每個項目是，進而，序列化。

> [!NOTE]
>  使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要偵錯輸出陣列中的個別項目，您必須設定的深度`CDumpContext`為 1 或更高的物件。

如需有關使用`CDWordArray`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
