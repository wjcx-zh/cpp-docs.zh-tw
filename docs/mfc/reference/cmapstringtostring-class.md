---
title: CMapStringToString 類別
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
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
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
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
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: ed717497866076681e39cdee7803a45eb8e097d3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780362"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 類別

支援以 `CString` 物件為索引鍵的 `CString` 物件對應。

## <a name="syntax"></a>語法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>成員

成員函式`CMapStringToString`類別的成員函式類似[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 無論在何處看到`CObject`指標，傳回值或 [輸出] 函式參數，替代的指標**char**。 無論在何處看到`CObject`指標為 「 輸入 」 的函式參數，以取代指標**char**。

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

例如，轉換為

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

### <a name="public-structures"></a>公用結構

|名稱|描述|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|巢狀的結構，其中包含索引鍵的值和相關聯的字串物件的值。|

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
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|取得第一個指標`CString`對應中。|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|取得下一個指標`CString`來重複。|
|[CMapStringToString::PLookup](#plookup)|將指標傳回至`CString`其值符合指定的值。|
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|此對應中移除所有項目。|
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的項目。|
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|項目插入對應中;如果找到相符的索引鍵，會取代現有的項目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToOb::operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將元素插入到 map — 運算子替代`SetAt`。|

## <a name="remarks"></a>備註

`CMapStringToString` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果對應儲存至封存，不論是使用多載的插入依次序列化每個項目 ( **<<**) 運算子或`Serialize`成員函式。

如果您需要個別的傾印`CString` -  `CString`項目，您必須將傾印內容的深度大於或等於 1。

當`CMapStringToString`物件被刪除，或當其項目會遭到移除，`CString`適當地移除物件。

如需詳細資訊`CMapStringToString`，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h

##  <a name="cpair"></a>  CMapStringToString::CPair

包含索引鍵的值和相關聯的 string 物件的值。

### <a name="remarks"></a>備註

這是在類別內的巢狀的結構[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)。

結構是由兩個欄位所組成：

- `key` 索引鍵類型的實際值。

- `value` 相關聯的物件值。

它用來儲存傳回的值從[CMapStringToString::PLookup](#plookup)， [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)，並[CMapStringToString::PGetNextAssoc](#pgetnextassoc)。

### <a name="example"></a>範例

  如需使用方式的範例，請參閱範例[CMapStringToString::PLookup](#plookup)。

##  <a name="pgetfirstassoc"></a>  CMapStringToString::PGetFirstAssoc

傳回 map 物件的第一個項目。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>傳回值

在對應的第一個項目指標請參閱[CMapStringToString::CPair](#cpair)。 如果 map 是空的則值會是 NULL。

### <a name="remarks"></a>備註

呼叫此函式可傳回指標的第一個元素的 map 物件中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>  CMapStringToString::PGetNextAssoc

擷取所指的地圖元素*pAssocRec*。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>參數

*pAssoc*<br/>
前一個對應項目會指向[PGetNextAssoc](#pgetnextassoc)或是[PGetFirstAssoc](#pgetfirstassoc)呼叫。

### <a name="return-value"></a>傳回值

在對應的下一個項目指標請參閱[CMapStringToString::CPair](#cpair)。 如果對應的最後一個項目，則值會是 NULL。

### <a name="remarks"></a>備註

呼叫這個方法來逐一查看對應中的所有項目。 擷取第一個項目，藉由呼叫`PGetFirstAssoc`，然後逐一對應與後續呼叫`PGetNextAssoc`。

### <a name="example"></a>範例

  範例，請參閱[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)。

##  <a name="plookup"></a>  CMapStringToString::PLookup

查閱對應至指定的索引鍵的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>參數

*key*<br/>
要搜尋項目的索引鍵的指標。

### <a name="return-value"></a>傳回值

指定的索引鍵的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以符合您指定的索引鍵的索引鍵搜尋對應項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
