---
title: CMFCPopupMenuBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::AdjustSizeImmediate
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::BuildOrigItems
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::CloseDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ExportToMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::FindDestintationToolBar
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetCurrentMenuImageSize
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetDefaultMenuId
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetLastCommandIndex
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::GetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::ImportFromMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsDropDownListMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsPaletteMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanel
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::IsRibbonPanelInRegularMode
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::LoadFromHash
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::RestoreDelayedSubMenu
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetButtonStyle
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::SetOffset
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::StartPopupMenuTimer
- AFXPOPUPMENUBAR/CMFCPopupMenuBar::m_bDisableSideBarInXPMode
helpviewer_keywords:
- CMFCPopupMenuBar [MFC], AdjustSizeImmediate
- CMFCPopupMenuBar [MFC], BuildOrigItems
- CMFCPopupMenuBar [MFC], CloseDelayedSubMenu
- CMFCPopupMenuBar [MFC], ExportToMenu
- CMFCPopupMenuBar [MFC], FindDestintationToolBar
- CMFCPopupMenuBar [MFC], GetCurrentMenuImageSize
- CMFCPopupMenuBar [MFC], GetDefaultMenuId
- CMFCPopupMenuBar [MFC], GetLastCommandIndex
- CMFCPopupMenuBar [MFC], GetOffset
- CMFCPopupMenuBar [MFC], ImportFromMenu
- CMFCPopupMenuBar [MFC], IsDropDownListMode
- CMFCPopupMenuBar [MFC], IsPaletteMode
- CMFCPopupMenuBar [MFC], IsRibbonPanel
- CMFCPopupMenuBar [MFC], IsRibbonPanelInRegularMode
- CMFCPopupMenuBar [MFC], LoadFromHash
- CMFCPopupMenuBar [MFC], RestoreDelayedSubMenu
- CMFCPopupMenuBar [MFC], SetButtonStyle
- CMFCPopupMenuBar [MFC], SetOffset
- CMFCPopupMenuBar [MFC], StartPopupMenuTimer
- CMFCPopupMenuBar [MFC], m_bDisableSideBarInXPMode
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
ms.openlocfilehash: 931404412d3b30d5352ecd2fabe30f9ec30f2e3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511812"
---
# <a name="cmfcpopupmenubar-class"></a>CMFCPopupMenuBar 類別

內嵌於快顯功能表的功能表列。

## <a name="syntax"></a>語法

```
class CMFCPopupMenuBar : public CMFCToolBar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新計算 窗格的配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|從指定的功能表資源載入的快顯功能表項目。|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|關閉延遲的快顯功能表按鈕。|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|建置從快顯功能表按鈕的功能表。|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|尋找工具列指定的點的所在位置。|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|表示功能表按鈕影像的大小。|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|傳回預設的功能表項目的識別碼。|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|取得最近叫用的功能表命令的索引。|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|取得快顯功能表列的資料列位移。|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|匯入快顯功能表按鈕，從指定的功能表。|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指出是否在下拉式清單清單模式快顯功能表列。|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|表示快顯功能表列是否為調色盤模式。|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指出這是否為功能區面板 (預設為 FALSE)。|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指出這是否為功能區面板，以一般模式 (預設為 FALSE)。|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|載入已封存的功能表。|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|還原延遲的功能表按鈕來關閉快顯功能表列。|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|設定指定索引處的工具列按鈕的樣式。 (覆寫[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|設定快顯功能表列的資料列的位移。|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|啟動指定的延遲快顯功能表按鈕的計時器。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCPopupMenuBar::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定應用程式具有 Windows XP 外觀時，是否會顯示灰色提要欄位。|

## <a name="remarks"></a>備註

`CMFCPopupMenuBar`建立與同時[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)和內嵌在其中。 `CMFCPopupMenuBar`涵蓋整個工作區`CMFCPopupMenu`物件。 它支援鍵盤和滑鼠輸入。 它也會進行通訊的輸入要`CMFCPopupMenu`和最上層框架視窗。

## <a name="example"></a>範例

下列範例示範如何初始化`CMFCPopupMenuBar`物件從`CMFCPopupMenu`物件。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpopupmenubar.h

##  <a name="adjustsizeimmediate"></a>  CMFCPopupMenuBar::AdjustSizeImmediate

立即重新計算快顯功能表列 窗格的配置。 (覆寫[CPane::AdjustSizeImmediate](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>參數

*bRecalcLayout*<br/>
[in]自動重新計算的快顯功能表列 窗格中，版面配置，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="buildorigitems"></a>  CMFCPopupMenuBar::BuildOrigItems

從指定的功能表資源載入的快顯功能表項目。

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>參數

*uiMenuResID*<br/>
[in]指定要載入功能表資源的功能表識別碼。

### <a name="return-value"></a>傳回值

如果成功則為 TRUE 或 FALSE，否則會傳回。

### <a name="remarks"></a>備註

##  <a name="closedelayedsubmenu"></a>  CMFCPopupMenuBar::CloseDelayedSubMenu

關閉已延遲的快顯功能表按鈕。

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>備註

##  <a name="exporttomenu"></a>  CMFCPopupMenuBar::ExportToMenu

建置從快顯功能表按鈕的功能表。

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>傳回值

傳回新的功能表的控制代碼。

### <a name="remarks"></a>備註

##  <a name="finddestintationtoolbar"></a>  CMFCPopupMenuBar::FindDestintationToolBar

尋找工具列指定的點的所在位置。

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>參數

*點*<br/>
[in]在螢幕上的點。

### <a name="return-value"></a>傳回值

傳回的控制代碼工具列點所在的位置，如果有的話，或如果不為 NULL。

### <a name="remarks"></a>備註

##  <a name="getcurrentmenuimagesize"></a>  CMFCPopupMenuBar::GetCurrentMenuImageSize

表示功能表按鈕影像的大小。

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>傳回值

傳回在工具列中的功能表按鈕影像的大小。

### <a name="remarks"></a>備註

##  <a name="getdefaultmenuid"></a>  CMFCPopupMenuBar::GetDefaultMenuId

傳回預設的功能表項目的識別碼。

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>傳回值

在快顯功能表列中會傳回預設的功能表項目的識別碼。

### <a name="remarks"></a>備註

##  <a name="getlastcommandindex"></a>  CMFCPopupMenuBar::GetLastCommandIndex

取得最近叫用的功能表命令的索引。

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>傳回值

傳回最後一個功能表命令已叫用的索引。

### <a name="remarks"></a>備註

##  <a name="getoffset"></a>  CMFCPopupMenuBar::GetOffset

取得快顯功能表列的資料列位移。

```
int GetOffset() const;
```

### <a name="return-value"></a>傳回值

傳回快顯功能表列的資料列的位移。

### <a name="remarks"></a>備註

此值會設定使用[CMFCPopupMenuBar::SetOffset](#setoffset)。

##  <a name="importfrommenu"></a>  CMFCPopupMenuBar::ImportFromMenu

匯入快顯功能表按鈕，從指定的功能表。

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[in]要從中匯入快顯功能表按鈕功能表。

*bShowAllCommands*<br/>
[in]如果所有功能表命令會匯入，或如果很少使用的項目可能會隱藏則為 FALSE。

### <a name="return-value"></a>傳回值

如果功能表按鈕已成功匯入從功能表中或 false 不，傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="isdropdownlistmode"></a>  CMFCPopupMenuBar::IsDropDownListMode

指出是否在下拉式清單清單模式快顯功能表列。

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>傳回值

如果快顯功能表列不是在下拉式清單清單模式中或 false，則傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="ispalettemode"></a>  CMFCPopupMenuBar::IsPaletteMode

表示快顯功能表列是否為調色盤模式。

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>傳回值

如果調色盤模式已啟用，則為 TRUE 或 FALSE，否則會傳回。

### <a name="remarks"></a>備註

當功能表列設定為調色盤模式時，功能表項目會出現在多個資料行和資料列數量有限。

##  <a name="isribbonpanel"></a>  CMFCPopupMenuBar::IsRibbonPanel

指出這是否為功能區面板 (預設為 FALSE)。

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>傳回值

根據預設值，指出這不功能區面板，會傳回 FALSE。

### <a name="remarks"></a>備註

##  <a name="isribbonpanelinregularmode"></a>  CMFCPopupMenuBar::IsRibbonPanelInRegularMode

指出這是否為功能區面板，以一般模式 (預設為 FALSE)。

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>傳回值

根據預設值，指出這不功能區面板以一般模式，會傳回 FALSE。

### <a name="remarks"></a>備註

##  <a name="loadfromhash"></a>  CMFCPopupMenuBar::LoadFromHash

載入已封存的功能表。

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[in]若要載入 [封存] 功能表控制代碼。

### <a name="return-value"></a>傳回值

如果功能表是載入成功，或如果沒有，則為 FALSE，則傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="m_bdisablesidebarinxpmode"></a>  CMFCPopupMenuBar::m_bDisableSideBarInXPMode

布林值參數，指出具有 Windows XP 外觀時，您的應用程式是否有灰色提要欄位。

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>備註

如果此成員變數設定為 FALSE，而且您的應用程式具有 Windows XP 外觀，架構會在您的應用程式中繪製灰色提要欄位。

預設值為 FALSE。

##  <a name="restoredelayedsubmenu"></a>  CMFCPopupMenuBar::RestoreDelayedSubMenu

還原延遲的功能表按鈕來關閉快顯功能表列。

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>備註

##  <a name="setbuttonstyle"></a>  CMFCPopupMenuBar::SetButtonStyle

設定指定索引處的工具列按鈕的樣式。 (覆寫[CMFCToolBar::SetButtonStyle](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle)。)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[in]工具列按鈕的樣式是設為起始的索引。

*nStyle*<br/>
[in]按鈕的樣式。 請參閱[ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)可用工具列按鈕樣式的清單。

### <a name="remarks"></a>備註

##  <a name="setoffset"></a>  CMFCPopupMenuBar::SetOffset

設定快顯功能表列的資料列的位移。

```
void SetOffset(int iOffset);
```

### <a name="parameters"></a>參數

*iOffset*<br/>
[in]快顯功能表列應進行位移的資料列數目。

### <a name="remarks"></a>備註

##  <a name="startpopupmenutimer"></a>  CMFCPopupMenuBar::StartPopupMenuTimer

啟動指定的延遲快顯功能表按鈕的計時器。

```
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>參數

*pMenuButton*<br/>
[in]要設定延遲計時器的 [功能表] 按鈕的指標。

*nDelayFactor*<br/>
[in]延遲因素，等於至少一個要乘以的標準功能表延遲時間 （通常在下半秒，且五秒）。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)
