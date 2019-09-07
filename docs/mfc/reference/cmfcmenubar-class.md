---
title: CMFCMenuBar 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 278feca6b64915d0cf789e8f68af3c3fdf9b3129
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739467"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 類別

實作停駐的功能表列。
如需詳細資訊，請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCMenuBar：： AdjustLocations](#adjustlocations)|(覆寫 `CMFCToolBar::AdjustLocations`。)|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定文字標籤是否可以在工具列按鈕的 [影像] 下顯示。 （覆寫[CMFCToolBar：： AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)。）|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|
|[CMFCMenuBar：： CalcFixedLayout](#calcfixedlayout)|計算工具列的水準大小。 （覆寫[CMFCToolBar：： CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)。）|
|[CMFCMenuBar::CalcLayout](#calclayout)|(覆寫 `CMFCToolBar::CalcLayout`。)|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|計算工具列中按鈕的最大高度。 （覆寫[CMFCToolBar：： CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)。）|
|[CMFCMenuBar：： CanBeClosed](#canbeclosed)|指定使用者是否可以關閉工具列。 （覆寫[CMFCToolBar：： CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)。）|
|[CMFCMenuBar：： CanBeRestored](#canberestored)|判斷系統是否可以在自訂之後，將工具列還原成其原始狀態。 （覆寫[CMFCToolBar：： CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。）|
|[CMFCMenuBar::Create](#create)|建立功能表控制項並將其附加至`CMFCMenuBar`物件。|
|[CMFCMenuBar::CreateEx](#createex)|建立具有其他樣式選項的物件。`CMFCMenuBar`|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|`CMFCMenuBar`初始化物件。 接受 HMENU 參數，作為填入`CMFCMenuBar`的範本。|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|啟用位於功能表列**右側的 [說明] 下拉式方塊**。|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|指定是否要顯示快顯功能表的陰影。|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|（覆寫[CPane：： GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)。）|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|傳回工具列按鈕的寬度。 （覆寫[CMFCToolBar：： GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)。）|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|傳回資源檔中原始功能表的控制碼。|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|傳回資源檔中原始功能表的資源識別碼。|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|傳回**說明下拉式方塊**的指標。|
|[CMFCMenuBar::GetHMenu](#gethmenu)|傳回附加至`CMFCMenuBar`物件之功能表的控制碼。|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|傳回功能表物件的目前全域字型。|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|傳回與所提供專案索引相關聯的工具列按鈕。|
|[CMFCMenuBar：： GetRowHeight](#getrowheight)|傳回工具列按鈕的高度。 （覆寫[CMFCToolBar：： GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)。）|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|指出是否反白顯示已停用的功能表項目。|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|決定工具列是否可以顯示具有延伸框線的按鈕。 （覆寫[CMFCToolBar：： IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)。）|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|指出是否反白顯示停用的專案。|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|指出是否繪製快顯功能表的陰影。|
|[CMFCMenuBar：： IsRecentlyUsedMenus](#isrecentlyusedmenus)|指出最近使用的功能表命令是否顯示在功能表列上。|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|指出快顯功能表是否顯示所有命令。|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|指出功能表在短暫延遲之後是否顯示所有命令。|
|[CMFCMenuBar::LoadState](#loadstate)|從登錄載入`CMFCMenuBar`物件的狀態。|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|當使用者選取工具列上的按鈕時由架構呼叫。 （覆寫[CMFCToolBar：： OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)。）|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|框架視窗從資源檔載入預設功能表時由架構呼叫。|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(覆寫 `CMFCToolBar::OnSendCommand`。)|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|當功能表處於自訂模式，而且使用者變更功能表項目的文字時，由架構呼叫。|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(覆寫 `CMFCToolBar::OnToolHitTest`。)|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(覆寫 `CMFCToolBar::PreTranslateMessage`。)|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|當功能表處於自訂模式，而且使用者選取功能表列的 [**重設**] 時，由架構呼叫。|
|[CMFCMenuBar::SaveState](#savestate)|將`CMFCMenuBar`物件的狀態儲存至登錄。|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|設定資源檔中的原始功能表。|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|當 MDI 子視窗變更其顯示模式時由架構呼叫。 如果 MDI 子視窗剛最大化或不再最大化，則此方法會更新功能表列。|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|設定當使用者以動態方式建立功能表按鈕時，所產生的執行時間類別資訊。|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|設定應用程式中所有功能表的字型。|
|[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)|指定功能表列是否顯示最近使用的功能表命令。|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|指定功能表列是否顯示所有命令。|

## <a name="remarks"></a>備註

`CMFCMenuBar`類別是用來執行銜接功能的功能表列。 它與工具列類似，但它並不會被關閉，它一律會顯示。

`CMFCMenuBar`支援顯示最近使用的功能表項目物件的選項。 如果啟用此選項，則`CMFCMenuBar`會在第一次查看時只顯示可用命令的子集。 之後，最近使用的命令會與原始的命令子集一起顯示。 此外，使用者一律可以展開功能表來查看所有可用的命令。 因此，每個可用的命令都會設定為持續顯示，或只在最近選取時才顯示。

若要使用`CMFCMenuBar`物件，請將它內嵌在主視窗框架物件中。 處理`WM_CREATE`訊息時，請呼叫`CMFCMenuBar::Create`或`CMFCMenuBar::CreateEx`。 不論您使用哪一個 create 函式，請將指標傳入主框架視窗。 然後藉由呼叫[CFrameWndEx：： EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)來啟用銜接。 藉由呼叫[CFrameWndEx：:D ockpane](../../mfc/reference/cframewndex-class.md#dockpane)來停駐此功能表。

## <a name="example"></a>範例

下例示範如何在 `CMFCMenuBar` 類別中使用各種方法。 此範例示範如何設定窗格的樣式、啟用 [自訂] 按鈕、啟用 [說明] 方塊、針對快顯功能表啟用陰影，以及更新功能表列。 此程式碼片段是[IE 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>需求

**標頭：** afxmenubar。h

##  <a name="adjustlocations"></a>CMFCMenuBar：： AdjustLocations

在功能表列上調整功能表項目的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>備註

##  <a name="allowchangetextlabels"></a>CMFCMenuBar：： AllowChangeTextLabels

決定功能表列的 [影像] 下是否允許文字標籤。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>傳回值

如果使用者可以選擇在 [影像] 下顯示文字標籤，則傳回 TRUE。

### <a name="remarks"></a>備註

##  <a name="allowshowonpanemenu"></a>CMFCMenuBar：： AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="calcfixedlayout"></a>CMFCMenuBar：： CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

在*bStretch*<br/>

[in] *bHorz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="calclayout"></a>CMFCMenuBar：： CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>參數

在*dwMode*<br/>

在*nLength*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar：： CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="canbeclosed"></a>CMFCMenuBar：： CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="canberestored"></a>CMFCMenuBar：： CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="create"></a>CMFCMenuBar：： Create

建立功能表控制項，並將它附加至[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
在新`CMFCMenuBar`物件之父視窗的指標。

*dwStyle*<br/>
在新功能表列的樣式。

*nID*<br/>
在功能表列之子視窗的識別碼。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

在您建立`CMFCMenuBar`物件之後，必須呼叫`Create`。 這個方法會建立`CMFCMenuBar`控制項，並將它附加`CMFCMenuBar`至物件。

如需工具列樣式的詳細資訊，請參閱[CBasePane：： SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle)。

##  <a name="createex"></a>CMFCMenuBar：： CreateEx

建立具有指定擴充樣式的[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
在新`CMFCMenuBar`物件之父視窗的指標。

*dwCtrlStyle*<br/>
在新功能表列的其他樣式。

*dwStyle*<br/>
在新功能表列的主要樣式。

*rcBorders*<br/>
在參數，指定`CMFCMenuBar`物件的框線大小。 `CRect`

*nID*<br/>
在功能表列之子視窗的識別碼。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

當您想要指定除了工具列樣式以外的樣式時，您應該使用此函式，而不是[CMFCMenuBar：： Create](#create) 。 一些經常使用的其他樣式是 TBSTYLE_TRANSPARENT 和 CBRS_TOP。

如需其他樣式的清單，請參閱[工具列控制項和按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)、[通用控制項樣式](/windows/win32/Controls/common-control-styles)，以及[常用的視窗樣式](/windows/win32/winmsg/window-styles)。

### <a name="example"></a>範例

下列範例示範如何使用`CreateEx` `CMFCMenuBar`類別的方法。 此程式碼片段是[IE 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>CMFCMenuBar：： CreateFromMenu

初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。 這個方法會在`CMFCMenuBar` HMENU 參數之後建立物件的模型。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
在功能表資源的控制碼。 `CreateFromMenu`會使用此資源做為的範本`CMFCMenuBar`。

*bDefaultMenu*<br/>
在布林值，指出新功能表是否為預設功能表。

*bForceUpdate*<br/>
在布林值，指出這個方法是否強制功能表更新。

### <a name="remarks"></a>備註

如果您想要功能表控制項具有與功能表資源相同的功能表項目，請使用這個方法。 呼叫[CMFCMenuBar：： Create](#create)或[CMFCMenuBar：： CreateEx](#createex)之後，請呼叫這個方法。

##  <a name="enablehelpcombobox"></a>CMFCMenuBar：： EnableHelpCombobox

啟用位於功能表列**右側的 [說明] 下拉式方塊**。

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>參數

*uiID*<br/>
在 **[說明] 下拉式方塊**按鈕的命令 ID。

*lpszPrompt*<br/>
在字串，其中包含架構在下拉式方塊中顯示的文字（如果它是空的且不在使用中）。 例如，「在此輸入文字」。

*nComboBoxWidth*<br/>
在下拉式方塊按鈕的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

[說明 **] 下拉式列示方塊**類似 Microsoft Word 功能表列中的 [說明 **] 下拉式方塊**。

當您呼叫這個方法，並將*uiID*設為0時，這個方法會隱藏下拉式方塊。 否則，這個方法會自動在功能表列的右側顯示下拉式方塊。 在您呼叫這個方法之後，請呼叫[CMFCMenuBar：： GetHelpCombobox](#gethelpcombobox)來取得所插入之[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件的指標。

##  <a name="enablemenushadows"></a>CMFCMenuBar：： EnableMenuShadows

啟用快顯功能表的陰影。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在布林值參數，指出是否應該啟用快顯功能表的陰影。

### <a name="remarks"></a>備註

這個方法所使用的演算法很複雜，而且可能會降低您的應用程式在較慢的系統上的效能。

##  <a name="getavailableexpandsize"></a>CMFCMenuBar：： GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getcolumnwidth"></a>CMFCMenuBar：： GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdefaultmenu"></a>CMFCMenuBar：： GetDefaultMenu

抓取原始功能表的控制碼。 架構會從資源檔載入原始功能表。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>傳回值

功能表資源的控制碼。

### <a name="remarks"></a>備註

如果您的應用程式自訂功能表，您可以使用這個方法來抓取原始功能表的控制碼。

##  <a name="getdefaultmenuresid"></a>CMFCMenuBar：： GetDefaultMenuResId

抓取預設功能表的資源識別碼。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>傳回值

功能表資源識別碼。

### <a name="remarks"></a>備註

架構會從資源檔載入`CMFCMenuBar`物件的預設功能表。

##  <a name="getfloatpopupdirection"></a>CMFCMenuBar：： GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>參數

在*pButton*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getforcedownarrows"></a>CMFCMenuBar：： GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="gethelpcombobox"></a>CMFCMenuBar：： GetHelpCombobox

傳回**說明下拉式方塊**的指標。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>傳回值

[說明] 下拉式**方塊的指標**。 如果 [說明] 下拉式方塊已隱藏或未啟用 **，則為**Null。

### <a name="remarks"></a>備註

[說明 **] 下拉式方塊**位於功能表列的右側。 呼叫[CMFCMenuBar：： EnableHelpCombobox](#enablehelpcombobox)方法，以啟用此下拉式方塊。

##  <a name="gethmenu"></a>CMFCMenuBar：： GetHMenu

抓取附加至[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件之功能表的控制碼。

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>CMFCMenuBar：： GetMenuFont

抓取目前的功能表字型。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*bHorz*<br/>
在指定是否要傳回水準或垂直字型的布林值參數。 TRUE 表示水準字型。

### <a name="return-value"></a>傳回值

[CFont](../../mfc/reference/cfont-class.md)參數的指標，其中包含目前的功能表列字型。

### <a name="remarks"></a>備註

傳回的字型是應用程式的全域參數。 系統會針對所有`CMFCMenuBar`物件維護兩個全域字型。 這些個別字型會用於水準和垂直功能表列。

##  <a name="getmenuitem"></a>CMFCMenuBar：： GetMenuItem

根據專案索引，在功能表列上抓取[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>參數

*iItem*<br/>
在要傳回之功能表項目的索引。

### <a name="return-value"></a>傳回值

`CMFCToolBarButton`物件的指標，符合*iItem*所指定的索引。 如果索引無效，則為 Null。

##  <a name="getrowheight"></a>CMFCMenuBar：： GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getsystembutton"></a>CMFCMenuBar：： GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>參數

在*uiBtn*<br/>

在*bByCommand*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getsystembuttonscount"></a>CMFCMenuBar：： GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getsystemmenu"></a>CMFCMenuBar：： GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="highlightdisableditems"></a>CMFCMenuBar：： HighlightDisabledItems

控制架構是否反白顯示已停用的功能表項目。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>參數

*bHighlight*<br/>
在布林值參數，指出架構是否會反白顯示無法使用的功能表項目。

### <a name="remarks"></a>備註

根據預設，當使用者將滑鼠指標置於其上時，架構不會反白顯示無法使用的功能表項目。

##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar：： IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ishighlightdisableditems"></a>CMFCMenuBar：： IsHighlightDisabledItems

指出架構是否會反白顯示無法使用的功能表項目。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>傳回值

如果反白顯示無法使用的功能表項目，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

根據預設，當使用者將滑鼠指標置於其上時，架構不會反白顯示無法使用的功能表項目。 請使用[CMFCMenuBar：： HighlightDisabledItems](#highlightdisableditems)方法來啟用這項功能。

##  <a name="ismenushadows"></a>CMFCMenuBar：： IsMenuShadows

指出架構是否繪製快顯功能表的陰影。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>傳回值

如果架構繪製功能表陰影，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

請使用[CMFCMenuBar：： EnableMenuShadows](#enablemenushadows)方法來啟用或停用這項功能。

##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar：： IsRecentlyUsedMenus

指出最近使用的功能表命令是否顯示在功能表列上。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>傳回值

如果`CMFCMenuBar`物件顯示最近使用的功能表命令，則為非零，否則為0。

### <a name="remarks"></a>備註

使用[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)函式來控制功能表列是否顯示最近使用的功能表命令。

##  <a name="isshowallcommands"></a>CMFCMenuBar：： IsShowAllCommands

指出功能表是否顯示所有命令。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>傳回值

如果顯示所有`CMFCMenuBar`命令，則為非零，否則為0。

### <a name="remarks"></a>備註

`CMFCMenuBar`物件可以設定為顯示所有命令，或只顯示命令的子集。 如需這項功能的詳細資訊，請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。

`IsShowAllCommands`會告訴您如何為`CMFCMenuBar`物件設定這項功能。 若要控制所顯示的功能表命令，請使用[CMFCMenuBar：： SetShowAllCommands](#setshowallcommands)和[CMFCMenuBar：： SetRecentlyUsedMenus](#setrecentlyusedmenus)方法。

##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar：： IsShowAllCommandsDelay

指出[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件是否會在短暫延遲後顯示所有命令。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>傳回值

如果功能表列在短暫延遲之後顯示完整功能表，則為非零;否則為0。

### <a name="remarks"></a>備註

當您設定功能表列以顯示 [最近使用的專案] 時，功能表列會以下列兩種方式的其中一種來顯示 [完整] 功能表：

- 當使用者將游標停留在功能表底部的箭號上時，顯示 [從設計的延遲後] 的 [完整] 功能表。

- 在使用者按一下功能表底部的箭號之後，顯示 [完整] 功能表。

根據預設，所有`CMFCMenuBar`物件都會使用選項，在短暫延遲之後顯示完整的功能表。 此選項無法在`CMFCMenuBar`類別中以程式設計方式變更。 不過，使用者可以使用 [**自訂**] 對話方塊，在自訂工具列期間變更行為。

##  <a name="loadstate"></a>CMFCMenuBar：： LoadState

從 Windows 登錄載入功能表列的狀態。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在字串，其中包含 Windows 登錄機碼的路徑。

*nIndex*<br/>
在功能表列的控制項 ID。

*uiID*<br/>
在保留的值。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用[CMFCMenuBar：： SaveState](#savestate)方法，將功能表列的狀態儲存至登錄。 儲存的資訊包括功能表項目、停駐狀態和功能表列的位置。

在大多數情況下，您的應用`LoadState`程式不會呼叫。 架構會在初始化工作區時呼叫這個方法。

##  <a name="onchangehot"></a>CMFCMenuBar：： OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>參數

在*iHot*<br/>

### <a name="remarks"></a>備註

##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar：： OnDefaultMenuLoaded

當此架構從資源檔載入功能表資源時，會呼叫這個方法。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
在附加至`CMFCMenuBar`物件之功能表的控制碼。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 在架構從資源檔載入功能表資源之後，覆寫此函式以執行自訂程式碼。

##  <a name="onsendcommand"></a>CMFCMenuBar：： OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

在*pButton*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar：： OnSetDefaultButtonText

當使用者在功能表列上變更專案的文字時，架構會呼叫這個方法。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

*pButton*<br/>
在使用者想要自訂之[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件的指標。

### <a name="return-value"></a>傳回值

如果架構將使用者變更套用至功能表列，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法的預設執行會將按鈕的文字變更為使用者所提供的文字。

##  <a name="ontoolhittest"></a>CMFCMenuBar：： OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>參數

在*點*<br/>

[in] *pTI*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="pretranslatemessage"></a>CMFCMenuBar：:P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

在*pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="restoreoriginalstate"></a>CMFCMenuBar：： RestoreOriginalstate

當使用者從 [**自訂**] 對話方塊中選取 [**重設**] 時，由架構呼叫。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

當使用者從 [自訂] 功能表選取 [**重設**] 時，會呼叫這個方法。 您也可以手動呼叫這個方法，以程式設計方式重設功能表列的狀態。 這個方法會從資源檔載入原始狀態。

如果您想要在使用者選取 [**重設**] 選項時進行任何處理，請覆寫這個方法。

##  <a name="savestate"></a>CMFCMenuBar：： SaveState

將[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件的狀態儲存至 Windows 登錄。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在字串，其中包含 Windows 登錄機碼的路徑。

*nIndex*<br/>
在功能表列的控制項 ID。

*uiID*<br/>
在保留的值。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE;否則為 FALSE;

### <a name="remarks"></a>備註

通常，您的應用程式不`SaveState`會呼叫。 當工作區序列化時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CWinAppEx：： SaveState](../../mfc/reference/cwinappex-class.md#savestate)。

儲存的資訊包括功能表項目、停駐狀態和功能表列的位置。

##  <a name="setdefaultmenuresid"></a>CMFCMenuBar：： SetDefaultMenuResId

根據資源識別碼設定[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件的預設功能表。

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>參數

*uiResId*<br/>
在新預設功能表的資源識別碼。

### <a name="remarks"></a>備註

[CMFCMenuBar：： RestoreOriginalstate](#restoreoriginalstate)方法會從資源檔案還原預設功能表。

使用[CMFCMenuBar：： GetDefaultMenuResId](#getdefaultmenuresid)方法來抓取預設功能表，而不將它還原。

##  <a name="setforcedownarrows"></a>CMFCMenuBar：： SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>參數

在*其中 bvalue system.boolean.true*<br/>

### <a name="remarks"></a>備註

##  <a name="setmaximizemode"></a>CMFCMenuBar：： SetMaximizeMode

當 MDI 變更其顯示模式，而且必須更新功能表列時，架構會呼叫這個方法。

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>參數

*bMax*<br/>
在指定模式的布林值。 如需詳細資訊，請參閱＜備註＞一節。

*pWnd*<br/>
在要變更之 MDI 子視窗的指標。

*bRecalcLayout*<br/>
在布林值，指定是否應該立即重新計算功能表列的版面配置。

### <a name="remarks"></a>備註

當 MDI 子視窗最大化時，附加至 MDI 主框架視窗的功能表列會顯示 [系統] 功能表和 [**最小化**]、[**最大化**] 和 [**關閉**] 按鈕。 如果*bMax*為 TRUE 且*PWND*不是 Null，則會將 MDI 子視窗最大化，而且功能表列必須併入額外的控制項。 否則，功能表列會回到其正常狀態。

##  <a name="setmenubuttonrtc"></a>CMFCMenuBar：： SetMenuButtonRTC

設定當使用者建立功能表按鈕時，架構所使用的執行時間類別資訊。

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>參數

*pMenuButtonRTC*<br/>
在衍生自[CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)之類別的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)資訊。

### <a name="remarks"></a>備註

當使用者將新按鈕新增至功能表列時，架構會動態建立按鈕。 根據預設，它會`CMFCMenuButton`建立物件。 覆寫這個方法，以變更架構所建立之按鈕物件的類型。

##  <a name="setmenufont"></a>CMFCMenuBar：： SetMenuFont

設定應用程式中所有功能表列的字型。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
在[LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta)結構的指標，定義要設定的字型。

*bHorz*<br/>
在如果您想要將*lpLogFont*參數用於垂直字型，則為 TRUE，如果您想要將它用於水準字型，則為 FALSE。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

所有`CMFCMenuBar`物件都會使用兩個字型。 這些個別字型會用於水準和垂直功能表列。

字型設定為全域變數，並會影響`CMFCMenuBar`所有物件。

##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar：： SetRecentlyUsedMenus

控制功能表列是否顯示最近使用的功能表命令。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
在布林值，控制是否顯示最近使用的功能表命令。

##  <a name="setshowallcommands"></a>CMFCMenuBar：： SetShowAllCommands

控制功能表是否顯示所有可用的命令。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>參數

*bShowAllCommands*<br/>
在布林值參數，指定快顯功能表是否顯示所有功能表命令。

### <a name="remarks"></a>備註

如果功能表未顯示所有功能表命令，則會隱藏很少使用的命令。 如需顯示功能表命令的詳細資訊，請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
