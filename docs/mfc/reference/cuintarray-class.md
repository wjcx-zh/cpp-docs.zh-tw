---
title: CUIntArray 類別
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 9d620269bbf6695af992feaf0df2ef1161c9ae8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373246"
---
# <a name="cuintarray-class"></a>CUIntArray 類別

支援不帶正負號整數的陣列。

## <a name="syntax"></a>語法

```
class CUIntArray : public CObject
```

## <a name="members"></a>成員

的成員`CUIntArray`函數類似於類[CObarray](../../mfc/reference/cobarray-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論將`CObject`指標視為函數參數或返回值,請替換 UINT。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CUIntarray:CUIntarray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CUIntarray:新增](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CUIntarray::附加](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CUIntarray:複製](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CUIntarray:元素At](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CUIntarray:免費額外](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CUIntarray:Getat](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CUIntarray:取得計數](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CUIntarray:取得資料](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CUIntarray:取得大小](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CUIntarray:抓取上部](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CUIntarray:插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CUIntarray::空](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CUIntarray:移除所有](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CUIntarray:刪除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CUIntarray:Setat](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CUIntarray:setat增長](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CUIntarray:設定大小](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CUIntarray::運算子\[\]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

無符號整數(UINT)與單詞和雙字不同,因為 UINT 的物理大小可能會根據目標操作環境而變化。 UINT 的大小與雙字相同。

`CUIntArray`合併[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)宏以支援執行時類型存取和轉儲到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件。 如果需要單個未簽名整數元素的轉儲,則必須將轉儲上下文的深度設置為 1 或更大。 無法序列化無符號整陣列。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

有關使用`CUIntArray`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
