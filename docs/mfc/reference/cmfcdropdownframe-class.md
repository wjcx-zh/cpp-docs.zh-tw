---
title: CMFCDropDownFrame 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: a5e95efe1880f1177490d55988ca1fe42c606b15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367545"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 類別

為下拉工具列和下拉工具列按鈕提供下拉框架視窗功能。

## <a name="syntax"></a>語法

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|`CMFCDropDownFrame::CMFCDropDownFrame`|預設建構函式。|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|解構函式。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC 下線框架:建立](#create)|建立 `CMFCDropDownFrame` 物件。|
|`CMFCDropDownFrame::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFC下拉框架:獲取父選單欄](#getparentmenubar)|檢索下拉框架的父功能表欄。|
|[CMFC下線框架:獲取家長彈出功能表](#getparentpopupmenu)|檢索下拉框架的父彈出式功能表。|
|`CMFCDropDownFrame::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC向下幀:Recalclayout](#recalclayout)|重新置放下拉框架。|
|[CMFC下拉幀::設置自動銷毀](#setautodestroy)|設置子下拉工具列視窗是否自動銷毀。|

### <a name="remarks"></a>備註

這個類別並不適合直接從您的程式碼使用。

框架使用此類向`CMFCDropDownToolbar``CMFCDropDownToolbarButton`和 類提供幀行為。 有關這些類別的詳細資訊,請參閱[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)與[CMFCDropDown 下拉工具列按鈕類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>範例

下面的示例演示如何從`CMFCDropDownFrame``CFrameWnd`類檢索指向物件的指標,以及如何將子下拉工具列窗口設置為自動銷毀。

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFC 下線框架](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a>CMFC 下線框架:建立

建立 `CMFCDropDownFrame` 物件。

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*pwnd 父級*|[在]下拉框架的父視窗。|
|*X.*|[在]下下幀位置的水平螢幕座標。|
|*Y*|[在]向下幀位置的垂直螢幕座標。|
|*pWndOrigin工具列*|[在]具有此方法用於填充新下拉框架物件的下拉按鈕的工具列。|

### <a name="return-value"></a>傳回值

如果成功創建了下拉框架,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

此方法調用基本[CMiniFrameWnd:createEx](../../mfc/reference/cminiframewnd-class.md#createex)方法,以創建具有WS_POPUP樣式的下拉框架視窗。 下拉框架視窗顯示在指定的螢幕座標處。 如果[CMiniFrameWnd:createEx](../../mfc/reference/cminiframewnd-class.md#createex)方法返回 FALSE,則此方法將失敗。

類別`CMFCDropDownFrame`創建提供的`CMFCDropDownToolBar`參數的複本。 此方法將按鈕圖像和按鈕狀態從`pWndOriginToolbar`參數複製`m_pWndOriginToolbar`到資料成員。

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a>CMFC下拉框架:獲取父選單欄

檢索下拉框架的父功能表欄。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>傳回值

指向下拉框架的父功能表欄的指標,如果框架沒有父菜單,則指向 NULL。

### <a name="remarks"></a>備註

此方法從父按鈕檢索父功能表欄。 如果下拉框架沒有父按鈕或父按鈕沒有父功能表欄,則此方法返回 NULL。

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFC下線框架:獲取家長彈出功能表

檢索下拉框架的父彈出式功能表。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>傳回值

指向下拉框架的父下拉菜單的指標,如果框架沒有父級,則指向 NULL。

### <a name="remarks"></a>備註

此方法從父按鈕檢索父功能表。 如果下拉框架沒有父按鈕或父按鈕沒有父功能表,則此方法將返回 NULL。

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a>CMFC向下幀:Recalclayout

重新置放下拉框架。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*b 通知*|[在]閑置。|

### <a name="remarks"></a>備註

創建下拉框架或調整父視窗大小時,框架將調用此方法。 此方法使用父視窗的位置和大小計算下拉框架的位置和大小。

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a>CMFC下拉幀::設置自動銷毀

設置子下拉工具列視窗是否自動銷毀。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAuto銷毀*<br/>
[在]TRUE 自動銷毀關聯的下拉工具列視窗;否則,FALSE。

### <a name="remarks"></a>備註

如果*bAuto 銷毀*`CMFCDropDownFrame`為 TRUE, 則析構函數將銷毀關聯的下拉工具列視窗。 預設值為 TRUE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
