---
title: CMapStringToString 類別
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442589"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 類別

支援以 `CString` 物件為索引鍵的 `CString` 物件對應。

## <a name="syntax"></a>語法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>成員

`CMapStringToString` 的成員函式類似于[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)類別的成員函式。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要您看到 `CObject` 指標做為傳回值或 "output" 函式參數，請將指標替換為**char**。 只要您看到 `CObject` 指標作為「輸入」函式參數，請將指標替換為**char**。

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>公用結構

|名稱|描述|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|包含索引鍵值和相關聯字串物件值的嵌套結構。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringToString：： GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|傳回此對應中的元素數目。|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|判斷雜湊表中目前的元素數目。|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|取得用於反覆運算的下一個專案。|
|[CMapStringToString：： GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|傳回此對應中的元素數目。|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|傳回第一個元素的位置。|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定之索引鍵的雜湊值。|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化雜湊表。|
|[CMapStringToString：： IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空白對應條件（沒有元素）。|
|[CMapStringToString：： Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據 void 指標索引鍵來查閱 void 指標。 指標值（而非其指向的實體）用於索引鍵比較。|
|[CMapStringToString：： LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|傳回與指定之索引鍵值相關聯之索引鍵的參考。|
|[CMapStringToString：:P GetFirstAssoc](#pgetfirstassoc)|取得對應中第一個 `CString` 的指標。|
|[CMapStringToString：:P GetNextAssoc](#pgetnextassoc)|取得下一個反覆運算之 `CString` 的指標。|
|[CMapStringToString：:P 查閱](#plookup)|傳回 `CString` 的指標，其值符合指定的值。|
|[CMapStringToString：： RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|移除這個對應中的所有元素。|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除索引鍵所指定的元素。|
|[CMapStringToString：： SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入至對應中;如果找到相符的索引鍵，則取代現有的元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringToString：： operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將專案插入地圖中，`SetAt`的運算子替代。|

## <a name="remarks"></a>備註

`CMapStringToString` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 每個專案都會依次序列化，因為會使用多載插入（ **<<** ）運算子或 `Serialize` 成員函式來儲存對應。

如果您需要將個別 `CString`的傾印 - `CString` 元素，您必須將傾印內容的深度設定為1或更大。

刪除 `CMapStringToString` 物件或移除其元素時，會適當地移除 `CString` 物件。

如需 `CMapStringToString`的詳細資訊，請參閱文章[集合](../../mfc/collections.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>需求

**標頭：** afxcoll.h。h

##  <a name="cpair"></a>CMapStringToString::CPair

包含索引鍵值和相關聯 string 物件的值。

### <a name="remarks"></a>備註

這是類別[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)內的嵌套結構。

結構是由兩個欄位所組成：

- `key` 金鑰類型的實際值。

- `value` 相關聯物件的值。

它用來儲存來自 CMapStringToString 的傳回值[：:P lookup](#plookup)、 [CMapStringToString：:P getfirstassoc](#pgetfirstassoc)和[CMapStringToString：:P getnextassoc](#pgetnextassoc)。

### <a name="example"></a>範例

  如需用法的範例，請參閱[CMapStringToString：:P lookup](#plookup)的範例。

##  <a name="pgetfirstassoc"></a>CMapStringToString：:P GetFirstAssoc

傳回 map 物件的第一個專案。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>傳回值

對應中第一個專案的指標;請參閱[CMapStringToString：： CPair](#cpair)。 如果對應是空的，則值為 Null。

### <a name="remarks"></a>備註

呼叫此函式可將指標傳回給 map 物件中的第一個元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>CMapStringToString：:P GetNextAssoc

抓取*pAssocRec*所指向的對應元素。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>參數

*pAssoc*<br/>
指向前一個[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)呼叫所傳回的對應專案。

### <a name="return-value"></a>傳回值

對應中下一個專案的指標;請參閱[CMapStringToString：： CPair](#cpair)。 如果元素是對應中的最後一個，則此值為 Null。

### <a name="remarks"></a>備註

呼叫這個方法，即可逐一查看對應中的所有專案。 藉由呼叫來取出第一個專案 `PGetFirstAssoc`，然後使用 `PGetNextAssoc`的後續呼叫逐一查看對應。

### <a name="example"></a>範例

  請參閱[CMapStringToString：:P getfirstassoc](#pgetfirstassoc)的範例。

##  <a name="plookup"></a>CMapStringToString：:P 查閱

查閱對應至指定索引鍵的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>參數

*key*<br/>
要搜尋之元素的索引鍵指標。

### <a name="return-value"></a>傳回值

指定之索引鍵的指標。

### <a name="remarks"></a>備註

呼叫這個方法，以搜尋具有完全符合指定索引鍵之索引鍵的地圖元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
