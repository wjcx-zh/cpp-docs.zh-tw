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
ms.openlocfilehash: d99dae9d8e7eca96c736a33621f0b544f1962f0f
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560890"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame 類別

提供下拉式清單方塊和下拉式工具列按鈕的下拉式框架視窗功能。

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
|[CMFCDropDownFrame：： Create](#create)|建立 `CMFCDropDownFrame` 物件。|
|`CMFCDropDownFrame::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCDropDownFrame：： GetParentMenuBar](#getparentmenubar)|抓取下拉式框架的上層功能表列。|
|[CMFCDropDownFrame：： GetParentPopupMenu](#getparentpopupmenu)|抓取下拉式框架的上層快顯功能表。|
|`CMFCDropDownFrame::GetThisClass`|由架構用來取得與這個類別類型相關聯之 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件的指標。|
|[CMFCDropDownFrame：： RecalcLayout](#recalclayout)|重新置放下拉清單架。|
|[CMFCDropDownFrame：： SetAutoDestroy](#setautodestroy)|設定是否要自動終結子下拉式工具列視窗。|

### <a name="remarks"></a>備註

這個類別並不適合直接從您的程式碼使用。

架構會使用這個類別來提供和類別的框架 `CMFCDropDownToolbar` 行為 `CMFCDropDownToolbarButton` 。 如需這些類別的詳細資訊，請參閱 [CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md) 和 [CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)。

## <a name="example"></a>範例

下列範例示範如何 `CMFCDropDownFrame` 從類別取出物件的指標 `CFrameWnd` ，以及如何將子下拉式工具列視窗設定為自動終結。

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxdropdowntoolbar.h

## <a name="cmfcdropdownframecreate"></a><a name="create"></a> CMFCDropDownFrame：： Create

建立 `CMFCDropDownFrame` 物件。

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>參數

*pWndParent*\
在下拉式框架的父視窗。

*X*\
在向下框架位置的水準螢幕座標。

*Y*\
在向下框架位置的垂直螢幕座標。

*pWndOriginToolbar*\
在具有下拉式按鈕的工具列，這個方法會使用這個按鈕來填入新的下拉式框架物件。

### <a name="return-value"></a>傳回值

如果已成功建立下拉式框架，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會呼叫基底 [CMiniFrameWnd：： CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) 方法，以 WS_POPUP 樣式來建立下拉式框架視窗。 下拉式框架視窗會出現在指定的螢幕座標上。 如果 [CMiniFrameWnd：： CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) 方法傳回 FALSE，這個方法將會失敗。

`CMFCDropDownFrame`類別會建立所提供參數的複本 `CMFCDropDownToolBar` 。 這個方法會從參數將按鈕影像和按鈕狀態複製 `pWndOriginToolbar` 到 `m_pWndOriginToolbar` 資料成員。

## <a name="cmfcdropdownframegetparentmenubar"></a><a name="getparentmenubar"></a> CMFCDropDownFrame：： GetParentMenuBar

抓取下拉式框架的上層功能表列。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>傳回值

下拉式框架的上層功能表列的指標，如果框架沒有父代，則為 Null。

### <a name="remarks"></a>備註

這個方法會從父按鈕抓取上層功能表列。 如果下拉式框架沒有父按鈕，或父按鈕沒有上層功能表列，則這個方法會傳回 Null。

## <a name="cmfcdropdownframegetparentpopupmenu"></a><a name="getparentpopupmenu"></a> CMFCDropDownFrame：： GetParentPopupMenu

抓取下拉式框架的上層快顯功能表。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>傳回值

下拉式框架之父下拉式功能表的指標，如果框架沒有父代，則為 Null。

### <a name="remarks"></a>備註

這個方法會從父按鈕抓取父功能表。 如果下拉式框架沒有父按鈕，或父按鈕沒有父功能表，則這個方法會傳回 Null。

## <a name="cmfcdropdownframerecalclayout"></a><a name="recalclayout"></a> CMFCDropDownFrame：： RecalcLayout

重新置放下拉清單架。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>參數

*bNotify*\
在閒置。

### <a name="remarks"></a>備註

當建立下拉式框架或調整父視窗大小時，架構會呼叫這個方法。 這個方法會使用父視窗的位置和大小，計算下拉式框架的位置和大小。

## <a name="cmfcdropdownframesetautodestroy"></a><a name="setautodestroy"></a> CMFCDropDownFrame：： SetAutoDestroy

設定是否要自動終結子下拉式工具列視窗。

```cpp
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*bAutoDestroy*<br/>
在TRUE 表示自動終結相關聯的下拉式工具列視窗;否則為 FALSE。

### <a name="remarks"></a>備註

如果 *bAutoDestroy* 為 TRUE，則此函式會終結 `CMFCDropDownFrame` 相關聯的下拉式工具列視窗。 預設值為 TRUE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar 類別](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
