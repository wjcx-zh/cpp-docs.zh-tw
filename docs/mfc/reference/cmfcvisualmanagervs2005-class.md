---
title: "CMFCVisualManagerVS2005 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9678ef4472f2bcb44a04d3484988033542aae243
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 類別
`CMFCVisualManagerVS2005`讓應用程式的 Microsoft Visual Studio 2005 的外觀。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](#getdockingtabsborderssize)|當它繪製為停駐和索引標籤式窗格時，架構會呼叫這個方法。 (覆寫[CMFCVisualManager::GetDockingTabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize)。)|  
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](#getmditabsborderssize)|架構會呼叫這個方法，它繪製視窗前，判斷 /mditabs 視窗的框線大小。 (覆寫[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)。)|  
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|(覆寫[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor)。)|  
|[CMFCVisualManagerVS2005::GetTabFrameColors](#gettabframecolors)|(覆寫[CMFCVisualManagerOffice2003::GetTabFrameColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors)。)|  
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](#hasoverlappedautohidebuttons)|傳回在目前的視覺管理員是否重疊的自動隱藏按鈕。 (覆寫[CMFCVisualManager::HasOverlappedAutoHideButtons](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons)。)|  
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|(覆寫[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder)。)|  
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](#ondrawcaptionbutton)|(覆寫 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`。)|  
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](#ondrawpanecaption)|(覆寫[CMFCVisualManagerOffice2003::OnDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption)。)|  
|[CMFCVisualManagerVS2005::OnDrawSeparator](#ondrawseparator)|(覆寫[CMFCVisualManagerOffice2003::OnDrawSeparator](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator)。)|  
|[CMFCVisualManagerVS2005::OnDrawTab](#ondrawtab)|(覆寫[CMFCVisualManagerOffice2003::OnDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab)。)|  
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](#ondrawtoolboxframe)|(覆寫[CMFCVisualManager::OnDrawToolBoxFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe)。)|  
|[CMFCVisualManagerVS2005::OnEraseTabsArea](#onerasetabsarea)|(覆寫[CMFCVisualManagerOffice2003::OnEraseTabsArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea)。)|  
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|(覆寫[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground)。)|  
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](#onfillhighlightedarea)|(覆寫[CMFCVisualManagerOffice2003::OnFillHighlightedArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea)。)|  
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](#onfillminiframecaption)|(覆寫 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`。)|  
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](#onupdatesystemcolors)|(覆寫[CMFCVisualManagerOffice2003::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors)。)|  
  
## <a name="remarks"></a>備註  
 變更您的應用程式，類似於的視覺外觀的情況下，您在使用 CMFCVisualManagerVS2005 類別[!INCLUDE[vsprvsext](../../mfc/reference/includes/vsprvsext_md.md)]。  
  
 這個類別的成員都衍生自這個類別的祖系的虛擬函式[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用視覺管理員 VS 2005。 此程式碼片段是部分[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
 [CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxvisualmanagervs2005.h  
  
##  <a name="getdockingtabsborderssize"></a>CMFCVisualManagerVS2005::GetDockingTabsBordersSize  

  
```  
virtual int GetDockingTabsBordersSize();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getmditabsborderssize"></a>CMFCVisualManagerVS2005::GetMDITabsBordersSize  

  
```  
virtual int GetMDITabsBordersSize();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="getpropertygridgroupcolor"></a>CMFCVisualManagerVS2005::GetPropertyGridGroupColor  

  
```  
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pPropList`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettabframecolors"></a>CMFCVisualManagerVS2005::GetTabFrameColors  

  
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
 [輸入] `pTabWnd`  
 [輸入] `clrDark`  
 [輸入] `clrBlack`  
 [輸入] `clrHighlight`  
 [輸入] `clrFace`  
 [輸入] `clrDarkShadow`  
 [輸入] `clrLight`  
 [輸入] `pbrFace`  
 [輸入] `pbrBlack`  
  
### <a name="remarks"></a>備註  
  
##  <a name="hasoverlappedautohidebuttons"></a>CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons  

  
```  
virtual BOOL HasOverlappedAutoHideButtons() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawautohidebuttonborder"></a>CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder  

  
```  
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rectBounds`  
 [輸入] `rectBorderSize`  
 [輸入] `pButton`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawcaptionbutton"></a>CMFCVisualManagerVS2005::OnDrawCaptionButton  

  
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
 [輸入] `pDC`  
 [輸入] `pButton`  
 [輸入] `bActive`  
 [輸入] `bHorz`  
 [輸入] `bMaximized`  
 [輸入] `bDisabled`  
 [輸入] `nImageID`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawpanecaption"></a>CMFCVisualManagerVS2005::OnDrawPaneCaption  

  
```  
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,  
    CDockablePane* pBar,  
    BOOL bActive,  
    CRect rectCaption,  
    CRect rectButtons);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `pBar`  
 [輸入] `bActive`  
 [輸入] `rectCaption`  
 [輸入] `rectButtons`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawseparator"></a>CMFCVisualManagerVS2005::OnDrawSeparator  

  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rect,  
    BOOL bIsHoriz);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `pBar`  
 [輸入] `rect`  
 [輸入] `bIsHoriz`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawtab"></a>CMFCVisualManagerVS2005::OnDrawTab  

  
```  
virtual void OnDrawTab(
    CDC* pDC,  
    CRect rectTab,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rectTab`  
 [輸入] `iTab`  
 [輸入] `bIsActive`  
 [輸入] `pTabWnd`  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawtoolboxframe"></a>CMFCVisualManagerVS2005::OnDrawToolBoxFrame  

  
```  
virtual void OnDrawToolBoxFrame(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rect`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onerasetabsarea"></a>CMFCVisualManagerVS2005::OnEraseTabsArea  

  
```  
virtual void OnEraseTabsArea(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rect`  
 [輸入] `pTabWnd`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground  

  
```  
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,  
    CRect rect,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rect`  
 [輸入] `pButton`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfillhighlightedarea"></a>CMFCVisualManagerVS2005::OnFillHighlightedArea  

  
```  
virtual void OnFillHighlightedArea(
    CDC* pDC,  
    CRect rect,  
    CBrush* pBrush,  
    CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rect`  
 [輸入] `pBrush`  
 [輸入] `pButton`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onfillminiframecaption"></a>CMFCVisualManagerVS2005::OnFillMiniFrameCaption  

  
```  
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,  
    CRect rectCaption,  
    CPaneFrameWnd* pFrameWnd,  
    BOOL bActive);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 [輸入] `rectCaption`  
 [輸入] `pFrameWnd`  
 [輸入] `bActive`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatesystemcolors"></a>CMFCVisualManagerVS2005::OnUpdateSystemColors  

  
```  
virtual void OnUpdateSystemColors();
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP 類別](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows 類別](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManagerOffice2003 類別](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)