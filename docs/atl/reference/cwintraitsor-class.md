---
title: CwinTraitsor 類別
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 825f79190c6f68cd1372154e4e02f430f545aa48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330277"
---
# <a name="cwintraitsor-class"></a>CwinTraitsor 類別

此類提供了一種用於標準化創建視窗物件時使用的樣式的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>參數

*t_dwStyle*<br/>
默認視窗樣式。

*t_dwExStyle*<br/>
默認擴展視窗樣式。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinTraitsOR:獲取WndEx樣式](#getwndexstyle)|檢索`CWinTraitsOR`物件的擴展樣式。|
|[CWinTraitsOR:獲得溫德風格](#getwndstyle)|檢索`CWinTraitsOR`物件的標準樣式。|

## <a name="remarks"></a>備註

此[視窗特徵類](../../atl/understanding-window-traits.md)提供了一種用於標準化用於創建 ATL 視窗物件的樣式的簡單方法。 將此類的專門化用作[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或其他 ATL 視窗類的範本參數,以指定要用於該視窗類實例的最小標準和擴展樣式集。

如果要確保為視窗類的所有實例設置某些樣式,同時允許在調用[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)中按實例設置其他樣式,請使用此範本的專用化。

如果要提供默認視窗樣式,僅當調用`CWindowImpl::Create`中 未指定其他樣式時才會使用,請改用[CWinTraits。](../../atl/reference/cwintraits-class.md)

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR:獲得溫德風格

調用此函數以檢索`CWinTraits`物件的標準樣式和*t_dwStyle*指定的預設樣式的組合(使用邏輯 OR 運算符)。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
用於創建視窗的樣式。

### <a name="return-value"></a>傳回值

使用邏輯 OR 運算子在*dwStyle*中傳遞`t_dwStyle`的樣式 和 指定的預設樣式的組合。

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR:獲取WndEx樣式

呼叫此函數以檢索`CWinTraits`物件擴充樣式和`t_dwStyle`指定的 預設樣式的組合(使用邏輯 OR 運算子)。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
用於創建視窗的擴展樣式。

### <a name="return-value"></a>傳回值

使用邏輯 OR 運算子在*dwExStyle*中`t_dwExStyle`傳遞的擴充 樣式和指定的預設樣式的組合

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[瞭解視窗特徵](../../atl/understanding-window-traits.md)
