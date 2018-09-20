---
title: CMFCColorPopupMenu 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e32c6d167fbccf1d2217aa4c187944b8018acdd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432499"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 類別

代表使用者使用文件或應用程式中選取色彩的快顯功能表。

## <a name="syntax"></a>語法

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|建構 `CMFCColorPopupMenu` 物件。|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|建立可停駐 tear-off 色彩列。 (覆寫[CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)。)|
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|傳回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) ，內嵌於快顯功能表。 (覆寫[CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。)|
|`CMFCColorPopupMenu::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCColorPopupMenu::SetPropList](#setproplist)|設定的屬性方格控制項物件嵌入的`CMFCColorBar`物件。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`m_bEnabledInCustomizeMode`|布林值，決定是否要顯示色軸。|
|`m_wndColorBar`|`CMFCColorBar`提供色彩選取範圍的物件。|

### <a name="remarks"></a>備註

這個類別繼承的快顯功能表功能`CMFCPopupMenu`類別，並管理`CMFCColorBar`提供色彩選取範圍的物件。 當工具列 framework 處於自訂模式和`m_bEnabledInCustomizeMode`成員設定為 FALSE，不會顯示色軸物件。 如需有關自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

如需詳細資訊`CMFCColorBar`，請參閱 < [CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcolorpopupmenu.h

##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu

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

*色彩*<br/>
[in]陣列，架構會顯示快顯功能表的色彩。

*色彩*<br/>
[in]選取的預設色彩。

*lpszAutoColor*<br/>
[in]文字標籤*自動*（預設值） 的色彩按鈕，則為 NULL。

標準自動按鈕的標籤**自動**。

*lpszOtherColor*<br/>
[in]文字標籤*其他* 按鈕，以顯示更多的色彩選擇，或 NULL。

[其他] 按鈕的標準標籤是**其他色彩...**.

*lpszDocColors*<br/>
[in]文件的 [色彩] 按鈕的文字標籤。 文件色彩調色盤會列出所有的文件目前使用的色彩。

*lstDocColors*<br/>
[in]一份文件目前使用的色彩。

*nColumns*<br/>
[in]具有色彩陣列的資料行數目。

*nHorzDockRows*<br/>
[in]可在色軸水平的停駐時的資料列數目。

*nVertDockColumns*<br/>
[in]可在色軸垂直的停駐時的資料行數目。

*colorAutomatic*<br/>
[in]當您按一下 [自動] 按鈕時，架構會套用預設色彩。

*uiCommandID*<br/>
[in]色軸控制項命令識別碼。

*bStdColorDlg*<br/>
[in]布林值，指出是否要顯示標準系統的 [色彩] 對話方塊或[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  對話方塊。

*pParentBtn*<br/>
[in]父代按鈕指標。

*nID*<br/>
[in]命令 id。

### <a name="remarks"></a>備註

每個多載建構函式集`m_bEnabledInCustomizeMode`成員設為 FALSE。

### <a name="example"></a>範例

下列範例示範如何建構`CMFCColorPopupMenu`物件。

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar

建立可停駐 tear-off 色彩列。

```
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,
    UINT uiID,
    LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pWndMain*|[in]Tear-off 列的父視窗的指標。|
|*uiID*|[in]Tear-off 列的命令識別碼。|
|*lpszName*|[in]Tear-off 列視窗文字。|

### <a name="return-value"></a>傳回值

新的分割控制列物件的指標。

### <a name="remarks"></a>備註

這個方法會建立[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)物件，並將它轉換成[CPane 類別](../../mfc/reference/cpane-class.md)指標。 您可以將此值轉換回[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)使用其中一種中所述的轉換巨集的指標[型別轉型的 MFC 類別物件](../../mfc/reference/type-casting-of-mfc-class-objects.md)。

##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar

傳回[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) ，內嵌於快顯功能表。

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>傳回值

內嵌的指標`CMFCPopupMenuBar`。

### <a name="remarks"></a>備註

色彩的快顯功能表還包含內嵌[CMFCPopupMenuBar 類別](../../mfc/reference/cmfcpopupmenubar-class.md)物件。 如果您的應用程式會使用不同的內嵌的類型，請覆寫這個方法在衍生類別中。

##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList

設定的屬性方格控制項物件嵌入的`CMFCColorBar`物件。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>參數

*pWndList*<br/>
[in]屬性方格控制項物件的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
