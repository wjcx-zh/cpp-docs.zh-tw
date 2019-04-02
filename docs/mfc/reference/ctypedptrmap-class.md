---
title: CTypedPtrMap 類別
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: bc164125f867cf3e2f27b74e69b826cbed31ff1d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781792"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap 類別

為指標對應類別 `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`和 `CMapStringToPtr`的物件提供類型安全「包裝函式」。

## <a name="syntax"></a>語法

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
基底類別的具類型的指標對應類別;必須是指標對應類別 ( `CMapPtrToPtr`， `CMapPtrToWord`， `CMapWordToPtr`，或`CMapStringToPtr`)。

*KEY*<br/>
做為對應索引鍵之物件的類別。

*VALUE*<br/>
在對應中儲存之物件的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|取得逐一查看的下一個項目。|
|[CTypedPtrMap::Lookup](#lookup)|傳回`KEY`根據`VALUE`。|
|[CTypedPtrMap::RemoveKey](#removekey)|移除索引鍵所指定的項目。|
|[CTypedPtrMap::SetAt](#setat)|項目插入對應中;如果找到相符的索引鍵，會取代現有的項目。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CTypedPtrMap::operator \[ \]](#operator_at)|將元素插入到 map。|

## <a name="remarks"></a>備註

當您使用`CTypedPtrMap`，c + + 型別檢查功能，有助於排除不相符的指標類型所造成的錯誤。

因為所有`CTypedPtrMap`函式會以內嵌方式，使用此範本不會不會大幅影響的大小或您的程式碼的速度。

如需有關使用`CTypedPtrMap`，請參閱文章[集合](../../mfc/collections.md)並[樣板架構類別](../../mfc/template-based-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>需求

**Header:** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

擷取對應項目，在`rNextPosition`，然後更新`rNextPosition`以指向 map 中的下一個元素。

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*rPosition*<br/>
指定前一個位置值的參考`GetNextAssoc`或是`BASE_CLASS` **:: GetStartPosition**呼叫。

*KEY*<br/>
指定對應的索引鍵的類型樣板參數。

*rKey*<br/>
指定傳回的索引鍵的擷取的項目。

*VALUE*<br/>
指定的對應值的類型樣板參數。

*rValue*<br/>
指定的擷取的項目傳回的值。

### <a name="remarks"></a>備註

此函式是最適合用來逐一查看對應中的所有項目。 請注意，位置順序不一定與索引鍵值順序相同。

如果擷取的項目是在對應中，最後則的新值`rNextPosition`設為 NULL。

此內嵌函式會呼叫`BASE_CLASS` **:: GetNextAssoc**。

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` 快速尋找會確實比對的索引鍵的對應項目，會使用雜湊演算法。

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>參數

*BASE_CLASS*<br/>
指定此對應類別的基底類別的樣板參數。

*key*<br/>
要查閱之項目的索引鍵。

*VALUE*<br/>
指定此對應中所儲存值的類型樣板參數。

*rValue*<br/>
指定的擷取的項目傳回的值。

### <a name="return-value"></a>傳回值

非零值，如果找不到項目;否則為 0。

### <a name="remarks"></a>備註

此內嵌函式會呼叫`BASE_CLASS` **:: 查閱**。

##  <a name="operator_at"></a>  CTypedPtrMap::operator [ ]

此運算子可用僅左邊的指派陳述式 （左值）。

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>參數

*VALUE*<br/>
指定此對應中所儲存值的類型樣板參數。

*BASE_CLASS*<br/>
指定此對應類別的基底類別的樣板參數。

*key*<br/>
要進行查閱，或建立在對應中的項目索引鍵。

### <a name="remarks"></a>備註

如果沒有附指定索引鍵的對應項目，則會建立新的項目。 任何 「 右側 」 （右值） 相當於這個運算子因為沒有索引鍵在對應中找到的可能性。 使用`Lookup`項目擷取的成員函式。

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

此成員函式會呼叫`BASE_CLASS` **:: RemoveKey**。

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>參數

*KEY*<br/>
指定對應的索引鍵的類型樣板參數。

*key*<br/>
要移除之項目的金鑰。

### <a name="return-value"></a>傳回值

如果找到並成功移除項目，非零值。否則為 0。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)。

##  <a name="setat"></a>  CTypedPtrMap::SetAt

此成員函式會呼叫`BASE_CLASS` **:: SetAt**。

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>參數

*KEY*<br/>
指定對應的索引鍵的類型樣板參數。

*key*<br/>
指定的索引鍵值的 newValue。

*newValue*<br/>
指定的物件指標做為新項目的值。

### <a name="remarks"></a>備註

如需詳細註解，請參閱[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)。

## <a name="see-also"></a>另請參閱

[MFC 範例收集](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr 類別](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord 類別](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr 類別](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr 類別](../../mfc/reference/cmapstringtoptr-class.md)
