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
ms.openlocfilehash: 027fe8569ff133bb3f348c9d0607f19c6d778c4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367835"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar 類別

工具欄的基類。

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
|[CMFCBase工具列:取得停靠模式](#getdockingmode)|傳回固定模式。 (覆寫[CBasePane:取得停靠模式](../../mfc/reference/cbasepane-class.md#getdockingmode)。|
|[CMFCBase工具列:取得最小值](#getminsize)|傳回工具列的最小大小。 ( 覆[寫 CPane: 取得最小值](../../mfc/reference/cpane-class.md#getminsize)。|
|[CMFCBase工具列:在更改后家長](#onafterchangeparent)|在窗格的父級更改後由框架調用。 (覆寫[CBasePane:之後更改父項目](../../mfc/reference/cbasepane-class.md#onafterchangeparent)。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBase工具列](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxbasetoolbar.h

## <a name="cmfcbasetoolbargetdockingmode"></a><a name="getdockingmode"></a>CMFCBase工具列:取得停靠模式

傳回固定模式。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>傳回值

停靠模式。

## <a name="cmfcbasetoolbargetminsize"></a><a name="getminsize"></a>CMFCBase工具列:取得最小值

傳回工具列的最小大小。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>參數

*大小*<br/>
[出]工具列的最小大小。

## <a name="cmfcbasetoolbaronafterchangeparent"></a><a name="onafterchangeparent"></a>CMFCBase工具列:在更改后家長

在窗格的父級更改後由框架調用。

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>參數

*pWndOld 父級*<br/>
[在]指向上一個父視窗的指標。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
