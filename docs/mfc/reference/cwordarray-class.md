---
title: CWordArray 類別
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CWordArray::CWordArray
- AFXCOLL/CWordArray::Add
- AFXCOLL/CWordArray::Append
- AFXCOLL/CWordArray::Copy
- AFXCOLL/CWordArray::ElementAt
- AFXCOLL/CWordArray::FreeExtra
- AFXCOLL/CWordArray::GetAt
- AFXCOLL/CWordArray::GetCount
- AFXCOLL/CWordArray::GetData
- AFXCOLL/CWordArray::GetSize
- AFXCOLL/CWordArray::GetUpperBound
- AFXCOLL/CWordArray::InsertAt
- AFXCOLL/CWordArray::IsEmpty
- AFXCOLL/CWordArray::RemoveAll
- AFXCOLL/CWordArray::RemoveAt
- AFXCOLL/CWordArray::SetAt
- AFXCOLL/CWordArray::SetAtGrow
- AFXCOLL/CWordArray::SetSize
helpviewer_keywords:
- CWordArray [MFC], CWordArray
- CWordArray [MFC], Add
- CWordArray [MFC], Append
- CWordArray [MFC], Copy
- CWordArray [MFC], ElementAt
- CWordArray [MFC], FreeExtra
- CWordArray [MFC], GetAt
- CWordArray [MFC], GetCount
- CWordArray [MFC], GetData
- CWordArray [MFC], GetSize
- CWordArray [MFC], GetUpperBound
- CWordArray [MFC], InsertAt
- CWordArray [MFC], IsEmpty
- CWordArray [MFC], RemoveAll
- CWordArray [MFC], RemoveAt
- CWordArray [MFC], SetAt
- CWordArray [MFC], SetAtGrow
- CWordArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: 9dfb0b674d52b288ebd05bf7574f1ae05e4ed1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365903"
---
# <a name="cwordarray-class"></a>CWordArray 類別

支援 16 位元字組陣列。

## <a name="syntax"></a>語法

```
class CWordArray : public CObject
```

## <a name="members"></a>成員

的成員`CWordArray`函數類似於類[CObarray](../../mfc/reference/cobarray-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CObArray` 參考文件。 無論在哪裡看到[CObject](../../mfc/reference/cobject-class.md)指標作為函數參數或返回值,請替換 WORD。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

例如，轉換為

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWordArray:CWordarray](../../mfc/reference/cobarray-class.md#cobarray)|建構空陣列。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWordArray:新增](../../mfc/reference/cobarray-class.md#add)|將項目加入至陣列結尾；必要時讓陣列增長。|
|[CWordArray::追加](../../mfc/reference/cobarray-class.md#append)|將其他陣列附加至該陣列；必要時讓陣列成長。|
|[CWordArray:複製](../../mfc/reference/cobarray-class.md#copy)|將其他陣列複製到該陣列；必要時讓陣列成長。|
|[CWordarray::元素](../../mfc/reference/cobarray-class.md#elementat)|傳回陣列中項目指標的臨時參考。|
|[CWordArray::免費額外](../../mfc/reference/cobarray-class.md#freeextra)|釋放超過目前上限的所有未使用記憶體。|
|[CWordarray:取得At](../../mfc/reference/cobarray-class.md#getat)|傳回給定索引的值。|
|[CWordArray:取得計數](../../mfc/reference/cobarray-class.md#getcount)|取得此陣列中項目的數目。|
|[CWordArray:抓取資料](../../mfc/reference/cobarray-class.md#getdata)|容許存取陣列中的項目。 可以是 NULL。|
|[CWordArray:取得 Size](../../mfc/reference/cobarray-class.md#getsize)|取得此陣列中項目的數目。|
|[CWordarray:抓取上部](../../mfc/reference/cobarray-class.md#getupperbound)|傳回最大的有效索引。|
|[CWordarray::插入At](../../mfc/reference/cobarray-class.md#insertat)|在指定索引處插入項目 (或其他陣列中的所有項目)。|
|[CWordarray::是空的](../../mfc/reference/cobarray-class.md#isempty)|判定陣列是否是空的。|
|[CWordarray::刪除所有](../../mfc/reference/cobarray-class.md#removeall)|從此陣列移除所有項目。|
|[CWordarray::刪除At](../../mfc/reference/cobarray-class.md#removeat)|移除特定索引處的項目。|
|[CWordarray:setat](../../mfc/reference/cobarray-class.md#setat)|設定給定索引的值；不容許陣列成長。|
|[CWordarray:setat增長](../../mfc/reference/cobarray-class.md#setatgrow)|設定給定索引的值；必要時讓陣列成長。|
|[CWordArray::設定大小](../../mfc/reference/cobarray-class.md#setsize)|設定此陣列中要包含的項目數目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CWordArray:運算符 &#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|設定或取得指定索引處的項目。|

## <a name="remarks"></a>備註

`CWordArray`合併[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏以支援其元素的序列化和轉儲。 如果將單片語儲存在存檔中,或者使用重載插入運算符或[CObject:序列化](../../mfc/reference/cobject-class.md#serialize)成員函數,則每個元素依次序列化。

> [!NOTE]
> 使用陣列之前，請先使用 `SetSize` 建立其大小，並為其配置記憶體。 如果您未使用 `SetSize`，則將項目加入至陣列會導致其被頻繁地重新配置及複製。 頻繁的重新配置及複製效率不高，且可能會讓記憶體分段。

如果需要陣列中單個元素的轉儲,則必須將轉儲上下文的深度設置為1或更大。

有關使用`CWordArray`的詳細資訊,請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
