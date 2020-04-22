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
ms.openlocfilehash: 901a44c8f5fdecd1b277ebdecc995722a3afe9a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752488"
---
# <a name="cmfccolorpopupmenu-class"></a>CMFCColorPopupMenu 類別

表示使用者用於選擇文檔或應用程式中顏色的彈出式功能表。

## <a name="syntax"></a>語法

```
class CMFCColorPopupMenu : public CMFCPopupMenu
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[CMFC顏色彈出選單::CMFC顏色彈出選單](#cmfccolorpopupmenu)|建構 `CMFCColorPopupMenu` 物件。|
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC顏色彈出選單::創建眼淚關閉欄](#createtearoffbar)|創建可停靠的撕掉顏色條。 (覆蓋[CMFC 彈出選單::建立"建立"關閉列](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar)")|
|[CMFC顏色彈出選單::獲取選單欄](#getmenubar)|返回嵌入在彈出式功能表中的[CMFCPopupMenuBar。](../../mfc/reference/cmfcpopupmenubar-class.md) (覆寫[CMFC 彈出選單::取得選單列](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar)。|
|`CMFCColorPopupMenu::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC 顏色彈出選單::設定Proplist](#setproplist)|設置嵌入`CMFCColorBar`物件的屬性網格控制物件。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|名稱|描述|
|`m_bEnabledInCustomizeMode`|確定是否顯示顏色條的布林值。|
|`m_wndColorBar`|提供`CMFCColorBar`顏色選擇的物件。|

### <a name="remarks"></a>備註

此類繼承`CMFCPopupMenu`類的彈出功能表功能,並管理提供顏色`CMFCColorBar`選擇的物件。 當工具列框架處於自定義模式且`m_bEnabledInCustomizeMode`成員設置為 FALSE 時,不會顯示顏色欄物件。 有關自定義模式的詳細資訊,請參閱[CMFCToolBar::是自定義模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)

有關 的詳細`CMFCColorBar`資訊 ,請參閱[CMFCColorBar 類別](../../mfc/reference/cmfccolorbar-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)

[CMFC 彈出選單](../../mfc/reference/cmfccolorpopupmenu-class.md)

## <a name="requirements"></a>需求

**標題:** afxcolorpopmenu.h

## <a name="cmfccolorpopupmenucmfccolorpopupmenu"></a><a name="cmfccolorpopupmenu"></a>CMFC顏色彈出選單::CMFC顏色彈出選單

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
[在]框架顯示在彈出式功能表上的顏色陣組。

*顏色*<br/>
[在]預設選擇的顏色。

*lpsz自動顏色*<br/>
[在]*自動*(預設)顏色按鈕或 NULL 的文字標籤。

自動按鈕的標準標籤是 **「自動**」。。

*lpszOther顏色*<br/>
[在]*另*一個按鈕的文字標籤,顯示更多顏色選項,或 NULL。

另一個按鈕的標準標籤是 **"更多顏色..."**

*lpszDocColors*<br/>
[在]文件顏色按鈕的文字標籤。 文件顏色調色板列出文件目前使用的所有顏色。

*lstDocColors*<br/>
[在]文件目前使用的顏色清單。

*nColumns*<br/>
[在]顏色陣列的欄數。

*n霍茲多克羅茨*<br/>
[在]顏色欄水準停靠時的行數。

*nVertDock 柱子*<br/>
[在]顏色列垂直停靠時的列數。

*顏色 自動*<br/>
[在]按下自動按鈕時框架適用的預設顏色。

*uiCommandID*<br/>
[在]顏色條控制命令 ID。

*bStdColorDlg*<br/>
[在]指示是顯示標準系統顏色對話框還是[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)對話方塊的布林。

*p 家長Btn*<br/>
[在]指向父按鈕的指標。

*nID*<br/>
[在]命令識別碼。

### <a name="remarks"></a>備註

每個重載構造函數將`m_bEnabledInCustomizeMode`成員設置為 FALSE。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCColorPopupMenu`物件。

[!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]

## <a name="cmfccolorpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFC顏色彈出選單::創建眼淚關閉欄

創建可停靠的撕掉顏色條。

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
|*普恩德·梅因*|[在]指向撕開條的父視窗。|
|*uiID*|[在]撕開欄的命令 ID。|
|*lpsz名稱*|[在]撕開欄的視窗文字。|

### <a name="return-value"></a>傳回值

指向新撕掉控制欄物件的指標。

### <a name="remarks"></a>備註

此方法創建一個[CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)物件,並將其轉換為[CPane 類](../../mfc/reference/cpane-class.md)指標。 您可以使用[MFC 類物件的類型轉換](../../mfc/reference/type-casting-of-mfc-class-objects.md)中描述的強制轉換宏之一將此值轉換回[CMFCColorBar 類](../../mfc/reference/cmfccolorbar-class.md)指標。

## <a name="cmfccolorpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFC顏色彈出選單::獲取選單欄

返回嵌入在彈出式功能表中的[CMFCPopupMenuBar。](../../mfc/reference/cmfcpopupmenubar-class.md)

```
virtual CMFCPopupMenuBar* GetMenuBar();
```

### <a name="return-value"></a>傳回值

指向嵌入`CMFCPopupMenuBar`的指標。

### <a name="remarks"></a>備註

顏色彈出式功能表具有嵌入[的 CMFCPopupMenuBar 類](../../mfc/reference/cmfcpopupmenubar-class.md)物件。 如果應用程式使用不同的嵌入類型,則在派生類中重寫此方法。

## <a name="cmfccolorpopupmenusetproplist"></a><a name="setproplist"></a>CMFC 顏色彈出選單::設定Proplist

設置嵌入`CMFCColorBar`物件的屬性網格控制物件。

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>參數

*pwndlist*<br/>
[在]指向屬性網格控件對象的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
