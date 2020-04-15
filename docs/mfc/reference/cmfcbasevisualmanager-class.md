---
title: CMFCBaseVisualManager 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: a3288949bd4867115c32d2cbffd09cf4f7c6b40b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367801"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 類別

派生視覺管理器和 Windows 主題 API 之間的圖層。

`CMFCBaseVisualManager`載入 UxTheme.dll(如果可用)並管理對 Windows 主題 API 方法的訪問。

此類僅供內部使用。

## <a name="syntax"></a>語法

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFCBase視覺化管理員:CMFCBase視覺化管理員](#cmfcbasevisualmanager)|建構並初始化 `CMFCBaseVisualManager` 物件。|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCBase視覺化管理員::D原始檢查盒](#drawcheckbox)|使用當前 Windows 主題繪製複選框控制元件。|
|[CMFCBase可視化管理器::D原始孔博邊界](#drawcomboborder)|使用當前 Windows 主題繪製組合框邊框。|
|[CMFCBase可視化管理員::D原始孔滴按鈕](#drawcombodropbutton)|使用當前 Windows 主題繪製組合框下拉按鈕。|
|[CMFCBase可視化管理員::D原始按鈕](#drawpushbutton)|使用當前 Windows 主題繪製按鈕。|
|[CMFCBase視覺化管理員::D原始無線按鈕](#drawradiobutton)|使用當前 Windows 主題繪製單選按鈕控制元件。|
|[CMFCBase 視覺化管理員::D原始狀態列進度](#drawstatusbarprogress)|使用目前的 Windows 主題在狀態列控制[件 (CMFCStatusBar 類](../../mfc/reference/cmfcstatusbar-class.md)) 上繪製進度條。|
|[CMFCBase可視化管理器::填充鋼筋](#fillrebarpane)|使用當前 Windows 主題填充鋼筋控制元件的背景。|
|[CMFCBase 視覺化管理員:取得標準視窗主題](#getstandardwindowstheme)|獲取當前 Windows 主題。|

### <a name="protected-methods"></a>保護方法

|||
|-|-|
|名稱|描述|
|[CMFCBase可視化管理員::清理主題](#cleanupthemes)|調用`CloseThemeData`在`UpdateSystemColors`中 獲取的所有句柄。|
|[CMFCBase 視覺化管理員:更新系統顏色](#updatesystemcolors)|呼叫`OpenThemeData`以取得用於繪製各種控制的句柄:視窗、工具列、按鈕等。|

## <a name="remarks"></a>備註

您不必直接實例化此類的物件。

因為它是所有可視化管理器的基類,因此只需調用[CMFCVisualManager::getInstance,](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)獲取指向當前可視化管理器的指標,並訪問使用`CMFCBaseVisualManager`該指標的方法。 但是,如果必須使用當前 Windows 主題顯示控制項,最好`CMFCVisualManagerWindows`使用該介面。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase 視覺化管理員](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>需求

**標題:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBase可視化管理員::清理主題

調用`CloseThemeData`在`UpdateSystemColors`中 獲取的所有句柄。

```
void CleanUpThemes();
```

### <a name="remarks"></a>備註

僅供內部使用。

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBase視覺化管理員:CMFCBase視覺化管理員

建構並初始化 `CMFCBaseVisualManager` 物件。

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBase視覺化管理員::D原始檢查盒

使用當前 Windows 主題繪製複選框控制元件。

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向裝置上下文的指標

*矩形*<br/>
[在]複選框的邊界矩形。

*突顯突顯*<br/>
[在]指定此選項是否突出顯示。

*n州*<br/>
[in] 0 表示未選中,1 表示檢查正常,

2 表示混合正常。

*b 啟用*<br/>
[在]指定是否啟用了複選方塊。

*bPressed*<br/>
[在]指定是否按下該複選方塊。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

*nState*的值對應於以下複選框樣式。

|n州|勾選方塊樣式|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBase可視化管理器::D原始孔博邊界

使用當前 Windows 主題繪製組合框邊框。

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]組合框邊框的邊界矩形。

*b 殘疾*<br/>
[在]指定是否關閉組合框邊框。

*bIs放棄*<br/>
[在]指定是否刪除組合框邊框。

*bIs 突顯*<br/>
[在]指定組合框邊框是否突出顯示。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBase可視化管理員::D原始孔滴按鈕

使用當前 Windows 主題繪製組合框下拉按鈕。

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pDC*|[在]指向設備上下文的指標。|
|*矩形*|[在]組合框下拉按鈕的邊界矩形。|
|*b 殘疾*|[在]指定是否關閉組合框下拉按鈕。|
|*bIs放棄*|[在]指定組合框下拉按鈕是否下拉。|
|*bIs 突顯*|[在]指定組合框下拉按鈕是否突出顯示。|

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBase可視化管理員::D原始按鈕

使用當前 Windows 主題繪製按鈕。

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]按鈕的邊界矩形。

*pButton*<br/>
[在]指向要繪製的[CMFCButton 類](../../mfc/reference/cmfcbutton-class.md)物件的指標。

*uiState*<br/>
[在]忽視。 狀態取自*pButton*。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBase視覺化管理員::D原始無線按鈕

使用當前 Windows 主題繪製單選按鈕控制元件。

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]單選按鈕的邊界矩形。

*突顯突顯*<br/>
[在]指定單選按鈕是否突出顯示。

*bChecked*<br/>
[在]指定是否選擇選單選按鈕。

*b 啟用*<br/>
[在]指定是否啟用單選按鈕。

*bPressed*<br/>
[在]指定是否按下單選按鈕。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBase 視覺化管理員::D原始狀態列進度

使用目前的 Windows 主題在狀態列控制[件 (CMFCStatusBar 類](../../mfc/reference/cmfcstatusbar-class.md)) 上繪製進度條。

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*pStatusbar*<br/>
[在]指向狀態列的指標。 這個值會被忽略。

*rectProgress*<br/>
[在]*pDC*座標中進度條的邊界矩形。

*nProgressTotal*<br/>
[在]總進度值。

*nProgressCurr*<br/>
[在]當前進度值。

*clrBar*<br/>
[在]起始顏色。 `CMFCBaseVisualManager`忽略這一點。 派生類可以將其用於顏色漸變。

*clrProgressBarDest*<br/>
[在]結束顏色。 `CMFCBaseVisualManager`忽略這一點。 派生類可以將其用於顏色漸變。

*clrProgressText*<br/>
[在]進度文字顏色。 `CMFCBaseVisualManager`忽略這一點。 文字顏色由`afxGlobalData.clrBtnText`定義 。

*bProgressText*<br/>
[在]指定是否顯示進度文本。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBase可視化管理器::填充鋼筋

使用當前 Windows 主題填充鋼筋控制元件的背景。

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*pBar*<br/>
[在]指向應繪製其背景的窗格的指標。

*rectClient*<br/>
[在]要填充的區域的邊界矩形。

### <a name="return-value"></a>傳回值

如果啟用了主題 API,則為 TRUE;否則 FALSE。

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBase 視覺化管理員:取得標準視窗主題

獲取當前 Windows 主題。

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>傳回值

當前選取的 Windows 主題顏色。 可以是以下枚舉值之一:

- `WinXpTheme_None`- 未啟用主題。

- `WinXpTheme_NonStandard`- 選擇非標準主題(表示選擇主題,但從下面的清單中沒有主題)。

- `WinXpTheme_Blue`- 藍色主題(露娜)。

- `WinXpTheme_Olive`-橄欖主題

- `WinXpTheme_Silver`-銀色主題

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBase 視覺化管理員:更新系統顏色

呼叫`OpenThemeData`以取得用於繪製各種控制的句柄:視窗、工具列、按鈕等。

```
void UpdateSystemColors();
```

### <a name="remarks"></a>備註

僅供內部使用。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
