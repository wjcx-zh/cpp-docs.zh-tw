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
ms.openlocfilehash: 2fbaf99e4cc9bcbecf1a94012713b34e986f7ecb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375589"
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
|[可停靠的窗格配接器::獲取包裝](#getwrappedwnd)|傳回已包裝的視窗。|
|[CDockablePaneAdapter::LoadState](#loadstate)|(覆蓋[可停靠窗格::載入狀態](cdockablepane-class.md#loadstate)。)|
|[CDockablePaneAdapter::SaveState](#savestate)|(覆蓋[可停靠窗格::儲存狀態](cdockablepane-class.md)。)|
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||

## <a name="remarks"></a>備註

通常,當您使用[CMFCBaseTabCtrl::addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)或[CMFCBaseTabCtrl::插入選項卡](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)方法時,框架會實例化此類的物件。

如果要自定義`CDockablePaneAdapter`行為,只需從該類派生一個新類,並使用 CMFCBaseTabCtrl 將執行時類資訊設置為選項卡式視窗[::設定 DockingBarWrapperRTC](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)\
•&nbsp;[CMD目標](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[Cwnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[可裝板](../../mfc/reference/cdockablepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;•&nbsp;[可裝板式窗格配接器](../../mfc/reference/cdockablepaneadapter-class.md)

## <a name="requirements"></a>需求

**標題:** afxDock 可窗格配接器.h

## <a name="cdockablepaneadaptergetwrappedwnd"></a><a name="getwrappedwnd"></a>可停靠的窗格配接器::獲取包裝

返回可停靠窗格適配器的基礎視窗。

```
virtual CWnd* GetWrappedWnd() const;
```

### <a name="return-value"></a>傳回值

指向包裝視窗的指標。

### <a name="remarks"></a>備註

使用此函數可以訪問包裝視窗。

## <a name="cdockablepaneadapterloadstate"></a><a name="loadstate"></a>可停靠窗格配接器::載入狀態

從註冊表載入窗格的狀態。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]設定檔名稱。

*nIndex*<br/>
[在]配置檔索引。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockablepaneadaptersavestate"></a><a name="savestate"></a>可停靠窗格配接器::儲存狀態

將窗格的狀態保存到註冊表。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]設定檔名稱。

*nIndex*<br/>
[在]配置檔索引(預設為視窗的控制ID)。

*uiID*<br/>
[在]窗格 ID。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cdockablepaneadaptersetwrappedwnd"></a><a name="setwrappedwnd"></a>可停靠窗格配接器::套包

設置可停靠窗格適配器的基礎視窗。

```
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
[在]指向視窗的指標,用於窗格適配器換行。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
