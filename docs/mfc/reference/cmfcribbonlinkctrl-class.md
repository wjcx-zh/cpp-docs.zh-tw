---
title: "CMFCRibbonLinkCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonLinkCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLinkCtrl class
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
caps.latest.revision: 22
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
ms.openlocfilehash: 87b6c595475a69eb26c8c2e83789ea6c4394e653
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl 類別
實作放置在功能區上的超連結。 當您按一下時，超連結會開啟網頁。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|建構並初始化 `CMFCRibbonLinkCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(覆寫 `CMFCRibbonButton::CopyFrom`。)|  
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(覆寫[CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)。)|  
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|傳回超連結的值。|  
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(覆寫[CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)。)|  
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(覆寫[CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)。)|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|  
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(覆寫[CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)。)|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)。)|  
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(覆寫 `CMFCRibbonButton::OnMouseMove`。)|  
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||  
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|開啟超連結中指定的網頁。|  
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|設定超連結的值。|  
  
## <a name="remarks"></a>備註  
 建立超連結之後，將它加入至面板藉由呼叫[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonLinkCtrl.h  
  
##  <a name="a-namecmfcribbonlinkctrla--cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl  
 建構並初始化[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)物件。  
  
```  
CMFCRibbonLinkCtrl(
    UINT nID,  
    LPCTSTR lpszText,  
    LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 指定命令執行時按下連結控制項時所執行的命令 ID。  
  
 [in] `lpszText`  
 指定要連結控制項上顯示的標籤。  
  
 [in] `lpszLink`  
 指定連結控制項相關聯的超連結。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用建構函式的`CMFCRibbonLinkCtrl`類別。 此程式碼片段是一部分[功能區小工具範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RibbonGadgets #&1;](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]  
  
##  <a name="a-namecopyfroma--cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonLinkCtrl::CopyFrom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcompactsizea--cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlinka--cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink  
 傳回超連結的值。  
  
```  
LPCTSTR GetLink() const;  
```  
  
### <a name="return-value"></a>傳回值  
 超連結的目前值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetregularsizea--cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegettooltiptexta--cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawmenuimagea--cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>參數  
 [in] `CDC*`  
 [in] `CRect`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisdrawtooltipimagea--cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameondrawa--cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a>CMFCRibbonLinkCtrl::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonmousemovea--cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a>CMFCRibbonLinkCtrl::OnMouseMove  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonseticona--cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnSetIcon();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameopenlinka--cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink  
 開啟超連結中指定的網頁。  
  
```  
BOOL OpenLink();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 開啟相關聯的 Web 網頁否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 開啟使用相關聯的超連結的網頁`CMFCRibbonLinkCtrl`物件。  
  
##  <a name="a-namesetlinka--cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a>CMFCRibbonLinkCtrl::SetLink  
 設定超連結的值。  
  
```  
void SetLink(LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLink`  
 指定超連結文字。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)

