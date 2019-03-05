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
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284745"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 類別

提供下拉式工具列和下拉式工具列按鈕的下拉式清單框架視窗功能。

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
|[CMFCDropDownFrame::Create](#create)|建立 `CMFCDropDownFrame` 物件。|
|`CMFCDropDownFrame::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|擷取在下拉式清單畫面格的父功能表列。|
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|擷取父快顯功能表的下拉式清單畫面格。|
|`CMFCDropDownFrame::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|重新置放在下拉式清單畫面格。|
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|設定是否會自動終結子下拉式工具列視窗。|

### <a name="remarks"></a>備註

這個類別不是直接從您的程式碼使用。

架構會使用這個類別提供以框架行為`CMFCDropDownToolbar`和`CMFCDropDownToolbarButton`類別。 如需有關這些類別的詳細資訊，請參閱 < [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)並[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>範例

下列範例示範如何擷取指標`CMFCDropDownFrame`物件從`CFrameWnd`類別，以及如何設定子下拉式工具列視窗會自動終結。

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdropdowntoolbar.h

##  <a name="create"></a>  CMFCDropDownFrame::Create

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
|*pWndParent*|[in]父框架的視窗下拉式清單。|
|*x*|[in]位置清單向下畫面格的水平螢幕座標。|
|*y*|[in]位置清單向下畫面格的垂直螢幕座標。|
|*pWndOriginToolbar*|[in]會顯示這個方法會使用來填入新的下拉式清單的畫面格物件的下拉式按鈕的工具列。|

### <a name="return-value"></a>傳回值

如果已成功建立下拉式框架;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會呼叫基底[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法用來建立 WS_POPUP 樣式的下拉式清單框架視窗。 在下拉式清單框架視窗會出現在指定的螢幕座標。 如果這個方法會失敗[CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)方法會傳回 FALSE。

`CMFCDropDownFrame`類別會建立一份提供的`CMFCDropDownToolBar`參數。 這個方法會複製按鈕影像和按鈕的狀態，從`pWndOriginToolbar`參數來`m_pWndOriginToolbar`資料成員。

##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar

擷取在下拉式清單畫面格的父功能表列。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>傳回值

父功能表列下拉式清單的範圍內，則為 NULL，如果沒有父代框架指標。

### <a name="remarks"></a>備註

這個方法會擷取父功能表列，從 [父] 按鈕。 如果下拉式清單畫面格沒有父代按鈕或 [父] 按鈕具有任何父功能表列，這個方法會傳回 NULL。

##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu

擷取父快顯功能表的下拉式清單畫面格。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>傳回值

父下拉式選單，下拉式清單的範圍內，則為 NULL，如果沒有父代框架指標。

### <a name="remarks"></a>備註

這個方法會擷取從父代按鈕的父功能表。 如果下拉式清單畫面格沒有父代按鈕或 [父] 按鈕功能表沒有父代，這個方法會傳回 NULL。

##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout

重新置放在下拉式清單畫面格。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*bNotify*|[in]未使用。|

### <a name="remarks"></a>備註

建立下拉式框架或父視窗大小調整時，架構會呼叫這個方法。 這個方法會計算的位置和大小的下拉式清單框架使用的位置和父視窗的大小。

##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy

設定是否會自動終結子下拉式工具列視窗。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
[in]為 true，則會自動終結相關聯的下拉工具列的視窗;否則為 FALSE。

### <a name="remarks"></a>備註

如果*bAutoDestroy*為 TRUE，則`CMFCDropDownFrame`解構函式會終結相關聯的下拉工具列的視窗。 預設值為 TRUE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
