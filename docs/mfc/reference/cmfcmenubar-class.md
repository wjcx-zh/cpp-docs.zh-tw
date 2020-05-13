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
ms.openlocfilehash: f25bff9564eb7a4290f958f0b7810cac8ef7e238
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749625"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar 類別

實作停駐的功能表列。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(覆寫 `CMFCToolBar::AdjustLocations`。)|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|指定文字標籤是否可以顯示在工具列按鈕上的圖像下。 (覆寫[CMFC 工具列::允許變更文字標籤](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|
|[CMFC選單列::允許顯示帕內選單](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|
|[CMFC選單列:鈣固定佈局](#calcfixedlayout)|計算工具列的水準大小。 (覆蓋[CMFCTool 列:CalcFixed佈局](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|
|[CMFC選單列:卡路里佈局](#calclayout)|(覆寫 `CMFCToolBar::CalcLayout`。)|
|[CMFC功能表列::卡爾馬克斯按鈕高度](#calcmaxbuttonheight)|計算工具列中按鈕的最大高度。 (覆蓋[CMFC 工具列::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|
|[CMFC選單列:可關閉](#canbeclosed)|指定使用者是否可以關閉工具列。 (覆寫[CMFC 工具列::可以關閉](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|
|[CMFC功能表列:可還原](#canberestored)|確定系統在自定義后是否可以將工具列還原到其原始狀態。 (覆蓋[CMFCTool 欄:可以還原](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFC選單列:建立](#create)|創建功能表控制件並將其附加到`CMFCMenuBar`物件。|
|[CMFC選單列:建立Ex](#createex)|創建具有`CMFCMenuBar`其他樣式選項的物件。|
|[CMFC選單列:從Menu創建](#createfrommenu)|初始化 `CMFCMenuBar` 物件。 接受充當填充`CMFCMenuBar`的範本的 HMENU 參數。|
|[CMFC選單列:啟用説明Combobox](#enablehelpcombobox)|啟用位於功能表欄右側**的幫助**組合框。|
|[CMFC選單列:啟用選單陰影](#enablemenushadows)|指定是否顯示彈出式功能表的陰影。|
|[CMFCMenuBar::取得可用延伸大小](#getavailableexpandsize)|( 覆[寫 CPane:取得可用延伸大小](../../mfc/reference/cpane-class.md#getavailableexpandsize)。|
|[CMFC選單列:取得柱寬度](#getcolumnwidth)|返回工具列按鈕的寬度。 (覆寫[CMFC 工具列:取得柱寬度](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|
|[CMFC選單列::取得預設選單](#getdefaultmenu)|返回資源檔中原始功能表的句柄。|
|[CMFC選單列:取得預設選單Resid](#getdefaultmenuresid)|返回資源檔中原始功能表的資源標識符。|
|[CMFC選單列:取得浮動彈出方向](#getfloatpopupdirection)||
|[CMFC功能表列:獲取力量向下箭頭](#getforcedownarrows)||
|[CMFC選單列:取得説明Combobox](#gethelpcombobox)|返回指向 **「幫助**組合」框的指標。|
|[CMFC選單列:取得HMenu](#gethmenu)|返回附加到物件的功能表的`CMFCMenuBar`句柄。|
|[CMFC選單列:取得選單方](#getmenufont)|返回功能表物件的當前全域字型。|
|[CMFC選單列:取得選單專案](#getmenuitem)|返回與提供的物料索引關聯的工具列按鈕。|
|[CMFC選單列:獲取羅高](#getrowheight)|返回工具列按鈕的高度。 (覆寫[CMFC 工具列:取得羅高](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFC 選單列:取得系統按鈕](#getsystembutton)||
|[CMFC選單列:取得系統按鈕計數](#getsystembuttonscount)||
|[CMFC選單:取得系統選單](#getsystemmenu)||
|[CMFC選單列::突出顯示禁用專案](#highlightdisableditems)|指示是否突出顯示禁用的功能表項。|
|[CMFC選單列:是按鈕外尺寸可用](#isbuttonextrasizeavailable)|確定工具列是否可以顯示具有擴展邊框的按鈕。 (覆寫[CMFC 工具列:是按鈕外大尺寸](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|
|[CMFC選單列:是突出顯示的禁用專案](#ishighlightdisableditems)|指示是否突出顯示已禁用的專案。|
|[CMFC功能表列::正選單陰影](#ismenushadows)|指示是否為彈出式功能表繪製陰影。|
|[CMFCMenuBar:是最近使用的選單](#isrecentlyusedmenus)|指示功能表列上是否顯示最近使用的功能表命令。|
|[CMFC選單列::是顯示所有命令](#isshowallcommands)|指示彈出式功能表是否顯示所有命令。|
|[CMFC選單列::是顯示所有命令延遲](#isshowallcommandsdelay)|指示功能表在短暫延遲後是否顯示所有命令。|
|[CMFC選單列:載入狀態](#loadstate)|從註冊表載入`CMFCMenuBar`物件的狀態。|
|[CMFC選單列:上更改熱](#onchangehot)|當用戶選擇工具列上的按鈕時,框架調用。 (覆寫[CMFC 工具列:開啟變更熱](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|
|[CMFC選單列:開啟預設選單載入](#ondefaultmenuloaded)|當框架視窗從資源檔載入預設選單時,框架調用。|
|[CMFC選單列:開啟傳送指令](#onsendcommand)|(覆寫 `CMFCToolBar::OnSendCommand`。)|
|[CMFC 選單列:開啟預設按鈕文字](#onsetdefaultbuttontext)|當功能表處於自訂模式且使用者更改功能表項的文本時,由框架調用。|
|[CMFCMenuBar::在工具命中測試](#ontoolhittest)|(覆寫 `CMFCToolBar::OnToolHitTest`。)|
|[CMFCMenuBar::P重新翻譯訊息](#pretranslatemessage)|(覆寫 `CMFCToolBar::PreTranslateMessage`。)|
|[CMFCMenuBar:回復原始狀態](#restoreoriginalstate)|當選單處於自定義模式且使用者為功能表欄選擇 **「重置」** 時,由框架調用。|
|[CMFC選單列:儲存狀態](#savestate)|將`CMFCMenuBar`物件的狀態保存到註冊表。|
|[CMFC選單列::設定預設選單Resid](#setdefaultmenuresid)|在資源檔中設置原始功能表。|
|[CMFC選單列:設定強制向下箭頭](#setforcedownarrows)||
|[CMFC選單列::設定最大化模式](#setmaximizemode)|當 MDI 子視窗更改其顯示模式時,由框架調用。 如果 MDI 子視窗是新最大化或不再最大化,此方法將更新功能表欄。|
|[CMFC選單列:設定選單按鈕RTC](#setmenubuttonrtc)|設置使用者動態創建功能表按鈕時生成的運行時類資訊。|
|[CMFCMenuBar:setMenuFont](#setmenufont)|設置應用程式中所有功能表的字型。|
|[CMFC選單列:設定最近使用的選單](#setrecentlyusedmenus)|指定選單列是否顯示最近使用的選單命令。|
|[CMFC選單列::設定顯示所有命令](#setshowallcommands)|指定選單列是否顯示所有命令。|

## <a name="remarks"></a>備註

類`CMFCMenuBar`是實現停靠功能的功能表欄。 它類似於工具列,儘管它無法關閉 - 它總是顯示。

`CMFCMenuBar`支援顯示最近使用的功能表項物件的選項。 如果啟用此選項,則第`CMFCMenuBar`一次查看時僅顯示可用命令的子集。 此後,最近使用的命令與命令的原始子集一起顯示。 此外,用戶始終可以展開功能表以查看所有可用的命令。 因此,每個可用命令都配置為持續顯示,或僅在最近選擇時顯示。

要使用物件`CMFCMenuBar`,請將它嵌入到主視窗框架物件中。 處理`WM_CREATE`訊息時,呼`CMFCMenuBar::Create`叫`CMFCMenuBar::CreateEx`或 。 無論您使用哪種創建函數,都會將指標傳遞到主框架視窗。 然後通過調用[CFrameWndEx::啟用停靠](../../mfc/reference/cframewndex-class.md#enabledocking)來啟用停靠。 通過調用[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane))來停靠此功能表。

## <a name="example"></a>範例

下例示範如何在 `CMFCMenuBar` 類別中使用各種方法。 該範例展示如何設定窗格的樣式、啟用自訂按鈕、啟用説明框、為彈出式功能表啟用陰影以及更新選單欄。 此代碼段是[IE 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>需求

**標題:** afxmenubar.h

## <a name="cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFC選單列:調整位置

調整功能表欄上功能表項的位置。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>備註

## <a name="cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFC選單列:允許變更文字標籤

確定選單列中的圖像下是否允許文本標籤。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>傳回值

如果用戶可以選擇在圖像下顯示文本標籤,則返回 TRUE。

### <a name="remarks"></a>備註

## <a name="cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC選單列::允許顯示帕內選單

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFC選單列:鈣固定佈局

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>參數

[在]*b 伸*<br/>

[在]*布霍茲*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFC選單列:卡路里佈局

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>參數

[在]*dwMode*<br/>

[在]*N 長度*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFC功能表列::卡爾馬克斯按鈕高度

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFC選單列:可關閉

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFC功能表列:可還原

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarcreate"></a><a name="create"></a>CMFC選單列:建立

創建功能表控制件並將其附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
[在]指向新`CMFCMenuBar`物件的父視窗。

*dwStyle*<br/>
[在]新功能表欄的樣式。

*nID*<br/>
[在]選單欄的子視窗的 ID。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

建構`CMFCMenuBar`物件後,必須呼`Create`叫 。 此方法創建`CMFCMenuBar`控制項並將其附加到`CMFCMenuBar`物件。

有關工具列樣式的詳細資訊,請參閱[CBasePane::設定窗格樣式](../../mfc/reference/cbasepane-class.md#setpanestyle)。

## <a name="cmfcmenubarcreateex"></a><a name="createex"></a>CMFC選單列:建立Ex

創建具有指定擴展樣式的[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。

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

*pparentwnd*<br/>
[在]指向新`CMFCMenuBar`物件的父視窗。

*dwCtrl風格*<br/>
[在]新功能表欄的其他樣式。

*dwStyle*<br/>
[在]新功能表欄的主樣式。

*rcBorders*<br/>
[在]指定`CRect``CMFCMenuBar`物件邊框大小的參數。

*nID*<br/>
[在]選單欄的子視窗的 ID。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

除了工具列樣式之外,還應使用此函數而不是[CMFCMenuBar::在](#create)指定樣式時創建。 TBSTYLE_TRANSPARENT和CBRS_TOP一些常用的其他樣式。

有關其他樣式的清單,請參閱[工具列控制項與按鈕樣式](/windows/win32/Controls/toolbar-control-and-button-styles)、[常見控制項樣式](/windows/win32/Controls/common-control-styles)與[常見視窗樣式](/windows/win32/winmsg/window-styles)。

### <a name="example"></a>範例

下面的示例演示如何使用`CreateEx``CMFCMenuBar`類的方法。 此代碼段是[IE 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

## <a name="cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFC選單列:從Menu創建

初始化[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件。 此方法在`CMFCMenuBar`HMENU 參數後對物件建模。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[在]功能表資源的句柄。 `CreateFromMenu`使用此資源作為的`CMFCMenuBar`範本。

*b預設選單*<br/>
[在]指示新功能表是否為預設選單的布林。

*bForce 更新*<br/>
[在]指示此方法是否強制功能表更新的布林。

### <a name="remarks"></a>備註

如果希望功能表控件具有與菜單資源相同的功能表項,請使用此方法。 呼叫[CMFCMenuBar:::建立](#create)或[CMFCMenuBar::createEx](#createex)後,調用此方法。

## <a name="cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFC選單列:啟用説明Combobox

啟用位於功能表欄右側**的幫助**組合框。

```cpp
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>參數

*uiID*<br/>
[在]**「幫助**組合」框按鈕的命令 ID。

*lpszPrompt*<br/>
[在]包含框架在組合框中顯示的文本(如果文字為空且不處於活動狀態)的字串。 例如,"在此處輸入文本"。

*nComboBox寬度*<br/>
[在]組合框的按鈕寬度(以像素為單位)。

### <a name="remarks"></a>備註

**「幫助**組合」框類似於 Microsoft Word 選單欄中的 **「幫助**組合」框。

當您使用*uiID*設定為 0 呼叫此方法時,此方法將隱藏組合框。 否則,此方法會自動在菜單欄的右側顯示組合框。 呼叫此方法後,調用[CMFCMenuBar::取得説明Combobox](#gethelpcombobox)以取得指向插入[的 CMFCToolBarComboxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)物件的指標。

## <a name="cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFC選單列:啟用選單陰影

為彈出式功能表啟用陰影。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]布爾參數,指示是否應為彈出式功能表啟用陰影。

### <a name="remarks"></a>備註

此方法使用的演演演算法很複雜,可能會降低應用程式在較慢系統上的性能。

## <a name="cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar::取得可用延伸大小

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFC選單列:取得柱寬度

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFC選單列::取得預設選單

檢索原始功能表的句柄。 框架從資源檔載入原始選單。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>傳回值

功能表資源的句柄。

### <a name="remarks"></a>備註

如果應用程式自定義功能表,則可以使用此方法檢索原始功能表的句柄。

## <a name="cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFC選單列:取得預設選單Resid

檢索預設功能表的資源標識符。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>傳回值

功能表資源標識碼。

### <a name="remarks"></a>備註

框架從資源檔載入`CMFCMenuBar`物件的預設功能表。

## <a name="cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFC選單列:取得浮動彈出方向

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pButton*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFC功能表列:獲取力量向下箭頭

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFC選單列:取得説明Combobox

返回指向 **「幫助**組合」框的指標。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>傳回值

指向 **「幫助**組合」框的指標。 如果 **「幫助**組合」框處於隱藏狀態或未啟用,則為 NULL。

### <a name="remarks"></a>備註

**「幫助**組合」框位於功能表欄的右側。 呼叫方法[CMFCMenuBar:啟用説明Combobox](#enablehelpcombobox)以啟用此組合框。

## <a name="cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFC選單列:取得HMenu

檢索附加到[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件的功能表的句柄。

```
HMENU GetHMenu() const;
```

## <a name="cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFC選單列:取得選單方

檢索當前功能表字體。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*布霍茲*<br/>
[在]指定是返回水平字體還是垂直字體的布爾參數。 TRUE 表示水準字體。

### <a name="return-value"></a>傳回值

指向包含當前功能表欄字型的[CFont](../../mfc/reference/cfont-class.md)參數的指標。

### <a name="remarks"></a>備註

返回的字體是應用程式的全域參數。 為所有`CMFCMenuBar`物件維護兩個全域字體。 這些單獨的字體用於水準和垂直功能表欄。

## <a name="cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFC選單列:取得選單專案

根據專案索引在功能表欄上檢索[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>參數

*iItem*<br/>
[在]要返回的功能表項的索引。

### <a name="return-value"></a>傳回值

指向與`CMFCToolBarButton`*iItem*指定的索引匹配的物件的指標。 如果索引無效,則為 NULL。

## <a name="cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFC選單列:獲取羅高

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFC 選單列:取得系統按鈕

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>參數

[在]*烏伊布滕*<br/>

[在]*bByCommand*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFC選單列:取得系統按鈕計數

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFC選單:取得系統選單

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFC選單列::突出顯示禁用專案

控制框架是否突出顯示禁用的功能表項。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>參數

*b 高光*<br/>
[在]一個布爾參數,指示框架是否突出顯示不可用的功能表項。

### <a name="remarks"></a>備註

默認情況下,當用戶將滑鼠指標放在它們上時,框架不會突出顯示不可用的菜單項。

## <a name="cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFC選單列:是按鈕外尺寸可用

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFC選單列:是突出顯示的禁用專案

指示框架是否突出顯示不可用的菜單項。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>傳回值

如果突出顯示不可用的功能表項,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

默認情況下,當用戶將滑鼠指標放在它們上時,框架不會突出顯示不可用的菜單項。 使用[CMFCMenuBar:突出顯示禁用專案](#highlightdisableditems)方法啟用此功能。

## <a name="cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFC功能表列::正選單陰影

指示框架是否為彈出式功能表繪製陰影。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>傳回值

如果框架繪製功能表陰影,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

使用[CMFCMenuBar:啟用MenuShadows](#enablemenushadows)方法啟用或禁用此功能。

## <a name="cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar:是最近使用的選單

指示功能表列上是否顯示最近使用的功能表命令。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>傳回值

如果對象顯示`CMFCMenuBar`最近 使用的功能表命令,則非零;否則 0。

### <a name="remarks"></a>備註

使用函數[CMFCMenuBar:設定最近使用功能表](#setrecentlyusedmenus)來控制功能表欄是否顯示最近使用的功能表命令。

## <a name="cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFC選單列::是顯示所有命令

指示功能表是否顯示所有命令。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>傳回值

如果顯示所有命令`CMFCMenuBar`,則非零;否則 0。

### <a name="remarks"></a>備註

可以將`CMFCMenuBar`物件設定為顯示所有命令或僅顯示命令的子集。 有關此功能的詳細資訊,請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。

`IsShowAllCommands`將告訴您如何為`CMFCMenuBar`物件配置此功能。 要控制顯示哪些選單指令,請使用[CMFCMenuBar::SetShowAll 命令](#setshowallcommands)與[CMFCMenuBar::設定最近使用的選單](#setrecentlyusedmenus)。

## <a name="cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFC選單列::是顯示所有命令延遲

指示[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件在短暫延遲后是否顯示所有命令。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>傳回值

如果功能表欄在短暫延遲後顯示完整功能表,則非零;否則 0。

### <a name="remarks"></a>備註

將選單列設定為顯示最近使用的項目時,選單列以以下兩種方式之一顯示完整選單:

- 在使用者將游標懸停在菜單底部的箭頭上時,在程式設計延遲後顯示完整菜單。

- 用戶按一下功能表底部的箭頭後顯示完整功能表。

默認情況下,所有`CMFCMenuBar`物件都使用 該選項在短暫延遲后顯示完整功能表。 此選項無法在`CMFCMenuBar`類中以程式設計方式更改。 但是,使用者可以使用 **「自訂」** 對話框更改工具列自定義期間的行為。

## <a name="cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFC選單列:載入狀態

從 Windows 註冊表載入功能表欄的狀態。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]包含 Windows 註冊表項路徑的字串。

*nIndex*<br/>
[在]功能表欄的控制 ID。

*uiID*<br/>
[在]保留值。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

使用[CMFCMenuBar::保存狀態](#savestate)方法將功能表欄的狀態保存到註冊表。 保存的資訊包括功能表項、停靠狀態和功能表欄的位置。

在大多數情況下,您的應用程式不呼叫`LoadState`。 框架在初始化工作區時調用此方法。

## <a name="cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFC選單列:上更改熱

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>參數

[在]*iHot*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFC選單列:開啟預設選單載入

當框架從資源檔載入選單資源時,它將調用此方法。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>參數

*hMenu*<br/>
[在]附加到物件的功能表的`CMFCMenuBar`句柄。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 重寫此函數,在框架從資源檔中載入功能表資源後執行自訂代碼。

## <a name="cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFC選單列:開啟傳送指令

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pButton*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFC 選單列:開啟預設按鈕文字

當使用者更改功能表欄上的項目的文字時,框架將調用此方法。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[在]指向使用者要自定義的[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)物件的指標。

### <a name="return-value"></a>傳回值

如果框架將使用者更改應用於功能表欄,則為 TRUE;如果框架將使用者更改應用於菜單欄。否則 FALSE。

### <a name="remarks"></a>備註

此方法的預設實現將按鈕的文本更改為使用者提供的文本。

## <a name="cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::在工具命中測試

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>參數

[在]*點*<br/>

[在]*pTI*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::P重新翻譯訊息

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

[在]*pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar:回復原始狀態

當使用者從 **「自訂」** 對話框中選擇 **「重置」** 時,由框架調用。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

當使用者從自定義功能表中選擇 **「重置」** 時,將調用此方法。 您還可以手動調用此方法以以程式設計方式重置功能表欄的狀態。 此方法從資源檔載入原始狀態。

如果要在使用者選擇 **「重置」** 選項時執行任何處理,請重寫此方法。

## <a name="cmfcmenubarsavestate"></a><a name="savestate"></a>CMFC選單列:儲存狀態

將[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件的狀態保存到 Windows 註冊表。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]包含 Windows 註冊表項路徑的字串。

*nIndex*<br/>
[在]功能表欄的控制 ID。

*uiID*<br/>
[在]保留值。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE;否則 FALSE;

### <a name="remarks"></a>備註

通常,您的應用程式不呼叫`SaveState`。 當工作區序列化時,框架調用此方法。 有關詳細資訊,請參閱[CWinAppEx::保存狀態](../../mfc/reference/cwinappex-class.md#savestate)。

保存的資訊包括功能表項、停靠狀態和功能表欄的位置。

## <a name="cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFC選單列::設定預設選單Resid

根據資源 ID 設定[CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)物件的預設功能表。

```cpp
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>參數

*uiResId*<br/>
[在]新預設功能表的資源 ID。

### <a name="remarks"></a>備註

[CMFCMenuBar:還原原始狀態](#restoreoriginalstate)方法從資源檔還原預設功能表。

使用[CMFCMenuBar:取得預設MenuResId](#getdefaultmenuresid)方法檢索預設功能表,而無需還原它。

## <a name="cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFC選單列:設定強制向下箭頭

```cpp
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>參數

[在]*bValue*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFC選單列::設定最大化模式

當 MDI 更改其顯示模式且選單欄必須更新時,框架將調用此方法。

```cpp
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>參數

*bMax*<br/>
[在]指定模式的布爾。 如需詳細資訊，請參閱「備註」一節。

*pwnd*<br/>
[在]指向正在更改的 MDI 子視窗的指標。

*bRecalcLayout*<br/>
[在]指定是否應立即重新計算選單欄佈局的布林。

### <a name="remarks"></a>備註

最大化 MDI 子視窗時,連接到 MDI 主框架視窗的選單列將顯示系統選單和 **「最小化**」、「**最大化**」和 **「關閉**」按鈕。 如果*bMax*為 TRUE,並且*pWnd*不是 NULL,則 MDI 子視窗將最大化,功能表欄必須合併額外的控制件。 否則,功能表欄將返回到其常規狀態。

## <a name="cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFC選單列:設定選單按鈕RTC

設置用戶創建功能表按鈕時框架使用的運行時類資訊。

```cpp
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>參數

*pMenuButtonRTC*<br/>
[在]從[CMFCMenuButton 類](../../mfc/reference/cmfcmenubutton-class.md)派生的類的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)資訊。

### <a name="remarks"></a>備註

當使用者向功能表欄添加新按鈕時,框架會動態創建按鈕。 預設情況下,它創建`CMFCMenuButton`物件。 重寫此方法以更改框架創建的按鈕物件的類型。

## <a name="cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar:setMenuFont

設置應用程式中所有功能表欄的字型。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
[在]指向[LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta)結構的指標,用於定義要設置的字型。

*布霍茲*<br/>
[在]如果希望*lpLogFont*參數用於垂直字體,則為 FALSE,如果希望將其用於水準字體,則 FALSE。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

兩種字體用於所有`CMFCMenuBar`物件。 這些單獨的字體用於水準和垂直功能表欄。

字體設置是全域變數,影響所有`CMFCMenuBar`物件。

## <a name="cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFC選單列:設定最近使用的選單

控制選單列是否顯示最近使用的選單命令。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*邦*<br/>
[在]控制是否顯示最近使用的功能表命令的布林。

## <a name="cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFC選單列::設定顯示所有命令

控制選單是否顯示所有可用命令。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>參數

*b 顯示所有指令*<br/>
[在]布爾參數,用於指定彈出功能表是否顯示所有功能表命令。

### <a name="remarks"></a>備註

如果功能表不顯示所有選單命令,它將隱藏很少使用的命令。 有關顯示選單指令的詳細資訊,請參閱[CMFCMenuBar 類別](../../mfc/reference/cmfcmenubar-class.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
