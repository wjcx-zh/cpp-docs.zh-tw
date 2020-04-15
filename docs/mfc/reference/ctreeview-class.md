---
title: CTreeView 類別
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373298"
---
# <a name="ctreeview-class"></a>CTreeView 類別

使用 MFC 的文檔檢視體系結構簡化了樹控件和[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)的類,該類封裝了樹控制功能。

## <a name="syntax"></a>語法

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTree檢視:CTreeView](#ctreeview)|建構 `CTreeView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTreeView::獲取樹譜](#gettreectrl)|返回與視圖關聯的樹控件。|

## <a name="remarks"></a>備註

有關此體系結構的詳細資訊,請參閱[CView](../../mfc/reference/cview-class.md)類的概述以及其中引用的交叉引用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>需求

**標題:** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTree檢視:CTreeView

建構 `CTreeView` 物件。

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView::獲取樹譜

返回對與檢視關聯的樹控件的引用。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>另請參閱

[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)
