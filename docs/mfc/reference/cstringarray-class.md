---
title: CStringArray 類別
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: 96a272cbbb76b399ed7a3db6848ab3f74a615a38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365993"
---
# <a name="cstringarray-class"></a>CStringArray 類別

支援[CString](../../atl-mfc-shared/using-cstring.md)物件的陣列。

## <a name="syntax"></a>語法

```
class CStringArray : public CObject
```

## <a name="members"></a>成員

的成員`CStringArray`函數類似於類[CObarray](../../mfc/reference/cobarray-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論將`CObject`指標視為返回值,請替換[CString](../../atl-mfc-shared/using-cstring.md)物件(而不是[CString](../../atl-mfc-shared/using-cstring.md)指標)。 無論在何處看到 `CObject` 指標做為函式參數，請取代 `LPCTSTR`。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`CString CStringArray::GetAt( int <nIndex> ) const;`

和

`void SetAt( int <nIndex>, CObject* <newElement> )`

轉換為

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[弦樂::弦樂](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[弦樂::添加](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[弦樂::附加](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[弦樂::複製](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[弦樂::元素At](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[弦樂::免費額外](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[弦樂::取得 At](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[弦樂::取得計數](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[弦樂::取得資料](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是**NULL**。|
|[弦樂::取得 Size](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[弦樂::獲取上線](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[弦樂::插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[弦樂::空](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[弦樂::刪除所有](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[弦樂::刪除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[弦樂::Setat](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[弦樂::Setat增長](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[弦樂::設定大小](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[弦樂::運算子\[\]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CStringArray`合併IMPLEMENT_SERIAL宏以支援其元素的序列化和轉儲。 如果 `CString` 物件的陣列儲存至封存檔，請使用多載插入運算子或 `Serialize` 成員函式，依次對每一個項目進行序列化。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果您需要傾印陣列中的個別字串項目，則您必須將傾印內容的深度設定為 1 或更大。

當刪除 `CString` 陣列，或者移除其項目時，會適當地釋放字串記憶體。

有關使用`CStringArray`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
