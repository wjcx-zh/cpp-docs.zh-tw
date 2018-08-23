---
title: CMFCToolTipInfo 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a8ec3a7898f846af85614dec75c10c5a0393e24
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540180"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo 類別
儲存工具提示視覺外觀的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolTipInfo  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|一個布林值變數，指出工具提示是否有氣球外觀。|  
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|一個布林值變數，指出工具提示標籤是否以粗體字顯示。|  
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|一個布林值變數，指出工具提示是否包含描述。|  
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|一個布林值變數，指出工具提示是否包含圖示。|  
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|一個布林值變數，指出是否要在工具提示標籤與工具提示描述之間顯示分隔符號。|  
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|一個布林值變數，指出工具提示是否有圓角。|  
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|布林值變數，指出是否應由視覺管理員控制的工具提示外觀 (請參閱[CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md))。|  
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|工具提示框線的色彩。|  
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|工具提示背景的色彩。|  
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|工具提示中填入的漸層色彩。|  
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|工具提示的文字色彩。|  
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|工具提示中填入的漸層角度。|  
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|工具提示描述的最大可能寬度，以像素為單位。|  
  
## <a name="remarks"></a>備註  
 使用[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，以及[CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)應用程式中實作自訂的工具提示。 如需如何使用這些工具提示類別的範例，請參閱 < [CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)主題。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定 `CMFCToolTipInfo` 類別中各種成員變數的值。  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtooltipctrl.h  
  
##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip  
 指定所有的工具提示的顯示樣式。  
  
```  
BOOL m_bBalloonTooltip;  
```  
  
### <a name="remarks"></a>備註  
 TRUE 表示工具提示使用氣球樣式，FALSE 表示工具提示使用的矩形樣式。  
  
##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel  
 指定的工具提示文字的字型是否為粗體。  
  
```  
BOOL m_bBoldLabel;  
```  
  
### <a name="remarks"></a>備註  
 設定這個成員以 true 或 FALSE 以粗體顯示的字型，顯示工具提示文字與非粗體字型顯示工具提示標籤。  
  
##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription  
 指定每個工具提示是否顯示描述文字。  
  
```  
BOOL m_bDrawDescription;  
```  
  
### <a name="remarks"></a>備註  
 設定這個成員，以顯示描述或 FALSE 表示隱藏描述 true。 您可以在工具提示上指定的描述，藉由呼叫[CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)  
  
##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon  
 指定所有的工具提示是否顯示圖示。  
  
```  
BOOL m_bDrawIcon;  
```  
  
### <a name="remarks"></a>備註  
 將這個成員設定為在每個工具提示上顯示圖示，則為 TRUE 或 FALSE，以顯示不含圖示的工具提示。  
  
##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator  
 指定每個工具提示是否有其標籤和其描述之間的分隔符號。  
  
```  
BOOL m_bDrawSeparator;  
```  
  
### <a name="remarks"></a>備註  
 將這個成員設定要顯示工具提示標籤和描述之間的分隔符號，則為 TRUE 或 FALSE，以顯示工具提示，且沒有分隔符號。  
  
##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners  
 指定所有的工具提示是否有圓角。  
  
```  
BOOL m_bRoundedCorners;  
```  
  
### <a name="remarks"></a>備註  
 設定這個成員，以顯示圓角邊角中，使用工具提示，或 FALSE true 以顯示工具提示上的矩形邊角。  
  
##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder  
 指定所有的工具提示框線的色彩。  
  
```  
COLORREF m_clrBorder;  
```  
  
##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill  
 指定的工具提示背景的色彩。  
  
```  
COLORREF m_clrFill;  
```  
  
### <a name="remarks"></a>備註  
 如果[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)為-1，工具提示背景色彩是`m_clrFill`。 否則`m_clrFill`指定的漸層開始色彩和`m_clrFillGradient`指定漸層結束色彩。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)決定漸層的方向。  
  
##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient  
 指定工具提示的漸層背景的結束色彩。  
  
```  
COLORREF m_clrFillGradient;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_clrFillGradient`為-1，沒有任何漸層。 否則，所指定的漸層停駐的初始色彩[CMFCToolTipInfo::m_clrFill](#m_clrfill)和漸層停駐完成色彩由指定`m_clrFillGradient`。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)決定漸層的方向。  
  
##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText  
 指定所有工具提示的文字的色彩。  
  
```  
COLORREF m_clrText;  
```  
  
##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle  
 指定的工具提示的背景繪製漸層的角度。  
  
```  
int m_nGradientAngle;  
```  
  
### <a name="remarks"></a>備註  
 `m_nGradientAngle` 指定的角度以度數為單位，工具提示背景的漸層水平位移。 如果`m_nGradientAngle`為 0，漸層繪製從左到右。 如果`m_nGradientAngle`是介於 1 到 360 度，漸層旋轉順時針旋轉的度數為單位的數目。 如果`m_nGradientAngle`為-1，也就是預設值，漸層繪製從上到下。 這是設定相同`m_nGradientAngle`為 90。  
  
 [CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill`指定的色彩漸層開頭並[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient`指定漸層結束色彩。 如果`m_clrFillGradient`為-1，沒有任何漸層。  
  
##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth  
 指定的描述，它顯示在每個工具提示的最大寬度。 如果描述寬度超過指定的值，表示文字換行。  
  
```  
int m_nMaxDescrWidth;  
```  
  
##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme  
 指定是否在應用程式的視覺管理員控制的所有工具提示外觀。  
  
```  
BOOL m_bVislManagerTheme;  
```  
  
### <a name="remarks"></a>備註  
 如果`m_bVislManagerTheme`為 TRUE 時，每個工具提示會要求新[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)從應用程式，才能出現在畫面上，並使用該物件中的值，來判斷其外觀的視覺管理員。 其他成員您[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)都會被忽略。  
  
##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator =  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```  
  
### <a name="parameters"></a>參數  
 [in]*src*  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)
