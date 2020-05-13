---
title: CByteArray 類別
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 9da30f6546a69a51c56bf4b27668e1603c13290b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352392"
---
# <a name="cbytearray-class"></a>CByteArray 類別

支援動態位元組陣列。

## <a name="syntax"></a>語法

```
class CByteArray : public CObject
```

## <a name="members"></a>成員

的成員`CByteArray`函數類似於類[CObarray](../../mfc/reference/cobarray-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論將`CObject`指標視為函數參數或返回值,請替換 BYTE。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C位元組陣列:C位元組](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C位元組數組::新增](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CByteArray::追加](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[C 位元組數組:複製](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CBytearray::元素](../../mfc/reference/cobarray-class.md#elementat)|返回對陣列中的位元組的臨時引用。|
|[CBytearray:免費額外](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CBytearray:GetAt](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[C位元組數組:取得計數](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[C 位元組數組:取得資料](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CBytearray:取得 Size](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CBytearray:取得上乘](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[C位元組數組::插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CBytearray::空](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CBytearray::刪除所有](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[C位元組數組::刪除AT](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CBytearray:setat](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CBytearray::Setat增長](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[C位元組陣列::設定大小](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CByteArray::運算子\[\]](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CByteArray`合併IMPLEMENT_SERIAL宏以支援其元素的序列化和轉儲。 如果將位元組儲存在存檔中,無論是使用重載插入 ( **<<**) 運算元還是`Serialize`使用 成員函數,則每個元素依次序列化。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果需要從陣列中的各個元素調試輸出,則必須將`CDumpContext`物件的深度設置為1或更大。

有關使用`CByteArray`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CObArray 類別](../../mfc/reference/cobarray-class.md)
