---
title: CFixedStringT 類別
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317832"
---
# <a name="cfixedstringt-class"></a>CFixedStringT 類別

此類表示具有固定字元緩衝區的字串物件。

## <a name="syntax"></a>語法

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>參數

*字串型別*<br/>
用作固定字串物件的基類,可以是任何`CStringT`基於的類型。 一些範例`CString``CStringA`包括`CStringW`與 。

*t_nChars*<br/>
緩衝區中存儲的字元數。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFixedStringT:CFixedStringT](#cfixedstringt)|字串對象的構造函數。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFixedStringT::運算符 |](#operator_eq)|為`CFixedStringT`物件分配新值。|

## <a name="remarks"></a>備註

預設字串類別的樣本`CStringT`。 雖然相似,但兩個類在實現上有所不同。 和`CFixedStringT``CStringT`之間的 主要區別是:

- 初始字元緩衝區作為物件的一部份分配,並且具有*大小t_nChars*。 這允許`CFixedString`物件出於性能目的佔用連續記憶體塊。 但是,如果`CFixedStringT`物件的內容增長到*超出t_nChars,* 則緩衝區將動態分配。

- `CFixedStringT`物件的字元緩衝區的長度始終相同 *(t_nChars*)。 `CStringT`對象的緩衝區大小沒有限制。

- 的`CFixedStringT`記憶體管理員是自定義的,因此不允許在兩個或多個`CFixedStringT`對象之間共用[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)物件。 `CStringT`對象沒有此限制。

有關字串物件的自訂`CFixedStringT`與記憶體管理的詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>需求

**標題:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringT:CFixedStringT

建構 `CFixedStringT` 物件。

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>參數

*皮茨斯爾克*<br/>
要複製到此`CFixedStringT`物件的 null 中止字串。

*斯特斯爾克*<br/>
要複製到`CFixedStringT``CFixedStringT`此物件的現有物件。

*普斯特林姆格*<br/>
指向物件的記憶體管理器的`CFixedStringT`指標。 有關 的詳細`IAtlStringMgr`資訊 和記憶體`CFixedStringT`管理 ,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

### <a name="remarks"></a>備註

由於建構函數將輸入資料複製到新的分配存儲中,因此您應該注意可能會出現記憶體異常。 其中一些構造函數充當轉換函數。

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::運算符 |

使用新資料重新初始化`CFixedStringT`現有物件。

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>參數

*皮茨斯爾克*<br/>
要複製到此`CFixedStringT`物件的 null 中止字串。

*斯特斯爾克*<br/>
要複製到`CFixedStringT`此`CFixedStringT`物件的現有。

### <a name="remarks"></a>備註

您應該注意,每當使用賦值運算符時,都可能發生記憶體異常,因為通常分配新存儲來保存生成的`CFixedStringT`物件。

## <a name="see-also"></a>另請參閱

[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
