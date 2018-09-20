---
title: CTreeView 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a760e567718ad7a485ebe469903c7cbd566daccc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375394"
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
|[Ctreeview:: Gettreectrl](#gettreectrl)|傳回與檢視相關聯的樹狀目錄控制項。|

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

##  <a name="gettreectrl"></a>  Ctreeview:: Gettreectrl

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
