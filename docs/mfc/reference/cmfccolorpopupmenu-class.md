---
title: CMFCColorPopupMenu 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
ms.openlocfilehash: d668a7bd2b5226de906ca146c7b7e882b97f4640
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560981"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 類別

表示使用者用來選取檔或應用程式色彩的快顯功能表。

## <a name="syntax"></a>語法

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFCColorPopupMenu：： CMFCColorPopupMenu](#cmfccolorpopupmenu)|建構 `CMFCColorPopupMenu` 物件。|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCColorPopupMenu：： CreateTearOffBar](#createtearoffbar)|建立可停駐的卸載色軸。  (覆寫 [CMFCPopupMenu：： CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)。 ) |
|[CMFCColorPopupMenu：： GetMenuBar](#getmenubar)|傳回內嵌在快顯功能表中的 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 。  (覆寫 [CMFCPopupMenu：： GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。 ) |
|`CMFCColorPopupMenu::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|
|[CMFCColorPopupMenu：： SetPropList](#setproplist)|設定内嵌物件的屬性方格控制項物件 `CMFCColorBar` 。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`m_bEnabledInCustomizeMode`|決定是否要顯示色軸的布林值。|
|`m_wndColorBar`|`CMFCColorBar`提供色彩選取的物件。|

### <a name="remarks"></a>備註

此類別會繼承類別的快顯功能表功能 `CMFCPopupMenu` ，並管理 `CMFCColorBar` 提供色彩選取的物件。 當工具列架構處於自訂模式，且 `m_bEnabledInCustomizeMode` 成員設為 FALSE 時，不會顯示色軸物件。 如需自訂模式的詳細資訊，請參閱 [CMFCToolBar：： IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

如需的詳細資訊 `CMFCColorBar` ，請參閱 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxcolorpopupmenu。h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a> CMFCColorPopupMenu：： CMFCColorPopupMenu

建構 `CMFCColorPopupMenu` 物件。

```
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    int nHorzDockRows,
    int nVertDockColumns,
    COLORREF colorAutomatic,
    UINT uiCommandID,
    BOOL bStdColorDlg = FALSE);

CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic);

CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,
    const CArray<COLORREF, COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nID);
```

### <a name="parameters"></a>參數

*顏色*<br/>
在架構顯示在快顯功能表上的色彩陣列。

*color*<br/>
在預設選取的色彩。

*lpszAutoColor*<br/>
在 *自動* (預設) 色彩按鈕的文字標籤，或 Null。

[自動] 按鈕的標準標籤是 [ **自動**]。

*lpszOtherColor*<br/>
在 *另* 一個按鈕的文字標籤，其會顯示更多色彩選擇或 Null。

另一個按鈕的標準標籤是 [其他 **色彩**] .。。

*lpszDocColors*<br/>
在檔色彩按鈕的文字標籤。 檔色彩調色板會列出檔目前使用的所有色彩。

*lstDocColors*<br/>
在檔目前使用的色彩清單。

*nColumns*<br/>
在色彩陣列的資料行數目。

*nHorzDockRows*<br/>
在當色軸水準停駐時，此資料列的數目。

*nVertDockColumns*<br/>
在當色軸垂直停駐時，所擁有的資料行數目。

*colorAutomatic*<br/>
在當您按一下 [自動] 按鈕時，架構所套用的預設色彩。

*uiCommandID*<br/>
在色 bar 控制項命令識別碼。

*bStdColorDlg*<br/>
在指出是否要顯示標準系統色彩對話方塊或 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 對話方塊的布林值。

*pParentBtn*<br/>
在父按鈕的指標。

*nID*<br/>
在命令識別碼。

### <a name="remarks"></a>備註

每個多載的函式都會將 `m_bEnabledInCustomizeMode` 成員設為 FALSE。

### <a name="example"></a>範例

下列範例示範如何建立 `CMFCColorPopupMenu` 物件。

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a> CMFCColorPopupMenu：： CreateTearOffBar

建立可停駐的卸載色軸。

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*pWndMain*\
在卸載列之父視窗的指標。

*uiID*\
在清除列的命令識別碼。

*lpszName*\
在清除橫條的視窗文字。

### <a name="return-value"></a>傳回值

新退出控制列物件的指標。

### <a name="remarks"></a>備註

這個方法會建立 [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md) 物件，並將它轉換成 [CPane 類別](../../mfc/reference/cpane-class.md) 指標。 您可以使用[MFC 類別物件的類型轉換](../../mfc/reference/type-casting-of-mfc-class-objects.md)中所述的其中一個轉換宏，將此值轉換回[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)指標。

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a> CMFCColorPopupMenu：： GetMenuBar

傳回內嵌在快顯功能表中的 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 。

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>傳回值

內嵌的指標 `CMFCPopupMenuBar` 。

### <a name="remarks"></a>備註

色彩快顯功能表具有內嵌的 [CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md) 物件。 如果您的應用程式使用不同的內嵌類型，請在衍生類別中覆寫這個方法。

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a> CMFCColorPopupMenu：： SetPropList

設定内嵌物件的屬性方格控制項物件 `CMFCColorBar` 。

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>參數

*pWndList*<br/>
在屬性方格控制項物件的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
