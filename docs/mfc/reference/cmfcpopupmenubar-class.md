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
ms.openlocfilehash: c0ba90246d19e8dd07c856eec6a518a8513ee665
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751916"
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
|[CMFCPopupMenuBar::AdjustSizeImmediate](#adjustsizeimmediate)|立即重新計算窗格的佈局。 (覆蓋[CPane:調整大小立即](../../mfc/reference/cpane-class.md#adjustsizeimmediate).)|
|[CMFCPopupMenuBar::BuildOrigItems](#buildorigitems)|從指定的功能表資源載入彈出功能表項。|
|[CMFCPopupMenuBar::CloseDelayedSubMenu](#closedelayedsubmenu)|關閉延遲的彈出功能表按鈕。|
|[CMFCPopupMenuBar::ExportToMenu](#exporttomenu)|從彈出式功能表按鈕生成功能表。|
|[CMFCPopupMenuBar::FindDestintationToolBar](#finddestintationtoolbar)|尋找指定點所在的工具列。|
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](#getcurrentmenuimagesize)|指示功能表按鈕圖像的大小。|
|[CMFCPopupMenuBar::GetDefaultMenuId](#getdefaultmenuid)|返回預設功能表項的標識碼。|
|[CMFCPopupMenuBar::GetLastCommandIndex](#getlastcommandindex)|獲取最近調用的功能表命令的索引。|
|[CMFCPopupMenuBar::GetOffset](#getoffset)|獲取彈出功能表欄的行偏移量。|
|[CMFCPopupMenuBar::ImportFromMenu](#importfrommenu)|從指定的功能表導入彈出功能表按鈕。|
|[CMFCPopupMenuBar::IsDropDownListMode](#isdropdownlistmode)|指示彈出功能表欄是否處於下拉清單模式。|
|[CMFCPopupMenuBar::IsPaletteMode](#ispalettemode)|指示彈出功能表欄是否處於調色板模式。|
|[CMFCPopupMenuBar::IsRibbonPanel](#isribbonpanel)|指示這是否是功能區面板(預設情況下為 FALSE)。|
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](#isribbonpanelinregularmode)|指示這是否是常規模式下的功能區面板(預設情況下為 FALSE)。|
|[CMFCPopupMenuBar::LoadFromHash](#loadfromhash)|載入存檔的功能表。|
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](#restoredelayedsubmenu)|還原用於關閉彈出功能表欄的延遲功能表按鈕。|
|[CMFCPopupMenuBar::SetButtonStyle](#setbuttonstyle)|設置給定索引處工具列按鈕的樣式。 ( 覆寫[CMFC 工具列:設定按鈕樣式](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)|
|[CMFCPopupMenuBar::SetOffset](#setoffset)|設置彈出功能表欄的行偏移量。|
|[CMFCPopupMenuBar::StartPopupMenuTimer](#startpopupmenutimer)|啟動指定延遲彈出功能表按鈕的計時器。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC彈出功能表欄::m_bDisableSideBarInXPMode](#m_bdisablesidebarinxpmode)|指定當應用程式具有 Windows XP 外觀時,是否將顯示灰色邊欄。|

## <a name="remarks"></a>備註

`CMFCPopupMenuBar`與[CMFCPopupMenu 類](../../mfc/reference/cmfcpopupmenu-class.md)同時創建,並嵌入其中。 覆蓋`CMFCPopupMenuBar``CMFCPopupMenu`物件的整個工作區。 它支援鍵盤和滑鼠輸入。 它還將輸入與 頂層框架`CMFCPopupMenu`視窗和頂部框架視窗通信。

## <a name="example"></a>範例

下面的範例展示如何從`CMFCPopupMenuBar``CMFCPopupMenu`物件初始化物件。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/cpp/cmfcpopupmenubar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

## <a name="requirements"></a>需求

**標題:** afxpopupmenubar.h

## <a name="cmfcpopupmenubaradjustsizeimmediate"></a><a name="adjustsizeimmediate"></a>CMFC彈出選單列::立即調整大小

立即重新計算彈出式功能表欄窗格的佈局。 (覆寫[CPane:調整大小立即](../../mfc/reference/cpane-class.md#adjustsizeimmediate)。

```
virtual void AdjustSizeImmediate(BOOL bRecalcLayout);
```

### <a name="parameters"></a>參數

*bRecalcLayout*<br/>
[在]TRUE 自動重新計算彈出功能表欄窗格的佈局;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarbuildorigitems"></a><a name="buildorigitems"></a>CMFCPopupMenu功能表列::建構Orig專案

從指定的功能表資源載入彈出功能表項。

```
BOOL BuildOrigItems(UINT uiMenuResID);
```

### <a name="parameters"></a>參數

*uiMenuResID*<br/>
[在]指定要載入的功能表資源的功能表 ID。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;如果成功則返回 FALSE;如果成功則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarclosedelayedsubmenu"></a><a name="closedelayedsubmenu"></a>CMFC彈出選單列:關閉延遲的子選單

關閉已延遲的彈出功能表按鈕。

```
virtual void CloseDelayedSubMenu();
```

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarexporttomenu"></a><a name="exporttomenu"></a>CMFCPopupMenu欄::匯出到功能表

從彈出式功能表按鈕生成功能表。

```
virtual HMENU ExportToMenu() const;
```

### <a name="return-value"></a>傳回值

返回新功能表的句柄。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarfinddestintationtoolbar"></a><a name="finddestintationtoolbar"></a>CMFCPopup功能表欄::尋找「選擇工具列」

尋找指定點所在的工具列。

```
CMFCToolBar* FindDestintationToolBar(CPoint point);
```

### <a name="parameters"></a>參數

*點*<br/>
[在]螢幕上的一個點。

### <a name="return-value"></a>傳回值

將句柄返回到點所在的工具列(如果有),或 NULL(如果沒有)。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubargetcurrentmenuimagesize"></a><a name="getcurrentmenuimagesize"></a>CMFCPopup選單列:取得目前選單影像大小

指示功能表按鈕圖像的大小。

```
virtual CSize GetCurrentMenuImageSize() const;
```

### <a name="return-value"></a>傳回值

返回工具列中的功能表按鈕圖像的大小。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubargetdefaultmenuid"></a><a name="getdefaultmenuid"></a>CMFCPopup選單列:取得預設選單Id

返回預設功能表項的標識碼。

```
UINT GetDefaultMenuId() const;
```

### <a name="return-value"></a>傳回值

在彈出式功能表欄中返回預設功能表項的標識碼。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubargetlastcommandindex"></a><a name="getlastcommandindex"></a>CMFCPopupMenu選單列:取得最後命令索引

獲取最近調用的功能表命令的索引。

```
static int __stdcall GetLastCommandIndex();
```

### <a name="return-value"></a>傳回值

返回已調用的最後一個功能表命令的索引。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubargetoffset"></a><a name="getoffset"></a>CMFCPopup功能表列:取得偏移

獲取彈出功能表欄的行偏移量。

```
int GetOffset() const;
```

### <a name="return-value"></a>傳回值

返回彈出功能表欄的行偏移量。

### <a name="remarks"></a>備註

這個值使用[CMFCPopupMenuMenu 欄設定::設定位移](#setoffset)量 。

## <a name="cmfcpopupmenubarimportfrommenu"></a><a name="importfrommenu"></a>CMFC彈出功能表列::從Menu導入

從指定的功能表導入彈出功能表按鈕。

```
virtual BOOL ImportFromMenu(
    HMENU hMenu,
    BOOL bShowAllCommands = FALSE);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[在]要從中導入彈出功能表按鈕的功能表。

*b 顯示所有指令*<br/>
[在]如果要導入功能表上的所有命令,則為 TRUE;如果很少使用命令,則 FALSE 可能會隱藏。

### <a name="return-value"></a>傳回值

如果功能表按鈕已成功從菜單導入,則返回 TRUE;如果功能表按鈕未從菜單中成功導入,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarisdropdownlistmode"></a><a name="isdropdownlistmode"></a>CMFC彈出選單列::是向下清單模式

指示彈出功能表欄是否處於下拉清單模式。

```
BOOL IsDropDownListMode() const;
```

### <a name="return-value"></a>傳回值

如果彈出功能表欄處於下拉清單模式,則返回 TRUE;如果沒有,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarispalettemode"></a><a name="ispalettemode"></a>CMFCPopup功能表列::是調色板模式

指示彈出功能表欄是否處於調色板模式。

```
BOOL IsPaletteMode() const;
```

### <a name="return-value"></a>傳回值

如果啟用了調色板模式,則返回 TRUE;如果未啟用,則返回 FALSE。

### <a name="remarks"></a>備註

當功能表欄設置為調色板模式時,功能表項將顯示在多個列和數量有限的行中。

## <a name="cmfcpopupmenubarisribbonpanel"></a><a name="isribbonpanel"></a>CMFCPopupMenu功能表列::是帶狀面板

指示這是否是功能區面板(預設情況下為 FALSE)。

```
virtual BOOL IsRibbonPanel() const;
```

### <a name="return-value"></a>傳回值

默認情況下返回 FALSE,表示這不是功能區面板。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarisribbonpanelinregularmode"></a><a name="isribbonpanelinregularmode"></a>CMFCPopupMenubar::在常規模式下,是帶彩板

指示這是否是常規模式下的功能區面板(預設情況下為 FALSE)。

```
virtual BOOL IsRibbonPanelInRegularMode() const;
```

### <a name="return-value"></a>傳回值

默認情況下返回 FALSE,表示這不是常規模式下的功能區面板。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarloadfromhash"></a><a name="loadfromhash"></a>CMFCPopupMenuBar::從哈什載入

載入存檔的功能表。

```
BOOL LoadFromHash(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[在]要載入的存檔功能表的句柄。

### <a name="return-value"></a>傳回值

如果功能表已成功載入,則返回 TRUE;如果未載入,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarm_bdisablesidebarinxpmode"></a><a name="m_bdisablesidebarinxpmode"></a>CMFC彈出功能表欄::m_bDisableSideBarInXPMode

Boolean 參數,指示應用程式在具有 Windows XP 外觀時是否有灰色側邊欄。

```
BOOL m_bDisableSideBarInXPMode;
```

### <a name="remarks"></a>備註

如果此成員變數設置為 FALSE,並且應用程式具有 Windows XP 外觀,則框架將繪製應用程式中的灰色側邊欄。

預設值為 FALSE。

## <a name="cmfcpopupmenubarrestoredelayedsubmenu"></a><a name="restoredelayedsubmenu"></a>CMFC彈出功能表列::恢復延遲的子功能表

還原用於關閉彈出功能表欄的延遲功能表按鈕。

```
virtual void RestoreDelayedSubMenu();
```

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CMFC彈出選單列::設定按鈕樣式

設置給定索引處工具列按鈕的樣式。 ( 覆寫[CMFC 工具列:設定按鈕樣式](../../mfc/reference/cmfctoolbar-class.md#setbuttonstyle).)

```
virtual void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
[在]要設置其樣式的工具列按鈕的零基索引。

*nStyle*<br/>
[在]按鈕的樣式。 有關可用工具列按鈕樣式的清單,請參閱[工具列控制元件樣式](../../mfc/reference/toolbar-control-styles.md)。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarsetoffset"></a><a name="setoffset"></a>CMFC彈出功能表列::設置偏移

設置彈出功能表欄的行偏移量。

```cpp
void SetOffset(int iOffset);
```

### <a name="parameters"></a>參數

*i 位移*<br/>
[在]彈出功能表欄應偏移的行數。

### <a name="remarks"></a>備註

## <a name="cmfcpopupmenubarstartpopupmenutimer"></a><a name="startpopupmenutimer"></a>CMFC彈出選單列::啟動彈出選單計時器

啟動指定延遲彈出功能表按鈕的計時器。

```cpp
void StartPopupMenuTimer(
    CMFCToolBarMenuButton* pMenuButton,
    int nDelayFactor = 1);
```

### <a name="parameters"></a>參數

*pMenu 按鈕*<br/>
[在]指向要為其設置延遲計時器的功能表按鈕。

*nDelay 因數*<br/>
[在]延遲因數(至少等於一個)乘以標準功能表延遲時間(通常介於半秒到五秒之間)。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)
