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
ms.openlocfilehash: 79a3c0945fdd0df04e9ee52d7bad97dc0847fa91
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834293"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager 類別

衍生的視覺管理員和 Windows 主題 API 之間的一層。

`CMFCBaseVisualManager` 載入 UxTheme.dll （如果有的話），並管理 Windows 主題 API 方法的存取權。

這個類別僅供內部使用。

## <a name="syntax"></a>語法

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CMFCBaseVisualManager：： CMFCBaseVisualManager](#cmfcbasevisualmanager)|建構並初始化 `CMFCBaseVisualManager` 物件。|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CMFCBaseVisualManager：:D rawCheckBox](#drawcheckbox)|使用目前的 Windows 主題繪製核取方塊控制項。|
|[CMFCBaseVisualManager：:D rawComboBorder](#drawcomboborder)|使用目前的 Windows 主題繪製下拉式方塊框線。|
|[CMFCBaseVisualManager：:D rawComboDropButton](#drawcombodropbutton)|使用目前的 Windows 主題繪製下拉式方塊下拉式按鈕。|
|[CMFCBaseVisualManager：:D rawPushButton](#drawpushbutton)|使用目前的 Windows 主題繪製推播按鈕。|
|[CMFCBaseVisualManager：:D rawRadioButton](#drawradiobutton)|使用目前的 Windows 主題繪製選項按鈕控制項。|
|[CMFCBaseVisualManager：:D rawStatusBarProgress](#drawstatusbarprogress)|使用目前的 Windows 主題)  ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md) 的狀態列控制項上繪製進度列。|
|[CMFCBaseVisualManager：： FillReBarPane](#fillrebarpane)|使用目前的 Windows 主題，填滿 Rebar 控制項的背景。|
|[CMFCBaseVisualManager：： GetStandardWindowsTheme](#getstandardwindowstheme)|取得目前的 Windows 主題。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|-|-|
|[CMFCBaseVisualManager：： CleanUpThemes](#cleanupthemes)|呼叫 `CloseThemeData` 中取得的所有控制碼 `UpdateSystemColors` 。|
|[CMFCBaseVisualManager：： UpdateSystemColors](#updatesystemcolors)|呼叫 `OpenThemeData` 以取得繪製各種控制項的控點： windows、工具列、按鈕等等。|

## <a name="remarks"></a>備註

您不必直接具現化此類別的物件。

由於它是所有視覺管理員的基類，您只要呼叫 [CMFCVisualManager：： GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance)、取得目前視覺管理員的指標，並存取 `CMFCBaseVisualManager` 使用該指標的方法即可。 但是，如果您必須使用目前的 Windows 主題來顯示控制項，最好是使用 `CMFCVisualManagerWindows` 介面。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxvisualmanager。h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a> CMFCBaseVisualManager：： CleanUpThemes

呼叫 `CloseThemeData` 中取得的所有控制碼 `UpdateSystemColors` 。

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>備註

僅供內部使用。

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a> CMFCBaseVisualManager：： CMFCBaseVisualManager

建構並初始化 `CMFCBaseVisualManager` 物件。

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a> CMFCBaseVisualManager：:D rawCheckBox

使用目前的 Windows 主題繪製核取方塊控制項。

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

*Pdc*<br/>
在裝置內容的指標

*矩形*<br/>
在核取方塊的周框。

*bHighlighted*<br/>
在指定是否要反白顯示覆選框。

*nState*<br/>
[in] 0 表示未核取，1表示已檢查正常，

2用於混合的一般。

*bEnabled*<br/>
在指定是否啟用此核取方塊。

*bPressed*<br/>
在指定是否按下核取方塊。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

*NState*的值會對應至下列核取方塊樣式。

|nState|核取方塊樣式|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a> CMFCBaseVisualManager：:D rawComboBorder

使用目前的 Windows 主題繪製下拉式方塊框線。

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在裝置內容的指標。

*矩形*<br/>
在下拉式方塊框線的周框。

*bDisabled*<br/>
在指定是否停用下拉式列示方塊框線。

*bIsDropped*<br/>
在指定是否要將下拉式方塊框線拖放。

*bIsHighlighted*<br/>
在指定是否反白顯示下拉式列示方塊框線。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a> CMFCBaseVisualManager：:D rawComboDropButton

使用目前的 Windows 主題繪製下拉式方塊下拉式按鈕。

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>參數

*Pdc*\
在裝置內容的指標。

*矩形*\
在下拉式方塊下拉式按鈕的周框。

*bDisabled*\
在指定是否停用下拉式方塊下拉式按鈕。

*bIsDropped*\
在指定下拉式方塊下拉式按鈕是否已中斷。

*bIsHighlighted*\
在指定是否反白顯示下拉式方塊下拉式按鈕。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a> CMFCBaseVisualManager：:D rawPushButton

使用目前的 Windows 主題繪製推播按鈕。

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在裝置內容的指標。

*矩形*<br/>
在推播按鈕的周框。

*pButton*<br/>
在要繪製之 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md) 物件的指標。

*uiState*<br/>
在忽視。 狀態是從 *pButton*取得。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a> CMFCBaseVisualManager：:D rawRadioButton

使用目前的 Windows 主題繪製選項按鈕控制項。

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

*Pdc*<br/>
在裝置內容的指標。

*矩形*<br/>
在選項按鈕的周框。

*bHighlighted*<br/>
在指定是否要反白顯示選項按鈕。

*bChecked*<br/>
在指定是否選取選項按鈕。

*bEnabled*<br/>
在指定是否啟用選項按鈕。

*bPressed*<br/>
在指定是否按下選項按鈕。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a> CMFCBaseVisualManager：:D rawStatusBarProgress

使用目前的 Windows 主題，在狀態列控制項上繪製進度列 ( [CMFCStatusBar 類別](../../mfc/reference/cmfcstatusbar-class.md)) 。

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

*Pdc*<br/>
在裝置內容的指標。

*pStatusBar*<br/>
在狀態列的指標。 這個值會被忽略。

*rectProgress*<br/>
在 *PDC* 座標中進度列的周框。

*nProgressTotal*<br/>
在總進度值。

*nProgressCurr*<br/>
在目前的進度值。

*clrBar*<br/>
在開始色彩。 `CMFCBaseVisualManager` 忽略這個。 衍生類別可以將它用於色彩漸層。

*clrProgressBarDest*<br/>
在結束色彩。 `CMFCBaseVisualManager` 忽略這個。 衍生類別可以將它用於色彩漸層。

*clrProgressText*<br/>
在進度文字色彩。 `CMFCBaseVisualManager` 忽略這個。 文字色彩是由定義 `afxGlobalData.clrBtnText` 。

*bProgressText*<br/>
在指定是否要顯示進度文字。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a> CMFCBaseVisualManager：： FillReBarPane

使用目前的 Windows 主題，填滿 Rebar 控制項的背景。

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>參數

*Pdc*<br/>
在裝置內容的指標。

*pBar*<br/>
在應繪製其背景之窗格的指標。

*rectClient*<br/>
在要填滿之區域的周框。

### <a name="return-value"></a>傳回值

如果啟用主題 API，則為 TRUE;否則為 FALSE。

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a> CMFCBaseVisualManager：： GetStandardWindowsTheme

取得目前的 Windows 主題。

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>傳回值

目前選取的 Windows 主題色彩。 可以是下列其中一個列舉值：

- `WinXpTheme_None` -未啟用任何主題。

- `WinXpTheme_NonStandard` -已選取 [非標準] 主題 (表示已選取主題，但沒有從下列清單中) 。

- `WinXpTheme_Blue` -blue 主題 (Luna) 。

- `WinXpTheme_Olive` -橄欖色主題。

- `WinXpTheme_Silver` -銀色主題。

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a> CMFCBaseVisualManager：： UpdateSystemColors

呼叫 `OpenThemeData` 以取得繪製各種控制項的控點： windows、工具列、按鈕等等。

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>備註

僅供內部使用。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
