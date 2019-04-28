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
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323592"
---
# <a name="ctreeview-class"></a>CTreeView 類別

簡化了使用和的樹狀目錄控制項[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)，封裝樹狀目錄控制項功能，並使用 MFC 的文件檢視架構的類別。

## <a name="syntax"></a>語法

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|建構 `CTreeView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|傳回與檢視相關聯的樹狀目錄控制項。|

## <a name="remarks"></a>備註

如需有關此架構的詳細資訊，請參閱的概觀[CView](../../mfc/reference/cview-class.md)類別，並那里提及的交互參考。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>需求

**標頭：** afxcview.h

##  <a name="ctreeview"></a>  CTreeView::CTreeView

建構 `CTreeView` 物件。

```
CTreeView();
```

##  <a name="gettreectrl"></a>  CTreeView::GetTreeCtrl

傳回與檢視相關聯的樹狀目錄控制項的參考。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>另請參閱

[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl 類別](../../mfc/reference/ctreectrl-class.md)
