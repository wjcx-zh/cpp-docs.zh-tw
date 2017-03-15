---
title: "CMFCToolTipCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolTipCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipCtrl class
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c4acd1cff8b3ce6fb4815ad78ad91225b385d547
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 類別
擴充工具提示實作根據[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)。 根據 `CMFCToolTipCtrl` 類別的工具提示可以顯示圖示、標籤和描述。 您可以使用漸層填滿、自訂文字和框線色彩、粗體文字、圓角或氣球樣式，自訂其視覺外觀。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|傳回工具提示中的圖示大小。|  
|[CMFCToolTipCtrl::GetParams](#getparams)|傳回工具提示的顯示設定。|  
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|繪製工具提示的框線。|  
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||  
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|在工具提示中顯示圖示。|  
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|繪製工具提示的標籤，或計算標籤的大小。|  
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|工具提示中的標籤和描述之間繪製分隔符號。|  
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|填滿工具提示背景。|  
|[CMFCToolTipCtrl::SetDescription](#setdescription)|設定要由工具提示顯示的描述。|  
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||  
|[CMFCToolTipCtrl::SetLocation](#setlocation)||  
|[CMFCToolTipCtrl::SetParams](#setparams)|使用 `CMFCToolTipInfo` 物件指定工具提示的視覺外觀。|  
  
## <a name="remarks"></a>備註  
 使用`CMFCToolTipCtrl`， `CMFCToolTipInfo`，和[CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)在一起，以在您的應用程式中實作自訂的工具提示的物件。  
  
 例如，若要使用氣球樣式工具提示，請依照下列步驟：  
  
 1. 使用[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)方法以初始化應用程式中的工具提示管理員。  
  
 2. 建立 `CMFCToolTipInfo` 結構來指定您想要的視覺樣式：  
  
```  
CMFCToolTipInfo params;  
    params.m_bBoldLabel = FALSE;  
    params.m_bDrawDescription = FALSE;  
    params.m_bDrawIcon = FALSE;  
    params.m_bRoundedCorners = TRUE;  
    params.m_bDrawSeparator = FALSE;  
    if (m_bCustomColors)  
 {  
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

 }  
```  
3. 使用[CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法來設定應用程式中所有的工具提示的視覺化樣式，使用定義的樣式`CMFCToolTipInfo`物件︰  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```  
您也可以從 `CMFCToolTipCtrl` 衍生新的類別，以控制工具提示的行為和呈現。 若要指定新的工具提示控制項類別，請使用 `CTooltipManager::SetTooltipParams` 方法：  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
若要還原預設工具提示控制類別，並將工具提示外觀重設為預設狀態，請在 `SetTooltipParams` 的執行階段類別和工具提示資訊參數中指定 NULL：  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL,
    NULL);
```  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCToolTipCtrl` 物件、設定工具提示顯示的描述，以及設定工具提示控制項的寬度。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&41;](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtooltipctrl.h  
  
##  <a name="a-namecmfctooltipctrla--cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParams`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegeticonsizea--cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::GetIconSize  
 傳回工具提示中的圖示大小。  
  
```  
virtual CSize GetIconSize();
```  
  
### <a name="return-value"></a>傳回值  
 圖示，單位為像素的大小。  
  
##  <a name="a-namegetparamsa--cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams  
 傳回工具提示的顯示設定。  
  
```  
const CMFCToolTipInfo& GetParams() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的工具提示顯示設定，儲存在[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件。  
  
##  <a name="a-nameondrawbordera--cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl::OnDrawBorder  
 繪製工具提示的框線。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect,  
    COLORREF clrLine);
```  
  
### <a name="parameters"></a>參數  
 `[in] pDC`  
 裝置內容的指標。  
  
 `[in] rect`  
 工具提示，這個周框。  
  
 `[in] clrLine`  
 框線色彩。  
  
### <a name="remarks"></a>備註  
 若要自訂的工具提示框線外觀的衍生類別中，這個方法會覆寫。  
  
##  <a name="a-nameondrawdescriptiona--cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl::OnDrawDescription  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize OnDrawDescription(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `rect`  
 [in] `bCalcOnly`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawicona--cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipCtrl::OnDrawIcon  
 在工具提示中顯示圖示。  
  
```  
virtual BOOL OnDrawIcon(
    CDC* pDC,  
    CRect rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectImage`  
 圖示的座標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已經繪製圖示。 否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 若要顯示自訂圖示的衍生類別中，這個方法會覆寫。 您也必須覆寫[CMFCToolTipCtrl::GetIconSize](#geticonsize)啟用工具提示來正確計算文字與描述的配置。  
  
##  <a name="a-nameondrawlabela--cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl::OnDrawLabel  
 繪製工具提示的標籤，或計算標籤的大小。  
  
```  
virtual CSize OnDrawLabel(
    CDC* pDC,  
    CRect rect,  
    BOOL bCalcOnly);
```  
  
### <a name="parameters"></a>參數  
 `[in] pDC`  
 裝置內容的指標。  
  
 `[in] rect`  
 [標籤] 區域的周框矩形。  
  
 `[in] bCalcOnly`  
 如果`TRUE`，不會繪製標籤。  
  
### <a name="return-value"></a>傳回值  
 像素為單位指定標籤的大小。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法在衍生類別中的，如果您想要自訂的工具提示標籤外觀。  
  
##  <a name="a-nameondrawseparatora--cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipCtrl::OnDrawSeparator  
 工具提示中的標籤和描述之間繪製分隔符號。  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    int x1,  
    int x2,  
    int y);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `x1`  
 水平座標分隔符號的左邊。  
  
 [in] `x2`  
 水平座標分隔符號的右邊。  
  
 [in] `Y`  
 分隔線的垂直座標。  
  
### <a name="remarks"></a>備註  
 預設實作會繪製一條線從點 (x1，y) 到點 (x2，y)。  
  
 覆寫此方法來自訂外觀分隔線的衍生類別中。  
  
##  <a name="a-nameonfillbackgrounda--cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipCtrl::OnFillBackground  
 填滿工具提示背景。  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect,  
    COLORREF& clrText,  
    COLORREF& clrLine);
```  
  
### <a name="parameters"></a>參數  
 `[in] pDC`  
 裝置內容的指標。  
  
 `[in] rect`  
 指定要填滿區域的周框矩形。  
  
 `[in] clrText`  
 工具提示的前景色彩。  
  
 `[in] clrLine`  
 色彩的框線和分隔符號之間的線條標籤和描述。  
  
### <a name="remarks"></a>備註  
 預設實作會填入所指定的矩形`rect`使用色彩或最新的呼叫所指定模式[CMFCToolTipCtrl::SetParams](#setparams)。  
  
 如果您想要自訂 工具提示的外觀，請覆寫這個方法在衍生類別中。  
  
##  <a name="a-namesetdescriptiona--cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl::SetDescription  
 設定要由工具提示顯示的描述。  
  
```  
virtual void SetDescription(const CString strDesrciption);
```  
  
### <a name="parameters"></a>參數  
 `[in] strDesrciption`  
 描述文字。  
  
### <a name="remarks"></a>備註  
 描述文字會顯示在分隔符號下方的工具提示。  
  
##  <a name="a-namesetfixedwidtha--cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::SetFixedWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetFixedWidth(
    int nWidthRegular,  
    int nWidthLargeImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nWidthRegular`  
 [in] `nWidthLargeImage`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesethotribbonbuttona--cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::SetHotRibbonButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```  
  
### <a name="parameters"></a>參數  
 [in] `pRibbonButton`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetlocationa--cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::SetLocation  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetLocation(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 [in] `pt`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetparamsa--cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams  
 使用指定的工具提示視覺外觀[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件。  
  
```  
void SetParams(CMFCToolTipInfo* pParams);
```  
  
### <a name="parameters"></a>參數  
 `[in] pParams`  
 指標[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件，其中包含顯示參數。  
  
### <a name="remarks"></a>備註  
 顯示工具提示，它會使用色彩來繪製視覺樣式，每當`pParams`指定。 值`pParams`會儲存在受保護成員`m_Params`，其可存取衍生類別中覆寫[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)， [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)， [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)， [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)，或[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)維護指定的外觀。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)   
 [Cwinappex 衍生類別](../../mfc/reference/cwinappex-class.md)

