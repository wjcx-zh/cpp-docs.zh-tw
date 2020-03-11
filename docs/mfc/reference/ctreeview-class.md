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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883989"
---
# <a name="ctreeview-class"></a>CTreeView 類別

透過 MFC 的檔查看架構，簡化樹狀目錄控制項及[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)（封裝樹狀目錄控制項功能的類別）的使用。

## <a name="syntax"></a>語法

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTreeView：： CTreeView](#ctreeview)|建構 `CTreeView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTreeView：： GetTreeCtrl](#gettreectrl)|傳回與此視圖相關聯的樹狀目錄控制項。|

## <a name="remarks"></a>備註

如需此架構的詳細資訊，請參閱[CView](../../mfc/reference/cview-class.md)類別的總覽和此處提及的交互參考。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>需求

**標頭：** afxcview。h

##  <a name="ctreeview"></a>CTreeView：： CTreeView

建構 `CTreeView` 物件。

```
CTreeView();
```

##  <a name="gettreectrl"></a>CTreeView：： GetTreeCtrl

傳回與此視圖相關聯之樹狀控制項的參考。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>另請參閱

[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CCtrlView 類別](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)
