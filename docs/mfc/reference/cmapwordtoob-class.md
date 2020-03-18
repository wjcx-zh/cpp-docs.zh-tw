---
title: CMapWordToOb 類別
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: 80d53f195ba98f853c86a4d9c38fa9fcda52da3b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442578"
---
# <a name="cmapwordtoob-class"></a>CMapWordToOb 類別

支援以 16 位元字組為索引鍵的 `CObject` 指標對應。

## <a name="syntax"></a>語法

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>成員

`CMapWordToOb` 的成員函式類似于[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要您看到 `CString` 或**char**的**const**指標做為函式參數或傳回值，請替代字。

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapWordToOb：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回此對應中的元素數目。|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapWordToOb：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回此對應中的元素數目。|
|[CMapWordToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapWordToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapWordToOb：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件（沒有元素）。|
|[CMapWordToOb：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapWordToOb：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapWordToOb：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|移除這個對應中的所有元素。|
|[CMapWordToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的元素。|
|[CMapWordToOb：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapWordToOb：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

`CMapWordToOb` 包含 IMPLEMENT_SERIAL 宏，以支援其元素的序列化和傾印。 每個專案都會依次序列化，因為會使用多載插入（ **<<** ）運算子或 `Serialize` 成員函式來儲存對應。

如果您需要個別單字 `CObject` 元素的傾印，您必須將傾印內容的深度設定為1或更大。

當 `CMapWordToOb` 物件被刪除，或移除其元素時，就會移除 `CObject` 的指標。 `CObject` 指標所參考的物件並不會遭到終結。

如需 `CMapWordToOb`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
