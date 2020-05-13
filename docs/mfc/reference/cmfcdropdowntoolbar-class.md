---
title: CMFCDropDownToolBar 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: 68dd976471b39d7f50c2f0378b2fce99ad3feeca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367594"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 類別

當使用者按住最上層工具列按鈕時出現的工具列。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC向下工具列::允許顯示帕內選單](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|
|[CMFC下拉工具列::載入點陣圖](#loadbitmap)|(覆蓋[CMFC 工具列::載入位圖](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFC下拉工具列::載入工具列](#loadtoolbar)|(覆寫[CMFC 工具列:LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFC下拉工具列::在LButtonup上](#onlbuttonup)||
|[CMFC向下工具列::滑鼠移動](#onmousemove)||
|[CMFC下拉工具列:打開傳送命令](#onsendcommand)|(覆寫 `CMFCToolBar::OnSendCommand`。)|
|[CMFC下拉工具列::更新CmdUI](#onupdatecmdui)|(覆寫[CMFCTool 列:更新 CmdUI](cmfctoolbar-class.md)。|

### <a name="remarks"></a>備註

物件`CMFCDropDownToolBar`將工具列的視覺外觀與彈出功能表的行為相結合。 當使用者按下並持有下拉工具列按鈕(請參閱[CMFCDropDownToolbarButton 類](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md))時,將顯示一個下拉工具列,使用者可以通過滾動到下拉工具列並釋放滑鼠按鈕來從下拉工具列中選擇一個按鈕。 用戶選擇下拉工具列中的按鈕后,該按鈕將顯示為頂部工具列上的當前按鈕。

無法自定義或停靠下拉工具列,並且沒有拆解狀態。

下圖顯示了一個`CMFCDropDownToolBar`物件:

![CMFCDropDownToolbar 範例](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDownToolbar 範例")

創建`CMFCDropDownToolBar`物件的方式與創建普通工具列的方式相同(請參閱[CMFCToolBar 類](../../mfc/reference/cmfctoolbar-class.md))。

要將下拉工具列插入父工具列::

1. 為父工具列資源的按鈕保留假的資源 ID。

2. 創建包含`CMFCDropDownToolBarButton`下拉工具列的物件(有關詳細資訊,請參閱[CMFCDrop 下拉工具列按鈕::CMFC下拉下工具列按鈕](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton))。

3. 使用 CMFCToolBar`CMFCDropDownToolBarButton`將虛擬按鈕取代為物件[::取代按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。

有關工具列按鈕的詳細資訊,請參閱[演練:將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 有關下拉工具列的範例,請參閱範例專案 VisualStudioDemo。

## <a name="example"></a>範例

下面的示例演示如何在`Create``CMFCDropDownToolBar`類中使用 方法。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

## <a name="cmfcdropdowntoolbarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFC向下工具列::允許顯示帕內選單

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdropdowntoolbarloadbitmap"></a><a name="loadbitmap"></a>CMFC下拉工具列::載入點陣圖

從應用程式資源載入工具列影像。

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>參數

*uiResID*<br/>
[在]引用熱工具列圖像的位圖的資源 ID。

*烏伊庫德雷斯ID*<br/>
[在]引用冷工具列圖像的位圖的資源 ID。

*uiMenuResID*<br/>
[在]引用常規功能表影像的位圖的資源 ID。

*封鎖*<br/>
[在]鎖定工具列的 TRUE;否則 FALSE。

*ui禁用雷斯代碼*<br/>
[在]引用禁用工具列圖像的點陣圖的資源 ID。

*uiMenu 關閉雷斯代碼*<br/>
[在]引用禁用功能表影像的點陣圖的資源 ID。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零，否則為零。

### <a name="remarks"></a>備註

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) 方法會呼叫這個方法來載入與工具列相關聯的影像。 覆寫這個方法可執行影像資源的自訂載入。

呼叫 `LoadBitmapEx` 方法可在建立工具列之後載入其他影像。

## <a name="cmfcdropdowntoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CMFC下拉工具列::載入工具列

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>參數

[在]*uiResID*<br/>

[在]*烏伊庫德雷斯ID*<br/>

[在]*uiMenuResID*<br/>

[在]*波爾*<br/>

[在]*ui禁用雷斯代碼*<br/>

[在]*uiMenu 關閉雷斯代碼*<br/>

[在]*烏霍特雷斯ID*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdropdowntoolbaronlbuttonup"></a><a name="onlbuttonup"></a>CMFC下拉工具列::在LButtonup上

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>參數

[在]*nFlags*<br/>

[在]*點*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdropdowntoolbaronmousemove"></a><a name="onmousemove"></a>CMFC向下工具列::滑鼠移動

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>參數

[在]*nFlags*<br/>

[在]*點*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdropdowntoolbaronsendcommand"></a><a name="onsendcommand"></a>CMFC下拉工具列:打開傳送命令

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pButton*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdropdowntoolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFC下拉工具列::更新CmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>參數

[在]*p 目標*<br/>

[在]*b 關閉IfNoHndler*<br/>

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFC工具列:建立](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFC工具列:更換按鈕](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
