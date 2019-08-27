---
title: CDockablePaneAdapter 類別
ms.date: 11/04/2016
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
ms.openlocfilehash: 88c125c63f9dbfe272f5d543e996366575fc533b
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866228"
---
# <a name="cdockablepaneadapter-class"></a>CDockablePaneAdapter 類別

提供 `CWnd`衍生窗格的停駐支援。

## <a name="syntax"></a>語法

```
class CDockablePaneAdapter : public CDockablePane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|傳回已包裝的視窗。|
|[CDockablePaneAdapter::LoadState](#loadstate)|(覆寫[CDockablePane:: LoadState](cdockablepane-class.md#loadstate)。)|
|[CDockablePaneAdapter::SaveState](#savestate)|(覆寫[CDockablePane:: SaveState](cdockablepane-class.md)。)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>備註

通常, 當您使用[CMFCBaseTabCtrl:: AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或[CMFCBaseTabCtrl:: InsertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法時, 架構會具現化這個類別的物件。

如果您想要自訂`CDockablePaneAdapter`行為, 只需從它衍生新類別, 然後使用[CMFCBaseTabCtrl:: setdockingbarwrapperrtc 類別](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)將執行時間類別資訊設定為索引標籤式視窗。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp; [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CDockablePane](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp; [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>需求

**標頭:** afxDockablePaneAdapter。h

##  <a name="getwrappedwnd"></a>CDockablePaneAdapter:: GetWrappedWnd

傳回可停駐窗格介面卡的基礎視窗。

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>傳回值

已包裝視窗的指標。

### <a name="remarks"></a>備註

使用此函式來存取已包裝的視窗。

##  <a name="loadstate"></a>  CDockablePaneAdapter::LoadState

從登錄載入窗格的狀態。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在設定檔名稱。

*nIndex*<br/>
在設定檔索引。

*uiID*<br/>
在窗格識別碼。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="savestate"></a>CDockablePaneAdapter:: SaveState

將窗格的狀態儲存至登錄。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在設定檔名稱。

*nIndex*<br/>
在設定檔索引 (預設為視窗的控制項 ID)。

*uiID*<br/>
在窗格識別碼。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="setwrappedwnd"></a>CDockablePaneAdapter:: SetWrappedWnd

設定可停駐窗格介面卡的基礎視窗。

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
在要包裝之窗格介面卡的視窗指標。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
