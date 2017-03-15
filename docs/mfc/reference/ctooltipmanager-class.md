---
title: "CTooltipManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTooltipManager
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager class
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3bbf191aacdd318f2afb0bd1a126c3eff290fad6
ms.lasthandoff: 02/24/2017

---
# <a name="ctooltipmanager-class"></a>CTooltipManager 類別
維護工具提示的執行階段資訊。 `CTooltipManager` 類別會在每個應用程式具現化一次。  
  
## <a name="syntax"></a>語法  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|建立指定的 Windows 控制項類型的工具提示控制項。|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|刪除工具提示控制項。|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|自訂指定的 Windows 控制項類型的工具提示控制項的視覺外觀。|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|設定工具提示控制項的文字和描述。|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>備註  
 使用[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和`CTooltipManager`在一起，以在您的應用程式中實作自訂的工具提示。 如需如何使用這些工具提示類別的範例，請參閱[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)主題。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtooltipmanager.h  
  
##  <a name="a-namecreatetooltipa--ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::CreateToolTip  
 建立工具提示控制項。  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pToolTip`  
 工具提示 」 指標的參考。 將函式傳回時指向新建立的工具提示。  
  
 [in] `pWndParent`  
 工具提示的父系。  
  
 [in] `nType`  
 工具提示的型別。  
  
### <a name="return-value"></a>傳回值  
 如果已成功建立工具提示為非零。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[CTooltipManager::DeleteToolTip](#deletetooltip)刪除工具提示控制項傳遞回`pToolTip`。  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)設定工具提示為基礎的視覺顯示參數，它會建立每個工具提示的類型，`nType`指定。 若要變更一個或多個工具提示類型的參數，呼叫[CTooltipManager::SetTooltipParams](#settooltipparams)。  
  
 下表列出有效的工具提示類型︰  
  
|工具提示的型別|控制項類別|範例型別|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|按鈕。|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|標題列。|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|不符合另一個類別目錄的任何控制項。|無。|  
|AFX_TOOLTIP_TYPE_DOCKBAR|可停駐窗格。|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|在文字方塊。|無。|  
|AFX_TOOLTIP_TYPE_MINIFRAME|自。|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|計劃。|無。|  
|AFX_TOOLTIP_TYPE_RIBBON|功能區列。|CMFCRibbonBar CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|索引標籤控制項。|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|工具列。|CMFCToolBar CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱中。|無。|  
  
##  <a name="a-namedeletetooltipa--ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip  
 刪除工具提示控制項。  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `pToolTip`  
 指向要終結的工具提示的參考。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，每個[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)所建立的[CTooltipManager::CreateToolTip](#createtooltip)。 父控制項應該呼叫這個方法，從其`OnDestroy`處理常式。 如此才能正確地移除架構中的工具提示。 這個方法會設定`pToolTip`至`NULL`它會傳回之前。  
  
##  <a name="a-namesettooltipparamsa--ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams  
 自訂指定的 Windows 控制項類型的工具提示控制項的外觀。  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTypes`  
 指定控制項型別。  
  
 [in] `pRTC`  
 執行階段類別的自訂工具提示。  
  
 [in] `pParams`  
 工具提示的參數。  
  
### <a name="remarks"></a>備註  
 這個方法會設定初始參數與執行階段類別， [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)建立工具提示時使用。 當控制項便會呼叫[CTooltipManager::CreateToolTip](#createtooltip)和工具提示中的傳遞類型，它是一種類型以`nTypes`，工具提示管理員會建立所指定的執行階段類別的執行個體的工具提示控制項`pRTC`，並將所指定的參數傳遞`pParams`新的工具提示。  
  
 當您呼叫這個方法時，所有現有的工具提示擁有者會收到 AFX_WM_UPDATETOOLTIPS 訊息而使用必須重建提示[CTooltipManager::CreateToolTip](#createtooltip)。  
  
 `nTypes`可以是任何有效的工具提示的組合類型[CTooltipManager::CreateToolTip](#createtooltip)用途，或它可以是 AFX_TOOLTIP_TYPE_ALL。 如果您傳遞 AFX_TOOLTIP_TYPE_ALL 時，會影響所有的工具提示類型。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetTooltipParams`方法`CTooltipManager`類別。 此程式碼片段是一部分[繪製的用戶端範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&11;](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="a-namesettooltiptexta--ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText  
 設定文字和工具提示描述。  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `pTI`  
 TOOLINFO 物件的指標。  
  
 [in、out] `pToolTip`  
 要設定文字與描述工具提示控制項的指標。  
  
 [in] `nType`  
 指定此工具提示所關聯的控制項類型。  
  
 [in] `strText`  
 要設定為工具提示文字的文字。  
  
 [in] `lpszDescr`  
 指標的工具提示描述。 可以是`NULL`。  
  
### <a name="remarks"></a>備註  
 值`nType`必須是相同的值`nType`參數[CTooltipManager::CreateToolTip](#createtooltip)當您建立工具提示。  
  
##  <a name="a-nameupdatetooltipsa--ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)

