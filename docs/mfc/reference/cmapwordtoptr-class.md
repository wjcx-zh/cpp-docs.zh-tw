---
title: CMapWordToPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CMapWordToPtr
- AFXCOLL/CMapWordToPtr
- AFXCOLL/CMapWordToPtr::CMapWordToPtr
- AFXCOLL/CMapWordToPtr::GetCount
- AFXCOLL/CMapWordToPtr::GetHashTableSize
- AFXCOLL/CMapWordToPtr::GetNextAssoc
- AFXCOLL/CMapWordToPtr::GetSize
- AFXCOLL/CMapWordToPtr::GetStartPosition
- AFXCOLL/CMapWordToPtr::HashKey
- AFXCOLL/CMapWordToPtr::InitHashTable
- AFXCOLL/CMapWordToPtr::IsEmpty
- AFXCOLL/CMapWordToPtr::Lookup
- AFXCOLL/CMapWordToPtr::LookupKey
- AFXCOLL/CMapWordToPtr::RemoveAll
- AFXCOLL/CMapWordToPtr::RemoveKey
- AFXCOLL/CMapWordToPtr::SetAt
helpviewer_keywords:
- CMapWordToPtr [MFC], CMapWordToPtr
- CMapWordToPtr [MFC], GetCount
- CMapWordToPtr [MFC], GetHashTableSize
- CMapWordToPtr [MFC], GetNextAssoc
- CMapWordToPtr [MFC], GetSize
- CMapWordToPtr [MFC], GetStartPosition
- CMapWordToPtr [MFC], HashKey
- CMapWordToPtr [MFC], InitHashTable
- CMapWordToPtr [MFC], IsEmpty
- CMapWordToPtr [MFC], Lookup
- CMapWordToPtr [MFC], LookupKey
- CMapWordToPtr [MFC], RemoveAll
- CMapWordToPtr [MFC], RemoveKey
- CMapWordToPtr [MFC], SetAt
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
ms.openlocfilehash: 71d79f9f57be2cdfe16c526bd50173a8ec3c5829
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442570"
---
# <a name="cmapwordtoptr-class"></a>CMapWordToPtr 類別

支援以 16 位元字組為索引鍵的 void 指標對應。

## <a name="syntax"></a>語法

```
class CMapWordToPtr : public CObject
```

## <a name="members"></a>成員

`CMapWordToPtr` 的成員函式類似于[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要您看到 `CObject` 指標做為函式參數或傳回值，請將指標替換為**void**。 只要您看到 `CString` 或**char**的**const**指標做為函式參數或傳回值，請替代字。

`BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapWordToPtr::CMapWordToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapWordToPtr：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回此對應中的元素數目。|
|[CMapWordToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapWordToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapWordToPtr：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回此對應中的元素數目。|
|[CMapWordToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapWordToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapWordToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapWordToPtr：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件（沒有元素）。|
|[CMapWordToPtr：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapWordToPtr：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapWordToPtr：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|移除這個對應中的所有元素。|
|[CMapWordToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的元素。|
|[CMapWordToPtr：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapWordToPtr：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

`CMapWordToPtr` 併入 IMPLEMENT_DYNAMIC 宏，以支援執行時間類型存取和傾印至 `CDumpContext` 物件。 如果您需要個別地圖元素的傾印，您必須將傾印內容的深度設定為1或更大。

文字到指標對應可能無法序列化。

刪除 `CMapWordToPtr` 物件或移除其元素時，會移除單字和指標。 不會移除指標所參考的實體。

如需 `CMapWordToPtr`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToPtr`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
