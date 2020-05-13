---
title: CMap 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: fbb34d4db41ef11cd01a6a8a7f20cafa0e737268
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749070"
---
# <a name="cmap-class"></a>CMap 類別

字典集合類別，這個類別會將唯一索引鍵對應至值。

## <a name="syntax"></a>語法

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>參數

*關鍵*<br/>
用作映射鍵的物件的類。

*ARG_KEY*<br/>
用於*KEY*參數的資料類型;通常參考*KEY*。

*價值*<br/>
存儲在地圖中的物件的類。

*ARG_VALUE*<br/>
用於*VALUE*參數的資料類型;通常參考*VALUE*。

## <a name="members"></a>成員

### <a name="public-structures"></a>公共結構

|名稱|描述|
|----------|-----------------|
|[CMap:CPair](#cpair)|包含鍵值和關聯物件值的嵌套結構。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMap:CMap](#cmap)|構造將鍵映射到值的集合。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMap:取得計數](#getcount)|返回此映射中的元素數。|
|[CMap:取得哈希表大小](#gethashtablesize)|返回哈希表中的元素數。|
|[CMap:取得NextAssoc](#getnextassoc)|獲取下一個反覆運算元素。|
|[CMap:取得大小](#getsize)|返回此映射中的元素數。|
|[CMap:抓取起始位置](#getstartposition)|返回第一個元素的位置。|
|[CMap:inithashTable](#inithashtable)|初始化哈希表並指定其大小。|
|[CMap::空](#isempty)|測試空映射條件(無元素)。|
|[CMap::尋找](#lookup)|尋找映射到給定鍵的值。|
|[CMap::P取得第一Assoc](#pgetfirstassoc)|返回指向第一個元素的指標。|
|[CMap::P獲取NextAssoc](#pgetnextassoc)|獲取指向下一個元素的指標,以便反覆運算。|
|[CMap::P搜尋](#plookup)|返回指向其值與指定值匹配的鍵的指標。|
|[CMap::全部刪除](#removeall)|從此映射中刪除所有元素。|
|[CMap::刪除鍵](#removekey)|刪除由鍵指定的元素。|
|[CMap:setat](#setat)|將元素插入到地圖中;如果找到匹配的鍵,則替換現有元素。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CMap::運算子\[\]](#operator_at)|將元素插入到映射中, 運算子取代`SetAt`。|

## <a name="remarks"></a>備註

將鍵值對(元素)插入到地圖中后,可以使用該鍵有效地檢索或刪除該對。 您還可以反覆運算地圖中的所有元素。

位置類型的變數用於對條目的備用訪問。 您可以使用「位置」來「記住」條目並遍遍地圖。 您可能認為此反覆運算按鍵值順序;因此,您可以認為此反覆運算按鍵值順序進行。它不是。 檢索的元素的順序不確定。

此類的某些成員函數調用全域説明器函數,這些函數必須針對`CMap`類的大多數用途進行自定義。 請參考**MFC 參考**的巨集與全域部分中的[集合類別說明器](../../mfc/reference/collection-class-helpers.md)。

`CMap`覆蓋[CObject::序列化](../../mfc/reference/cobject-class.md#serialize)以支援其元素的序列化和轉儲。 如果使用 將地圖存儲到存`Serialize`檔 ,則依次序列化每個地圖元素。 説明器函數的`SerializeElements`預設實現執行位寫入。 有關派生自`CObject`或其他使用者定義的類型的指標集合項的序列化的資訊,請參閱[如何:創建類型安全集合](../../mfc/how-to-make-a-type-safe-collection.md)。

如果需要對地圖中的各個元素(鍵和值)進行診斷轉儲,則必須將轉儲上下文的深度設置為 1 或更大。

刪除`CMap`物件或刪除其元素時,將刪除鍵和值。

映射類派生類似於清單派生。 有關特殊用途清單類派生的插圖,請參閱文章[「集合](../../mfc/collections.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap:CMap

構造空地圖。

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>參數

*nBlockSize*<br/>
指定用於擴展映射的記憶體分配粒度。

### <a name="remarks"></a>備註

隨著地圖的增長,記憶體以*nBlockSize*條目的單位分配。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap:CPair

包含鍵值和關聯物件的值。

### <a name="remarks"></a>備註

這是類[CMap](../../mfc/reference/cmap-class.md)中的嵌套結構。

結構由兩個字段組成:

- `key`鍵類型的實際值。

- `value`關聯物件的值。

它用於存儲[從 CMap::P 查找](#plookup)[、CMap::PGetFirstAssoc](#pgetfirstassoc)和[CMap::PGetNextAssoc](#pgetnextassoc)的返回值。

### <a name="example"></a>範例

有關使用方式的範例,請參閱[CMap::P 搜尋「的範例](#plookup)。

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap:取得計數

檢索地圖中的元素數。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>傳回值

項目的數目。

### <a name="example"></a>範例

請參閱[CMap::尋找](#lookup)的範例。

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap:取得哈希表大小

確定地圖哈希表中的元素數。

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>傳回值

哈希表中的元素數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap:取得NextAssoc

在 中檢索地圖`rNextPosition`元素 ,`rNextPosition`然後更新 以引用地圖中的下一個元素。

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*r 下一個位置*<br/>
指定對前`GetNextAssoc`一個或多個`GetStartPosition`調用返回的定位值的引用。

*關鍵*<br/>
指定地圖鍵類型的範本參數。

*rKey*<br/>
指定檢索到的元素的返回鍵。

*價值*<br/>
指定地圖值類型的範本參數。

*rValue*<br/>
指定檢索到的元素的返回值。

### <a name="remarks"></a>備註

此函數對於反覆運算地圖中的所有元素最有用。 請注意,位置序列不一定與鍵值序列相同。

如果檢索到的元素是地圖中的最後一個元素,則*rNext定位*的新值將設置為NULL。

### <a name="example"></a>範例

請參閱[CMap::setAt](#setat)的範例。

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap:取得大小

返回地圖元素的數量。

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>傳回值

地圖中的項數。

### <a name="remarks"></a>備註

調用此方法以檢索映射中的元素數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap:抓取起始位置

通過返回可以傳遞給`GetNextAssoc`調用的定位值來啟動映射反覆運算。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>傳回值

指示反覆運算地圖的起始位置的定位值;如果地圖為空,則為 NULL。

### <a name="remarks"></a>備註

反覆運算序列是不可預測的;因此,「地圖中的第一個元素」沒有特殊的意義。

### <a name="example"></a>範例

請參閱[CMap::setAt](#setat)的範例。

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap:inithashTable

初始化哈希表。

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>參數

*哈希*<br/>
哈希表中的條目數。

*巴羅克現在*<br/>
如果為 TRUE,則在初始化時分配哈希表;如果為 TRUE,則在初始化時分配哈希錶。否則,將在需要時分配表。

### <a name="remarks"></a>備註

為了獲得最佳性能,哈希表大小應為質數。 為了盡量減少衝突,大小應比最大預期數據集大大約 20%。

### <a name="example"></a>範例

請參閱[CMap::尋找](#lookup)的範例。

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::空

確定地圖是否為空。

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>傳回值

如果此地圖不包含任何元素,則非零;否則 0。

### <a name="example"></a>範例

請參考[CMap 表示:移除所有](#removeall)。

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::尋找

尋找映射到給定鍵的值。

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定*鍵*值類型的範本參數。

*key*<br/>
指定標識要備份的元素的鍵。

*價值*<br/>
指定要抬頭的值的類型。

*rValue*<br/>
接收上個值。

### <a name="return-value"></a>傳回值

如果找到元素,則非零;否則 0。

### <a name="remarks"></a>備註

`Lookup`使用哈希演演演算法快速查找具有與給定鍵完全匹配的鍵的映射元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::運算符 |

成員函數的`SetAt`方便替代品。

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>參數

*價值*<br/>
指定地圖值類型的範本參數。

*ARG_KEY*<br/>
指定鍵值類型的範本參數。

*key*<br/>
用於從映射檢索值的鍵。

### <a name="remarks"></a>備註

因此,它只能在賦值語句(l值)的左側使用。 如果沒有具有指定鍵的地圖元素,則創建新元素。

沒有等效於此運算符的「右側」(r 值),因為在地圖中可能找不到鍵。 使用`Lookup`成員函數進行元素檢索。

### <a name="example"></a>範例

請參閱[CMap::尋找](#lookup)的範例。

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::P取得第一Assoc

返回地圖物件的第一個條目。

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>傳回值

指向地圖中第一個條目的指標;請參閱[CMap:CPair](#cpair)。 如果地圖不包含條目,則值為 NULL。

### <a name="remarks"></a>備註

調用此函數以返回地圖物件中第一個元素的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::P獲取NextAssoc

檢索*由 pAssocRec*指向的地圖元素。

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>參數

*帕索克雷特*<br/>
指向以前[PGetNextAssoc](#pgetnextassoc)或[CMap::PGetFirstAssoc](#pgetfirstassoc)調用返回的地圖條目。

### <a name="return-value"></a>傳回值

指向地圖中下一個條目的指標;請參閱[CMap:CPair](#cpair)。 如果元素是地圖中的最後一個元素,則該值為 NULL。

### <a name="remarks"></a>備註

調用此方法以反覆運算地圖中的所有元素。 使用 調`PGetFirstAssoc`用 檢索第一個元素,然後通過映射遍`PGetNextAssoc`歷對 的調用來反覆運算。

### <a name="example"></a>範例

請參閱[CMap::P獲取第一Assoc](#pgetfirstassoc)的範例。

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::P搜尋

尋找映射到給定鍵的值。

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>參數

*key*<br/>
要搜索的元素的鍵。

### <a name="return-value"></a>傳回值

指向鍵結構的指標;指向鍵結構的指標請參閱[CMap:CPair](#cpair)。 如果未找到符合項,`CMap::PLookup`則傳回 NULL。

### <a name="remarks"></a>備註

調用此方法以搜索具有與給定鍵完全匹配的鍵的地圖元素。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::全部刪除

通過調用全域説明器函數`DestructElements`從此映射中刪除所有值。

```cpp
void RemoveAll();
```

### <a name="remarks"></a>備註

如果地圖已為空,則函數工作正常。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::刪除鍵

查找與提供的鍵對應的地圖條目;然後,如果找到該鍵,則刪除該條目。

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定鍵類型的範本參數。

*key*<br/>
要刪除的元素的鍵。

### <a name="return-value"></a>傳回值

如果發現並成功刪除條目,則非零;否則 0。

### <a name="remarks"></a>備註

説明`DestructElements`器函數用於刪除條目。

### <a name="example"></a>範例

請參閱[CMap::setAt](#setat)的範例。

## <a name="cmapsetat"></a><a name="setat"></a>CMap:setat

主要是指在地圖中插入元素。

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>參數

*ARG_KEY*<br/>
指定*鍵*參數類型的樣本參數。

*key*<br/>
指定新元素的鍵。

*ARG_VALUE*<br/>
指定*newValue*參數類型的範本參數。

*newValue*<br/>
指定新元素的值。

### <a name="remarks"></a>備註

首先,鍵被抬起來。 如果找到該鍵,則更改相應的值;如果找到該鍵,則更改相應的值。否則將創建新的鍵值對。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品收集](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
