---
title: "CMFCLinkCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
dev_langs: C++
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc83e5abf09102af8f27b1ee73fc78ed162b9335
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl 類別
`CMFCLinkCtrl`類別顯示按鈕為超連結，並在按下按鈕時叫用連結的目標。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCLinkCtrl : public CMFCButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCLinkCtrl::SetURL](#seturl)|顯示指定的 URL 做為按鈕文字。|  
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|設定隱含的通訊協定 (例如，"http:") 的 url。|  
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|調整大小，以包含按鈕文字或點陣圖按鈕。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|繪製焦點矩形的按鈕前，由架構呼叫。|  
  
## <a name="remarks"></a>備註  
 當您按一下按鈕，衍生自`CMFCLinkCtrl`類別，此架構將按鈕的 URL 做為參數來`ShellExecute`方法。 然後在`ShellExecute`方法開啟的 URL 目標。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定的大小`CMFCLinkCtrl`物件，以及如何設定 url 和中的工具提示`CMFCLinkCtrl`物件。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxlinkctrl.h  
  
##  <a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect  
 繪製焦點矩形的按鈕前，由架構呼叫。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rectClient`  
 範圍連結控制項的矩形。  
  
### <a name="remarks"></a>備註  
 當您想要使用自己的程式碼繪製按鈕的焦點矩形，請覆寫這個方法。  
  
##  <a name="seturl"></a>CMFCLinkCtrl::SetURL  
 顯示指定的 URL 做為按鈕文字。  
  
```  
void SetURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszURL`  
 要顯示的按鈕文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix  
 設定隱含的通訊協定 (例如，"http:") 的 url。  
  
```  
void SetURLPrefix(LPCTSTR lpszPrefix);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszPrefix`  
 URL 通訊協定前置詞。  
  
### <a name="remarks"></a>備註  
 若要設定的 URL 前置詞使用此方法。 前置詞不會顯示在按鈕的圖示，但您可以使用它來協助瀏覽至的 URL 目標。  
  
##  <a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent  
 調整大小，以包含按鈕文字或點陣圖按鈕。  
  
```  
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,  
    BOOL bHCenter=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bVCenter`  
 `TRUE`若要按鈕文字和點陣圖頂端和底部的連結控制; 之間的垂直置中否則， `FALSE`。 預設值是 `FALSE`。  
  
 [輸入] `bHCenter`  
 `TRUE`若要按鈕文字和點陣圖的左邊和右邊的連結控制; 之間的水平置中否則， `FALSE`。 預設值是 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含連結控制項的新大小。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CLinkCtrl 類別](../../mfc/reference/clinkctrl-class.md)   
 [CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
