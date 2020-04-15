---
title: CWinTraits 類別
ms.date: 11/04/2016
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
ms.openlocfilehash: fd73f733e4eff21da92937d1e1b0cce21552a48c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330304"
---
# <a name="cwintraits-class"></a>CWinTraits 類別

此類提供了一種用於標準化創建視窗物件時使用的樣式的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```

#### <a name="parameters"></a>參數

*t_dwStyle*<br/>
默認標準視窗樣式。

*t_dwExStyle*<br/>
默認擴展視窗樣式。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinTraits:獲取WndEx樣式](#getwndexstyle)|(靜態)檢索`CWinTraits`物件的擴展樣式。|
|[CWinTraits:取得溫德風格](#getwndstyle)|(靜態)檢索`CWinTraits`物件的標準樣式。|

## <a name="remarks"></a>備註

此[視窗特徵類](../../atl/understanding-window-traits.md)提供了一種用於標準化用於創建 ATL 視窗物件的樣式的簡單方法。 將此類的專門化用作[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或其他 ATL 視窗類的範本參數,以指定用於該視窗類實例的預設標準和擴展樣式。

如果要提供默認視窗樣式,僅當對[CWindowImpl::create](../../atl/reference/cwindowimpl-class.md#create)調用時未指定其他樣式時,才使用此範本。

ATL 此樣本的三個預先定義的功能為常用的視窗樣式組合:

- `CControlWinTraits`

   專為標準控制視窗而設計。 使用以下標準樣式:WS_CHILD、WS_VISIBLE、WS_CLIPCHILDREN和WS_CLIPSIBLINGS。 沒有擴展樣式。

- `CFrameWinTraits`

   專為標準框架視窗而設計。 使用的標準樣式包括:WS_OVERLAPPEDWINDOW、WS_CLIPCHILDREN 和WS_CLIPSIBLINGS。 使用的擴展樣式包括:WS_EX_APPWINDOW和WS_EX_WINDOWEDGE。

- `CMDIChildWinTraits`

   專為標準 MDI 子視窗而設計。 使用的標準樣式包括:WS_OVERLAPPEDWINDOW、WS_CHILD、WS_VISIBLE、WS_CLIPCHILDREN和WS_CLIPSIBLINGS。 使用的擴展樣式包括:WS_EX_MDICHILD。

如果要確保為視窗類的所有實例設置某些樣式,同時允許基於每個實例設置其他樣式,請使用[CWinTraitsOR。](../../atl/reference/cwintraitsor-class.md)

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits:取得溫德風格

調用此函數以檢索`CWinTraits`物件的標準樣式。

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
用於創建視窗的標準樣式。 如果*dwStyle*為 0,則傳回`t_dwStyle`樣本樣式值 ( ) 。 如果*dwStyle*是非零,則返回*dwStyle。*

### <a name="return-value"></a>傳回值

對象的標準視窗樣式。

## <a name="cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits:獲取WndEx樣式

調用此函數以檢索`CWinTraits`物件的擴展樣式。

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
用於創建視窗的擴展樣式。 如果*dwExStyle*為 0,則傳回`t_dwExStyle`樣本樣式值 ( ) 。 如果*dwExStyle*是非零,則返回*dwExStyle。*

### <a name="return-value"></a>傳回值

對象的擴展視窗樣式。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[瞭解視窗特徵](../../atl/understanding-window-traits.md)
