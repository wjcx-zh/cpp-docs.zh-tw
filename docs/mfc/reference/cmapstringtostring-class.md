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
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370123"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 類別

支援以 `CString` 物件為索引鍵的 `CString` 物件對應。

## <a name="syntax"></a>語法

```
class CMapStringToString : public CObject
```

## <a name="members"></a>成員

的成員`CMapStringToString`函數類似於類[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)的成員函數。 由於此相似性，您可以針對成員函式特性使用 `CMapStringToOb` 參考文件。 只要將`CObject`指標視為返回值或"輸出"函數參數,請替換指向**char**的指標。 無論將`CObject`指標視為"輸入"函數參數,請替換指向**char**的指標。

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

例如，轉換為

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>公共結構

|名稱|描述|
|----------|-----------------|
|[CMapStringtoString::CPair](#cpair)|包含鍵值和關聯字串物件值的嵌套結構。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CmapStringtoString::CmapStringtoString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMapStringtoString::獲取計數](../../mfc/reference/cmapstringtoob-class.md#getcount)|返回此映射中的元素數。|
|[CMapStringtoString::取得哈希表大小](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|確定哈希表中的當前元素數。|
|[CMapStringtoString::獲取NextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|獲取下一個反覆運算元素。|
|[CMapStringtoString::取得大小](../../mfc/reference/cmapstringtoob-class.md#getsize)|返回此映射中的元素數。|
|[CMapStringtoString::取得起始位置](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回第一個元素的位置。|
|[CMapStringtoString::哈希鍵](../../mfc/reference/cmapstringtoob-class.md#hashkey)|計算指定鍵的哈希值。|
|[CMapStringtostring::inithashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|
|[CMapStringtoString::空](../../mfc/reference/cmapstringtoob-class.md#isempty)|測試空映射條件(無元素)。|
|[CMapStringtoString::查找](../../mfc/reference/cmapstringtoob-class.md#lookup)|根據空指標鍵查找空指標。 指標值(而不是它指向的實體)用於鍵比較。|
|[CMapStringtoString::尋找鍵](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回對與指定鍵值關聯的鍵的引用。|
|[CMapStringtoString::P獲取第一assoc](#pgetfirstassoc)|獲取指向地圖中第一`CString`個指標的指標。|
|[CMapStringtoString::P獲取Nextassoc](#pgetnextassoc)|獲取指向下`CString`一個反覆運算的指標。|
|[CMapStringtoString::P查找](#plookup)|返回指向 其`CString`值 與指定值匹配的指標。|
|[CMapStringtoString::刪除所有](../../mfc/reference/cmapstringtoob-class.md#removeall)|從此映射中刪除所有元素。|
|[CMapStringtoString::刪除鍵](../../mfc/reference/cmapstringtoob-class.md#removekey)|刪除由鍵指定的元素。|
|[CMapStringtoString::Setat](../../mfc/reference/cmapstringtoob-class.md#setat)|將元素插入到地圖中;如果找到匹配的鍵,則替換現有元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMapStringtoString::運算子\[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|將元素插入到映射中, 運算子取代`SetAt`。|

## <a name="remarks"></a>備註

`CMapStringToString` 引入 `IMPLEMENT_SERIAL` 巨集，以支援其項目的序列化和傾印。 如果將地圖儲存到存檔中(使用重載插入**<<**( ) 運算子`Serialize`或使用成員函數,則依次序列化每個元素。

如果需要單個`CString`- `CString`元素的轉儲,則必須將轉儲上下文的深度設置為 1 或更大。

刪除`CMapStringToString`物件或刪除其元素時,將根據需要刪除`CString`物件 。

有關的詳細資訊`CMapStringToString`,請參閱文章["集合](../../mfc/collections.md)"。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>需求

**標題:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringtoString::CPair

包含鍵值和關聯的字串物件的值。

### <a name="remarks"></a>備註

這是類[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)中的嵌套結構。

結構由兩個字段組成:

- `key`鍵類型的實際值。

- `value`關聯物件的值。

它用於存儲從[CMapStringToString::P 查找](#plookup)[、CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)和[CMapStringToString::P獲取NextAssoc](#pgetnextassoc)的返回值。

### <a name="example"></a>範例

  有關使用方式的示例,請參閱[CMapStringToString::P 查找](#plookup)"的範例。

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringtoString::P獲取第一assoc

返回地圖物件的第一個條目。

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>傳回值

指向地圖中第一個條目的指標;請參考[CmapStringtoString::CPair](#cpair)。 如果地圖為空,則值為 NULL。

### <a name="remarks"></a>備註

調用此函數以返回地圖物件中第一個元素的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringtoString::P獲取Nextassoc

檢索*由 pAssocRec*指向的地圖元素。

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>參數

*帕索克*<br/>
指向以前[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)調用返回的地圖條目。

### <a name="return-value"></a>傳回值

指向地圖中下一個條目的指標;請參考[CmapStringtoString::CPair](#cpair)。 如果元素是地圖中的最後一個元素,則該值為 NULL。

### <a name="remarks"></a>備註

調用此方法以反覆運算地圖中的所有元素。 使用 調`PGetFirstAssoc`用 檢索第一個元素,然後通過映射遍`PGetNextAssoc`歷對 的調用來反覆運算。

### <a name="example"></a>範例

  請參閱[CMapStringToString::P獲取第一Assoc](#pgetfirstassoc)的範例。

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringtoString::P查找

尋找映射到給定鍵的值。

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>參數

*關鍵*<br/>
指向要搜索的元素的鍵的指標。

### <a name="return-value"></a>傳回值

指向指定鍵的指標。

### <a name="remarks"></a>備註

調用此方法以搜索具有與給定鍵完全匹配的鍵的地圖元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
