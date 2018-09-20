---
title: CMap 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8fad9179764c1198cbf9df19478e1ac7936421
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440923"
---
# <a name="cmap-class"></a>CMap 類別

字典集合類別，這個類別會將唯一索引鍵對應至值。

## <a name="syntax"></a>語法

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>參數

*KEY*<br/>
做為對應索引鍵之物件的類別。

*ARG_KEY*<br/>
用於資料類型*金鑰*引數; 通常參考*金鑰*。

*值*<br/>
在對應中儲存之物件的類別。

*ARG_VALUE*<br/>
用於資料類型*值*引數; 通常參考*值*。

## <a name="members"></a>成員

### <a name="public-structures"></a>公用結構

|名稱|描述|
|----------|-----------------|
|[CMap::CPair](#cpair)|巢狀的結構，其中包含索引鍵的值和相關聯之物件的值。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMap::CMap](#cmap)|建構對應值的索引鍵的集合。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMap::GetCount](#getcount)|在此地圖中傳回的項目數。|
|[CMap::GetHashTableSize](#gethashtablesize)|傳回雜湊表中的項目數目。|
|[CMap::GetNextAssoc](#getnextassoc)|取得逐一查看的下一個項目。|
|[CMap::GetSize](#getsize)|在此地圖中傳回的項目數。|
|[CMap::GetStartPosition](#getstartposition)|傳回第一個元素的位置。|
|[CMap::InitHashTable](#inithashtable)|初始化雜湊表，並指定其大小。|
|[CMap::IsEmpty](#isempty)|空白對應條件 （沒有項目） 的測試。|
|[CMap::Lookup](#lookup)|查閱對應至指定的索引鍵的值。|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|傳回的第一個元素的指標。|
|[CMap::PGetNextAssoc](#pgetnextassoc)|取得下一個元素的指標，來重複。|
|[CMap::PLookup](#plookup)|傳回其值符合指定的值的索引鍵的指標。|
|[CMap::RemoveAll](#removeall)|此對應中移除所有項目。|
|[CMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|
|[CMap::SetAt](#setat)|項目插入對應中;如果找到相符的索引鍵，會取代現有的項目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMap::operator]](#operator_at)|將元素插入到 map — 運算子替代`SetAt`。|

## <a name="remarks"></a>備註

一旦您已插入對應的索引鍵 / 值組 （項目），您就可以有效率地擷取，或刪除使用來存取它的金鑰組。 您也可以逐一查看對應中的所有項目。

位置用於替代的存取權的項目類型的變數。 「 記住 」 項目，並逐一查看 map，您可以使用的位置。 您可能會認為此反覆項目是循序的索引鍵值;不存在。 擷取項目的順序為不定。

全域 helper 函式，這個類別呼叫的特定成員函式必須是可自訂的大部分使用`CMap`類別。 請參閱[集合類別 Helper](../../mfc/reference/collection-class-helpers.md)的巨集和全域區段中**MFC 參考 》**。

`CMap` 覆寫[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)支援序列化和傾印其項目。 如果對應儲存封存使用`Serialize`，每個地圖元素會依序序列化。 預設實作`SerializeElements`helper 函式會執行位元的寫入。 如需指標集合項目的序列化的資訊衍生自`CObject`或其他使用者定義型別，請參閱[如何： 建立類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。

如果您需要個別的項目對應 （索引鍵和值） 中的診斷傾印，您必須設定為 1 或更高的傾印內容的深度。

當`CMap`物件被刪除，或當其項目會遭到移除，會移除索引鍵和值。

Map 類別的衍生是類似於清單衍生。 請參閱文章[集合](../../mfc/collections.md)取得的特殊用途清單類別衍生的說明。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="cmap"></a>  CMap::CMap

建構空的對應。

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
指定擴充對應的記憶體配置資料粒度。

### <a name="remarks"></a>備註

隨著對應時，配置記憶體的單位*nBlockSize*項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

##  <a name="cpair"></a>  CMap::CPair

包含索引鍵的值和相關聯之物件的值。

### <a name="remarks"></a>備註

這是在類別內的巢狀的結構[CMap](../../mfc/reference/cmap-class.md)。

結構是由兩個欄位所組成：

- `key` 索引鍵類型的實際值。

- `value` 相關聯的物件值。

它用來儲存傳回的值從[CMap::PLookup](#plookup)， [CMap::PGetFirstAssoc](#pgetfirstassoc)，並[CMap::PGetNextAssoc](#pgetnextassoc)。

### <a name="example"></a>範例

如需使用方式的範例，請參閱範例[CMap::PLookup](#plookup)。

##  <a name="getcount"></a>  CMap::GetCount

擷取在對應中的項目數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

元素數。

### <a name="example"></a>範例

範例，請參閱[CMap::Lookup](#lookup)。

##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize

決定在對應的雜湊資料表中的項目數。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>傳回值

雜湊表中的項目數目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

##  <a name="getnextassoc"></a>  CMap::GetNextAssoc

擷取對應項目，在`rNextPosition`，然後更新`rNextPosition`以指向 map 中的下一個元素。

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*rNextPosition*<br/>
指定前一個位置值的參考`GetNextAssoc`或`GetStartPosition`呼叫。

*KEY*<br/>
指定對應的索引鍵的類型樣板參數。

*rKey*<br/>
指定傳回的索引鍵的擷取的項目。

*值*<br/>
指定的對應值的類型樣板參數。

*rValue*<br/>
指定的擷取的項目傳回的值。

### <a name="remarks"></a>備註

此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。

如果擷取的項目是在對應中，最後則的新值*rNextPosition*設為 NULL。

### <a name="example"></a>範例

範例，請參閱[CMap::SetAt](#setat)。

##  <a name="getsize"></a>  CMap::GetSize

傳回對應項目數目。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

在對應中的項目數目。

### <a name="remarks"></a>備註

呼叫這個方法來擷取在對應中的項目數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="getstartposition"></a>  CMap::GetStartPosition

對應的反覆項目一開始會傳回位置的值可以傳遞至`GetNextAssoc`呼叫。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

位置值，指出逐一查看對應的開始位置或者，如果 map 是空的則為 NULL。

### <a name="remarks"></a>備註

反覆項目序列不是可預測的因此，「 第一個 map 中的元素 「 必須沒有特殊意義。

### <a name="example"></a>範例

範例，請參閱[CMap::SetAt](#setat)。

##  <a name="inithashtable"></a>  CMap::InitHashTable

初始化雜湊表。

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>參數

*hashSize*<br/>
雜湊表中的項目數。

*bAllocNow*<br/>
如果為 TRUE，會配置的雜湊表初始化; 時否則需要時，會配置資料表。

### <a name="remarks"></a>備註

為了達到最佳效能，雜湊資料表大小應該是質數。 為了減少衝突，大小應該大約 20%超過最大預期的資料集。

### <a name="example"></a>範例

範例，請參閱[CMap::Lookup](#lookup)。

##  <a name="isempty"></a>  CMap::IsEmpty

決定是否是空的對應。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

此對應會不包含任何項目; 如果為非零否則為 0。

### <a name="example"></a>範例

範例，請參閱[CMap::RemoveAll](#removeall)。

##  <a name="lookup"></a>  CMap::Lookup

查閱對應至指定的索引鍵的值。

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定的類型樣板參數*金鑰*值。

*key*<br/>
指定識別的項目，是要查閱的索引鍵。

*值*<br/>
指定要查閱之值的類型。

*rValue*<br/>
接收的查閱值。

### <a name="return-value"></a>傳回值

非零值，如果找不到項目;否則為 0。

### <a name="remarks"></a>備註

`Lookup` 若要快速尋找完全符合指定的索引鍵的索引鍵的對應項目，會使用雜湊演算法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="operator_at"></a>  CMap::operator]

方便替代`SetAt`成員函式。

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>參數

*值*<br/>
指定的對應值的類型樣板參數。

*ARG_KEY*<br/>
指定的索引鍵值的類型樣板參數。

*key*<br/>
用來擷取值，從對應的金鑰。

### <a name="remarks"></a>備註

因此可以使用只在指派陳述式 （左值） 的左側。 如果沒有附指定索引鍵的對應項目，則會建立新的項目。

任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。

### <a name="example"></a>範例

範例，請參閱[CMap::Lookup](#lookup)。

##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc

傳回 map 物件的第一個項目。

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>傳回值

在對應的第一個項目指標請參閱[CMap::CPair](#cpair)。 如果對應不包含任何項目，則值會是 NULL。

### <a name="remarks"></a>備註

呼叫此函式可傳回指標的第一個元素的 map 物件中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc

擷取所指的地圖元素*pAssocRec*。

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>參數

*pAssocRet*<br/>
前一個對應項目會指向[PGetNextAssoc](#pgetnextassoc)或是[CMap::PGetFirstAssoc](#pgetfirstassoc)呼叫。

### <a name="return-value"></a>傳回值

在對應的下一個項目指標請參閱[CMap::CPair](#cpair)。 如果對應的最後一個項目，則值會是 NULL。

### <a name="remarks"></a>備註

呼叫這個方法來逐一查看對應中的所有項目。 擷取第一個項目，藉由呼叫`PGetFirstAssoc`，然後逐一對應與後續呼叫`PGetNextAssoc`。

### <a name="example"></a>範例

範例，請參閱[CMap::PGetFirstAssoc](#pgetfirstassoc)。

##  <a name="plookup"></a>  CMap::PLookup

尋找對應到指定的索引鍵的值。

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>參數

*key*<br/>
要搜尋項目的金鑰。

### <a name="return-value"></a>傳回值

指向的索引鍵的結構;請參閱[CMap::CPair](#cpair)。 如果找到相符項目，則`CMap::PLookup`會傳回 NULL。

### <a name="remarks"></a>備註

呼叫這個方法，以符合您指定的索引鍵的索引鍵搜尋對應項目。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

##  <a name="removeall"></a>  CMap::RemoveAll

移除此對應中的所有值，藉由呼叫全域 helper 函式`DestructElements`。

```
void RemoveAll();
```

### <a name="remarks"></a>備註

如果 map 已經是空白，則函式會運作正常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

##  <a name="removekey"></a>  CMap::RemoveKey

查閱對應到所提供的索引鍵; 的對應項目然後，如果找到索引鍵，則移除的項目。

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定的索引鍵類型的樣板參數。

*key*<br/>
要移除之項目的金鑰。

### <a name="return-value"></a>傳回值

如果找到並成功移除項目，非零值。否則為 0。

### <a name="remarks"></a>備註

`DestructElements` Helper 函式用來移除項目。

### <a name="example"></a>範例

範例，請參閱[CMap::SetAt](#setat)。

##  <a name="setat"></a>  CMap::SetAt

若要將項目插入對應中，主要表示。

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定的類型樣板參數*金鑰*參數。

*key*<br/>
指定新項目的索引鍵。

*ARG_VALUE*<br/>
指定的類型樣板參數*newValue*參數。

*newValue*<br/>
指定新項目的值。

### <a name="remarks"></a>備註

首先，索引鍵查閱。 如果找到索引鍵，則會變更對應的值;否則，系統會建立新的索引鍵 / 值組。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
