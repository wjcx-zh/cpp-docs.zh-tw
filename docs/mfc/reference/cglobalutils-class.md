---
title: CGlobalUtils 類別
ms.date: 10/18/2018
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
ms.openlocfilehash: dbac56ea7efca98218133b23657f8508ea6bac28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752912"
---
# <a name="cglobalutils-class"></a>CGlobalUtils 類別

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CGlobalUtils
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CGlobalUtils::CanBeAttached](#canbeattached)||
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||
|[CGlobalUtils::CheckAlignment](#checkalignment)||
|[CGlobalUtils::CyFromString](#cyfromstring)||
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||
|[CGlobalUtils::FlipRect](#fliprect)||
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||
|[CGlobalUtils::GetWndIcon](#getwndicon)||
|[CGlobalUtils::SetNewParent](#setnewparent)||
|[CGlobalUtils::StringFromCy](#stringfromcy)||
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||

## <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CGlobalUtils](../../mfc/reference/cglobalutils-class.md)

## <a name="requirements"></a>需求

**標題:** afxglobalutils.h

## <a name="cglobalutilsadjustrecttoworkarea"></a><a name="adjustrecttoworkarea"></a>CGlobalUtils::調整RecttoWork區域

```cpp
void AdjustRectToworkArea(
    CRect& rect,
    CRect* pRectDelta = NULL);
```

### <a name="parameters"></a>參數

[進出]*rect*<br/>
[在]*普雷克拉德爾塔*<br/>

### <a name="remarks"></a>備註

## <a name="cglobalutilscalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CGlobalUtils::鈣化物多克

```cpp
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,
    CWnd* pWndTodock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>參數

[在]*酒吧容器管理員*<br/>

[在]*普恩德托多克*<br/>

[在]*ptMouse*<br/>

[出]*rectResult*<br/>

[出]*bDrawTab*<br/>

[出]*ppTargetBar*<br/>

### <a name="remarks"></a>備註

## <a name="cglobalutilscanbeattached"></a><a name="canbeattached"></a>CGlobalUtils::可附加

```
BOOL CanBeAttached(CWnd* pWnd) const;
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilscanpanebeinfloatingmultipaneframewnd"></a><a name="canpanebeinfloatingmultipaneframewnd"></a>CGlobalUtils::坎帕內貝在漂浮的多窗格框架

```
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilscheckalignment"></a><a name="checkalignment"></a>CGlobalUtils:檢查對齊

```
BOOL CheckAlignment(
    CPoint point,
    CBasePane* pBar,
    int nSensitivity,
    const CDockingManager* pDockManager,
    BOOL bOuterEdge,
    DWORD& dwAlignment,
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,
    LPCRECT lpRectBounds = NULL) const;
```

### <a name="parameters"></a>參數

[在]*點*<br/>

[在]*pBar*<br/>

[在]*nSensitivity*<br/>

[在]*pDock 管理員*<br/>

[在]*bouterEdge*<br/>

[出]*dwalignment*<br/>

[在]*dwEnabledDockBars*<br/>

[在]*lpRectBounds*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilscyfromstring"></a><a name="cyfromstring"></a>CGlobalUtils::CyFromString

```
BOOL CyFromString(
    CY& cy,
    LPCTSTR psz);
```

### <a name="parameters"></a>參數

[出]*cy*<br/>

[在]*psz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsdecimalfromstring"></a><a name="decimalfromstring"></a>CGlobalUtils::D從弦

```
BOOL DecimalFromString(
    DECIMAL& decimal,
    LPCTSTR psz);
```

### <a name="parameters"></a>參數

[出]*十進位*<br/>

[在]*psz*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsfliprect"></a><a name="fliprect"></a>CGlobalUtils::翻轉

```cpp
void FlipRect(
    CRect& rect,
    int nDegrees);
```

### <a name="parameters"></a>參數

[進出]*rect*<br/>
[在]*n 度*<br/>

### <a name="remarks"></a>備註

## <a name="cglobalutilsforceadjustlayout"></a><a name="forceadjustlayout"></a>CGlobalUtils::強制調整佈局

```cpp
void ForceAdjustLayout(
    CDockingManager* pDockManager,
    BOOL bForce = FALSE,
    BOOL bForceInvisible = FALSE);
```

### <a name="parameters"></a>參數

[進出]*pDock 管理員*<br/>

[在]*bForce*<br/>

[在]*bForce 隱形*<br/>

### <a name="remarks"></a>備註

## <a name="cglobalutilsgetdockingmanager"></a><a name="getdockingmanager"></a>CGlobalUtils::取得延伸管理員

```
CDockingManager* GetDockingManager(CWnd* pWnd);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsgetoppositealignment"></a><a name="getoppositealignment"></a>CGlobalUtils:取得相反對齊

```
DWORD GetOppositeAlignment(DWORD dwAlign);
```

### <a name="parameters"></a>參數

[在]*dwalign*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsgetpaneandalignfrompoint"></a><a name="getpaneandalignfrompoint"></a>CGlobalUtils::取得窗格和從點對齊

```
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,
    CPoint pt,
    CDockablePane** ppTargetControlBar,
    DWORD& dwAlignment,
    BOOL& bTabArea,
    BOOL& bCaption);
```

### <a name="parameters"></a>參數

[在]*酒吧容器管理員*<br/>

[在]*pt*<br/>

[出]*ppTarget 控制列*<br/>

[出]*dwalignment*<br/>

[出]*bTabArea*<br/>

[出]*bCaption*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsgetwndicon"></a><a name="getwndicon"></a>CGlobalUtils:取得WndIcon

```
HICON GetWndIcon(CWnd* pWnd);
```

### <a name="parameters"></a>參數

[在]*pwnd*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilssetnewparent"></a><a name="setnewparent"></a>CGlobalUtils::設置新家長

```cpp
void SetNewParent(
    CObList& lstControlBars,
    CWnd* pNewParent,
    BOOL bCheckVisibility = TRUE);
```

### <a name="parameters"></a>參數

[在]*lstControlBars*<br/>

[在]*p 新家長*<br/>

[在]*b 檢查可見度*<br/>

### <a name="remarks"></a>備註

## <a name="cglobalutilsstringfromcy"></a><a name="stringfromcy"></a>CGlobalUtils::弦從西

```
BOOL StringFromCy(
    CString& str,
    CY& cy);
```

### <a name="parameters"></a>參數

[出]*斯特*<br/>

[在]*cy*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cglobalutilsstringfromdecimal"></a><a name="stringfromdecimal"></a>CGlobalUtils:從十進位的字串

```
BOOL StringFromDecimal(
    CString& str,
    DECIMAL& decimal);
```

### <a name="parameters"></a>參數

[出]*斯特*<br/>

[在]*十進位*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
