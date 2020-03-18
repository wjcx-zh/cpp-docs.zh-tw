---
title: CMapPtrToPtr 類別
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::CMapPtrToPtr
- AFXCOLL/CMapPtrToPtr::GetCount
- AFXCOLL/CMapPtrToPtr::GetHashTableSize
- AFXCOLL/CMapPtrToPtr::GetNextAssoc
- AFXCOLL/CMapPtrToPtr::GetSize
- AFXCOLL/CMapPtrToPtr::GetStartPosition
- AFXCOLL/CMapPtrToPtr::HashKey
- AFXCOLL/CMapPtrToPtr::InitHashTable
- AFXCOLL/CMapPtrToPtr::IsEmpty
- AFXCOLL/CMapPtrToPtr::Lookup
- AFXCOLL/CMapPtrToPtr::LookupKey
- AFXCOLL/CMapPtrToPtr::RemoveAll
- AFXCOLL/CMapPtrToPtr::RemoveKey
- AFXCOLL/CMapPtrToPtr::SetAt
helpviewer_keywords:
- CMapPtrToPtr [MFC], CMapPtrToPtr
- CMapPtrToPtr [MFC], GetCount
- CMapPtrToPtr [MFC], GetHashTableSize
- CMapPtrToPtr [MFC], GetNextAssoc
- CMapPtrToPtr [MFC], GetSize
- CMapPtrToPtr [MFC], GetStartPosition
- CMapPtrToPtr [MFC], HashKey
- CMapPtrToPtr [MFC], InitHashTable
- CMapPtrToPtr [MFC], IsEmpty
- CMapPtrToPtr [MFC], Lookup
- CMapPtrToPtr [MFC], LookupKey
- CMapPtrToPtr [MFC], RemoveAll
- CMapPtrToPtr [MFC], RemoveKey
- CMapPtrToPtr [MFC], SetAt
ms.assetid: 23cbbaec-9d64-48f2-92ae-5e24fa64b926
ms.openlocfilehash: b4ae511caab8278daf723bbcb8ffc5d57f5a1cd0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442677"
---
# <a name="cmapptrtoptr-class"></a>CMapPtrToPtr 類別

支援以 void 指標為索引鍵的 void 指標對應。

## <a name="syntax"></a>語法

```
class CMapPtrToPtr : public CObject
```

## <a name="members"></a>成員

`CMapPtrToPtr` 的成員函式類似于[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要您看到 `CObject` 指標做為函式參數或傳回值，請將指標替換為**void**。 只要您看到 `CString` 或**char**指標做為函式參數或傳回值，請**將指標替換**為**void**。

`BOOL CMapPtrToPtr::Lookup( void* <key>, void*& <rValue> ) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapPtrToPtr::CMapPtrToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapPtrToPtr：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回此對應中的元素數目。|
|[CMapPtrToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapPtrToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapPtrToPtr：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回此對應中的元素數目。|
|[CMapPtrToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapPtrToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapPtrToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapPtrToPtr：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件（沒有元素）。|
|[CMapPtrToPtr：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapPtrToPtr：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapPtrToPtr：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|移除這個對應中的所有元素。|
|[CMapPtrToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的元素。|
|[CMapPtrToPtr：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapPtrToPtr：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

`CMapPtrToPtr` 併入 IMPLEMENT_DYNAMIC 宏，以支援執行時間類型存取和傾印至 `CDumpContext` 物件。 如果您需要個別地圖元素（指標值）的傾印，您必須將傾印內容的深度設定為1或更大。

指標指向指標的對應可能不會序列化。

當 `CMapPtrToPtr` 物件被刪除，或當它的項目被移除時，只會移除指標，而非它們參考的實體。

如需 `CMapPtrToPtr`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToPtr`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
