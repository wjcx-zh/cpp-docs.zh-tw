---
title: CMapPtrToWord 類別
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: eec254852c00e1b7f3a536e4e63c874fd1f3b12a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260461"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord 類別

支援以 void 指標為索引鍵的 16 位元字組對應。

## <a name="syntax"></a>語法

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>成員

成員函式`CMapPtrToWord`類別的成員函式類似[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 無論在何處看到`CObject`指標做為函式參數或傳回值，取代文字。 無論在何處看到`CString`或**const**指標**char**身為函式參數或傳回值，替換成指向**void**。

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

例如，轉換為

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|在此地圖中傳回的項目數。|
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷目前的雜湊表中的元素數目。|
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得逐一查看的下一個項目。|
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|在此地圖中傳回的項目數。|
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定的索引鍵的雜湊值。|
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|空白對應條件 （沒有項目） 的測試。|
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查閱根據 void 指標的索引鍵的 void 指標。 指標值，而不將它指向，實體用於索引鍵的比較。|
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定的索引鍵值相關聯的索引鍵的參考。|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此對應中移除所有項目。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的項目。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|項目插入對應中;如果找到相符的索引鍵，會取代現有的項目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將元素插入到 map — 運算子替代`SetAt`。|

## <a name="remarks"></a>備註

`CMapWordToPtr` 併入 IMPLEMENT_DYNAMIC 巨集，以支援執行階段類型存取和傾印`CDumpContext`物件。 如果您需要個別地圖元素的傾印，您必須設定為 1 或更高的傾印內容的深度。

無法序列化指標到字組對應。

當`CMapPtrToWord`物件被刪除，或當其項目會遭到移除，會移除指標，而文字。 不會移除索引鍵的指標所參考的實體。

如需詳細資訊`CMapPtrToWord`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
