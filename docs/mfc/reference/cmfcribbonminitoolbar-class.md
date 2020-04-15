---
title: CMFCRibbonMiniToolBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
helpviewer_keywords:
- CMFCRibbonMiniToolBar [MFC], IsContextMenuMode
- CMFCRibbonMiniToolBar [MFC], IsRibbonMiniToolBar
- CMFCRibbonMiniToolBar [MFC], SetCommands
- CMFCRibbonMiniToolBar [MFC], Show
- CMFCRibbonMiniToolBar [MFC], ShowWithContextMenu
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
ms.openlocfilehash: 10b1d35c331df6563d09be0bea3c97c73e89acaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375082"
---
# <a name="cmfcribbonminitoolbar-class"></a>CMFCRibbonMiniToolBar 類別

實作內容快顯工具列。

## <a name="syntax"></a>語法

```
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|預設建構函式。|
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCRibbonMiniToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCRibbonMiniToolBar::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(覆寫 `CMFCPopupMenu::IsRibbonMiniToolBar`。)|
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|設定要顯示在工具列上的命令清單。|
|[CMFCRibbonMiniToolBar::Show](#show)|顯示位於指定的螢幕座標的迷你工具列。|
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|顯示迷你工具列以及內容功能表。|

## <a name="remarks"></a>備註

使用者在文件中選取物件之後，通常會顯示迷你工具列。 比方說，在使用者於文書處理程式中選取文字區塊之後，應用程式會顯示包含文字格式化命令的迷你工具列。

當滑鼠指標超出迷你工具列的範圍時，迷你工具列會變成透明。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

`CMFCRibbonPanelMenu`

[CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonMiniToolBar.h

## <a name="cmfcribbonminitoolbarsetcommands"></a><a name="setcommands"></a>CMFC 功能迷你工具列:設定指令

設定要顯示在工具列上的命令清單。

```
void SetCommands(
    CMFCRibbonBar* pRibbonBar,
    const CList<UINT,UINT>& lstCommands);
```

### <a name="parameters"></a>參數

*pRibbonbar*<br/>
[在]迷你工具列搜索要顯示的按鈕的功能區列。

*lstCommands*<br/>
[在]要顯示在迷你工具列上的命令清單。 將搜索所有功能區類別以查找關聯的按鈕。

### <a name="remarks"></a>備註

使用此函數可以設置要顯示在迷你工具列中的命令清單。

### <a name="example"></a>範例

下面的示例演示如何使用`SetCommands``CMFCRibbonMiniToolBar`類的方法。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#9](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]

## <a name="cmfcribbonminitoolbarshow"></a><a name="show"></a>CMFC功能迷你工具列:顯示

顯示位於指定的螢幕座標的迷你工具列。

```
BOOL Show(
    int x,
    int y);
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]在螢幕座標中指定迷你工具列的水準位置。

*Y*<br/>
[在]在螢幕座標中指定迷你工具列的垂直位置。

### <a name="return-value"></a>傳回值

如果迷你工具列已成功顯示,則為 TRUE;否則,FALSE。

## <a name="cmfcribbonminitoolbarshowwithcontextmenu"></a><a name="showwithcontextmenu"></a>CMFC 功能迷你工具列::顯示與上下文選單

顯示迷你工具列以及內容功能表。

```
BOOL ShowWithContextMenu(
    int x,
    int y,
    UINT uiMenuResID,
    CWnd* pWndOwner);
```

### <a name="parameters"></a>參數

*X.*<br/>
[在]指定螢幕座標中上下文選單的水準位置。

*Y*<br/>
[在]指定螢幕座標中上下文選單的垂直位置。

*uiMenuResID*<br/>
[在]指定要顯示的上下文選單的資源 ID。

*pwndOwner*<br/>
[在]標識從上下文菜單接收消息的視窗。

### <a name="return-value"></a>傳回值

如果上下文菜單成功顯示,則為 TRUE;如果上下文菜單已成功顯示,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

使用此功能可顯示具有上下文菜單的迷你工具列。 上下文菜單位於迷你工具列下方 15 圖元。

## <a name="cmfcribbonminitoolbariscontextmenumode"></a><a name="iscontextmenumode"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
BOOL IsContextMenuMode() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonminitoolbarisribbonminitoolbar"></a><a name="isribbonminitoolbar"></a>CMFC 功能迷你工具列:是帶狀迷你工具列

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual BOOL IsRibbonMiniToolBar() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
