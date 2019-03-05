---
title: CMFCBaseToolBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 7a6ccdaf3d78b9973505dd4e90ca76f671fce889
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265375"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar 類別

工具列的基底類別。

## <a name="syntax"></a>語法

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|預設建構函式。|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|傳回固定模式。 (覆寫[cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode)。)|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|傳回的最小的工具列。 (覆寫[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|在窗格的父代變更之後，由架構呼叫。 (覆寫[CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent)。)|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxbasetoolbar.h

##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode

傳回固定模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>傳回值

停駐的模式。

##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize

傳回的最小的工具列。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*size*<br/>
[out]工具列的大小下限。

##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent

在窗格的父代變更之後，由架構呼叫。

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>參數

*pWndOldParent*<br/>
[in]先前的父視窗的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
