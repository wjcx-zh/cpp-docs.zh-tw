---
title: CMFCVisualManagerVS2005 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetDockingTabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetMDITabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetPropertyGridGroupColor
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetTabFrameColors
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawCaptionButton
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawPaneCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawSeparator
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawTab
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawToolBoxFrame
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnEraseTabsArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillHighlightedArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillMiniFrameCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnUpdateSystemColors
helpviewer_keywords:
- CMFCVisualManagerVS2005 [MFC], GetDockingTabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetMDITabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetPropertyGridGroupColor
- CMFCVisualManagerVS2005 [MFC], GetTabFrameColors
- CMFCVisualManagerVS2005 [MFC], HasOverlappedAutoHideButtons
- CMFCVisualManagerVS2005 [MFC], OnDrawAutoHideButtonBorder
- CMFCVisualManagerVS2005 [MFC], OnDrawCaptionButton
- CMFCVisualManagerVS2005 [MFC], OnDrawPaneCaption
- CMFCVisualManagerVS2005 [MFC], OnDrawSeparator
- CMFCVisualManagerVS2005 [MFC], OnDrawTab
- CMFCVisualManagerVS2005 [MFC], OnDrawToolBoxFrame
- CMFCVisualManagerVS2005 [MFC], OnEraseTabsArea
- CMFCVisualManagerVS2005 [MFC], OnFillAutoHideButtonBackground
- CMFCVisualManagerVS2005 [MFC], OnFillHighlightedArea
- CMFCVisualManagerVS2005 [MFC], OnFillMiniFrameCaption
- CMFCVisualManagerVS2005 [MFC], OnUpdateSystemColors
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
ms.openlocfilehash: b92077ecf4670dd5395296327c767ee3c7b848ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319909"
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 類別

`CMFCVisualManagerVS2005`為應用程式提供 Microsoft Visual Studio 2005 外觀。

## <a name="syntax"></a>語法

```
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCVisualManagerVS2005::獲取對接塔布邊界大小](#getdockingtabsborderssize)|框架在繪製停靠和選項卡式窗格時調用此方法。 ( 覆[寫 CMFC 視覺管理器:取得停靠選項卡邊界大小](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize)。|
|[CMFCVisualManagerVS2005::獲取MDITabsBordersSize](#getmditabsborderssize)|框架呼叫此方法以確定 MDITabs 視窗在繪製視窗之前的邊界大小。 ( 覆[寫 CMFC 視覺管理員:取得 MDITabs 邊界大小](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)。|
|[CMFCVisualManagerVS2005::獲取財產網格群彩](#getpropertygridgroupcolor)|(覆蓋[CMFC 視覺化管理員Office2003:取得屬性網格群顏色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor).)|
|[CMFC視覺管理器VS2005::取得TabFrame顏色](#gettabframecolors)|(覆蓋[CMFC 視覺化管理員Office2003:取得 TabFrame 顏色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors).)|
|[CMFCVisualManagerVS2005:: 已重疊自動隱藏按鈕](#hasoverlappedautohidebuttons)|返回自動隱藏按鈕是否在當前可視管理器中重疊。 ( 覆[寫 CMFC 視覺管理器:已重疊自動隱藏按鈕](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons)。|
|[CMFCVisualManagervs2005::在Draw自動隱藏按鈕邊框](#ondrawautohidebuttonborder)|(覆蓋[CMFCVisualManagerOffice2003:onDraw 自動隱藏按鈕邊框](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder).)|
|[CMFCVisualManagerVS2005::ONDrawCaption按鈕](#ondrawcaptionbutton)|(覆寫 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`。)|
|[CMFCVisualManagervs2005::在DrawPaneCaption](#ondrawpanecaption)|(覆蓋[CMFCVisualManagerOffice2003:onDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption).)|
|[CMFCVisualManagerVS2005:OnDrawSeator](#ondrawseparator)|(覆蓋[CMFCVisualManagerOffice2003:onDrawSeor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator).)|
|[CMFCVisualManagerVS2005::在DrawTab](#ondrawtab)|(覆蓋[CMFCVisualManagerOffice2003:onDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab).)|
|[CMFCVisualManagerVS2005::在畫工具框框](#ondrawtoolboxframe)|(覆寫[CMFC 視覺管理員:onDrawToolBox框架](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe)。|
|[CMFCVisualManagerVS2005::在EraseTabs區域](#onerasetabsarea)|(覆蓋[CMFCVisualManagerOffice2003:在 EraseTabs 區域](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea).)|
|[CMFCVisualManagerVS2005::在填充自動隱藏按鈕背景](#onfillautohidebuttonbackground)|(覆蓋[CMFCVisualManagerOffice2003::onfill 自動隱藏按鈕背景](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground).)|
|[CMFCVisualManagerVS2005::在填充突出顯示區域](#onfillhighlightedarea)|(覆蓋[CMFCVisualManagerOffice2003:onFill 突出顯示區域](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea).)|
|[CMFCVisualManagerVS2005::在填充迷你框架標題](#onfillminiframecaption)|(覆寫 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`。)|
|[CMFCVisualManagerVS2005::更新系統顏色](#onupdatesystemcolors)|(覆蓋[CMFCVisualManagerOffice2003:上更新系統顏色](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors).)|

## <a name="remarks"></a>備註

您可以使用 CMFCVisualManagerVS2005 類來更改應用程式的可視外觀,以類似於 Microsoft Visual Studio 2005。

此類的所有成員都是從此類的祖先[CMFCVisualManager 類](../../mfc/reference/cmfcvisualmanager-class.md)派生的虛擬函數。

## <a name="example"></a>範例

下面的範例展示如何使用視覺化管理員 VS 2005。 此代碼段是[桌面警報演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBase 視覺化管理員](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFC可視化經理辦公室XP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)

[CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)

## <a name="requirements"></a>需求

**標題:** afxvisualmanagervs2005.h

## <a name="cmfcvisualmanagervs2005getdockingtabsborderssize"></a><a name="getdockingtabsborderssize"></a>CMFCVisualManagerVS2005::獲取對接塔布邊界大小

```
virtual int GetDockingTabsBordersSize();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005getmditabsborderssize"></a><a name="getmditabsborderssize"></a>CMFCVisualManagerVS2005::獲取MDITabsBordersSize

```
virtual int GetMDITabsBordersSize();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManagerVS2005::獲取財產網格群彩

```
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```

### <a name="parameters"></a>參數

[在]*pProplist*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005gettabframecolors"></a><a name="gettabframecolors"></a>CMFC視覺管理器VS2005::取得TabFrame顏色

```
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,
    COLORREF& clrDark,
    COLORREF& clrBlack,
    COLORREF& clrHighlight,
    COLORREF& clrFace,
    COLORREF& clrDarkShadow,
    COLORREF& clrLight,
    CBrush*& pbrFace,
    CBrush*& pbrBlack);
```

### <a name="parameters"></a>參數

[在]*pTabwnd*<br/>
[在]*clrDark*<br/>
[在]*clrBlack*<br/>
[在]*clr 高光*<br/>
[在]*clrFace*<br/>
[在]*clrDark陰影*<br/>
[在]*clrLight*<br/>
[在]*pbrFace*<br/>
[在]*普布布萊克*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005hasoverlappedautohidebuttons"></a><a name="hasoverlappedautohidebuttons"></a>CMFCVisualManagerVS2005:: 已重疊自動隱藏按鈕

```
virtual BOOL HasOverlappedAutoHideButtons() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManagervs2005::在Draw自動隱藏按鈕邊框

```
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rectBunds*<br/>
[在]*整邊界大小*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawcaptionbutton"></a><a name="ondrawcaptionbutton"></a>CMFCVisualManagerVS2005::ONDrawCaption按鈕

```
virtual void OnDrawCaptionButton(
    CDC* pDC,
    CMFCCaptionButton* pButton,
    BOOL bActive,
    BOOL bHorz,
    BOOL bMaximized,
    BOOL bDisabled,
    int nImageID = -1);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*pButton*<br/>
[在]*b 活動*<br/>
[在]*布霍茲*<br/>
[在]*b 最大化*<br/>
[在]*b 殘疾*<br/>
[在]*nImageID*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManagervs2005::在DrawPaneCaption

```
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,
    CDockablePane* pBar,
    BOOL bActive,
    CRect rectCaption,
    CRect rectButtons);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*pBar*<br/>
[在]*b 活動*<br/>
[在]*rectCaption*<br/>
[在]*rectButtons*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManagerVS2005:OnDrawSeator

```
virtual void OnDrawSeparator(
    CDC* pDC,
    CBasePane* pBar,
    CRect rect,
    BOOL bIsHoriz);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*pBar*<br/>
[在]*rect*<br/>
[在]*比索裡茲*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManagerVS2005::在DrawTab

```
virtual void OnDrawTab(
    CDC* pDC,
    CRect rectTab,
    int iTab,
    BOOL bIsActive,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rectTab*<br/>
[在]*iTab*<br/>
[在]*bIsActive*<br/>
[在]*pTabwnd*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005ondrawtoolboxframe"></a><a name="ondrawtoolboxframe"></a>CMFCVisualManagerVS2005::在畫工具框框

```
virtual void OnDrawToolBoxFrame(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rect*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005onerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManagerVS2005::在EraseTabs區域

```
virtual void OnEraseTabsArea(
    CDC* pDC,
    CRect rect,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pTabwnd*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerVS2005::在填充自動隱藏按鈕背景

```
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,
    CRect rect,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a>CMFCVisualManagerVS2005::在填充突出顯示區域

```
virtual void OnFillHighlightedArea(
    CDC* pDC,
    CRect rect,
    CBrush* pBrush,
    CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*pBrush*<br/>
[在]*pButton*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005onfillminiframecaption"></a><a name="onfillminiframecaption"></a>CMFCVisualManagerVS2005::在填充迷你框架標題

```
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,
    CRect rectCaption,
    CPaneFrameWnd* pFrameWnd,
    BOOL bActive);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rectCaption*<br/>
[在]*pFramewnd*<br/>
[在]*b 活動*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcvisualmanagervs2005onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManagerVS2005::更新系統顏色

```
virtual void OnUpdateSystemColors();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[CMFCVisualManagerOfficeXP 類別](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)<br/>
[CMFC 視覺化管理員類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)<br/>
[CMFCVisualManagerOffice2003 類別](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)
