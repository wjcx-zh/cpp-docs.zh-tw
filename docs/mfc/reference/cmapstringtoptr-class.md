---
title: CMapStringToPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToPtr::CMapStringToPtr
- AFXCOLL/CMapStringToPtr::GetCount
- AFXCOLL/CMapStringToPtr::GetHashTableSize
- AFXCOLL/CMapStringToPtr::GetNextAssoc
- AFXCOLL/CMapStringToPtr::GetSize
- AFXCOLL/CMapStringToPtr::GetStartPosition
- AFXCOLL/CMapStringToPtr::HashKey
- AFXCOLL/CMapStringToPtr::InitHashTable
- AFXCOLL/CMapStringToPtr::IsEmpty
- AFXCOLL/CMapStringToPtr::Lookup
- AFXCOLL/CMapStringToPtr::LookupKey
- AFXCOLL/CMapStringToPtr::RemoveAll
- AFXCOLL/CMapStringToPtr::RemoveKey
- AFXCOLL/CMapStringToPtr::SetAt
helpviewer_keywords:
- CMapStringToPtr [MFC], CMapStringToPtr
- CMapStringToPtr [MFC], GetCount
- CMapStringToPtr [MFC], GetHashTableSize
- CMapStringToPtr [MFC], GetNextAssoc
- CMapStringToPtr [MFC], GetSize
- CMapStringToPtr [MFC], GetStartPosition
- CMapStringToPtr [MFC], HashKey
- CMapStringToPtr [MFC], InitHashTable
- CMapStringToPtr [MFC], IsEmpty
- CMapStringToPtr [MFC], Lookup
- CMapStringToPtr [MFC], LookupKey
- CMapStringToPtr [MFC], RemoveAll
- CMapStringToPtr [MFC], RemoveKey
- CMapStringToPtr [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
ms.openlocfilehash: 0e722b305dad6595eb67b1a235c375d21f674353
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442610"
---
# <a name="cmapstringtoptr-class"></a>CMapStringToPtr 類別

支援以 `CString` 物件為索引鍵的 void 指標對應。

## <a name="syntax"></a>語法

```
class CMapStringToPtr : public CObject
```

## <a name="members"></a>成員

`CMapStringToPtr` 的成員函式類似于[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要您看到 `CObject` 指標做為函式參數或傳回值，請將指標替換為**void**。

`BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> ) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapStringToPtr::CMapStringToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToPtr：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回此對應中的元素數目。|
|[CMapStringToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapStringToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapStringToPtr：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回此對應中的元素數目。|
|[CMapStringToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapStringToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapStringToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapStringToPtr：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件（沒有元素）。|
|[CMapStringToPtr：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapStringToPtr：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapStringToPtr：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|移除這個對應中的所有元素。|
|[CMapStringToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的元素。|
|[CMapStringToPtr：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToPtr：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

`CMapStringToPtr` 併入 IMPLEMENT_DYNAMIC 宏，以支援執行時間類型存取和傾印至 `CDumpContext` 物件。 如果您需要個別地圖元素的傾印，您必須將傾印內容的深度設定為1或更大。

字串對指標對應可能不會序列化。

當 `CMapStringToPtr` 物件被刪除，或移除其元素時，就會移除 `CString` 的索引鍵物件和字組。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToPtr`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
