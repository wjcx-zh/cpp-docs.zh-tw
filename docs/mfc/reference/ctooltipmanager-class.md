---
title: CTooltipManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78b191766e33d291317ef50a4d5373dc26428577
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ctooltipmanager-class"></a>CTooltipManager 類別
維護工具提示的執行階段資訊。 `CTooltipManager` 類別會在每個應用程式具現化一次。  
  
## <a name="syntax"></a>語法  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|建立指定的 Windows 控制項類型的工具提示控制項。|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|刪除工具提示控制項。|  
|[Settooltipparams](#settooltipparams)|自訂指定的 Windows 控制項類型的工具提示控制項的視覺外觀。|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|設定工具提示控制項的文字和描述。|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>備註  
 使用[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和`CTooltipManager`在一起，以在您的應用程式中實作自訂的工具提示。 如需如何使用這些工具提示類別的範例，請參閱[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)主題。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip  
 建立的工具提示控制項。  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `pToolTip`  
 工具提示 」 指標的參考。 它是設定為函式傳回時指向新建立的工具提示。  
  
 [輸入] `pWndParent`  
 工具提示的父系。  
  
 [輸入] `nType`  
 工具提示的類型。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立工具提示。  
  
### <a name="remarks"></a>備註  
 您必須呼叫[CTooltipManager::DeleteToolTip](#deletetooltip)刪除在中傳回的工具提示控制項`pToolTip`。  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)設定工具提示為基礎的視覺顯示參數，它會建立每個工具提示的類型，`nType`指定。 若要變更一個或多個工具提示類型的參數，呼叫[Settooltipparams](#settooltipparams)。  
  
 下表列出有效的工具提示類型：  
  
|工具提示的型別|控制項類別|類型的範例|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|按鈕。|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|標題列。|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|任何不符合另一個類別目錄的控制項。|無。|  
|AFX_TOOLTIP_TYPE_DOCKBAR|可停駐窗格。|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|文字方塊。|無。|  
|AFX_TOOLTIP_TYPE_MINIFRAME|迷你。|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|規劃。|無。|  
|AFX_TOOLTIP_TYPE_RIBBON|功能區列。|CMFCRibbonBar CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|索引標籤控制項。|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|工具列。|CMFCToolBar CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱中。|無。|  
  
##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip  
 刪除工具提示控制項。  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `pToolTip`  
 為工具提示，也將被銷毀指標的參考。  
  
### <a name="remarks"></a>備註  
 每個呼叫這個方法[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)中建立[CTooltipManager::CreateToolTip](#createtooltip)。 父控制項應該呼叫這個方法，從其`OnDestroy`處理常式。 如此才能正確地移除架構中的工具提示。 這個方法會設定`pToolTip`至`NULL`它會傳回之前。  
  
##  <a name="settooltipparams"></a>  Settooltipparams  
 自訂指定的 Windows 控制項類型的工具提示控制項的外觀。  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nTypes`  
 指定控制項類型。  
  
 [輸入] `pRTC`  
 執行階段類別的自訂工具提示。  
  
 [輸入] `pParams`  
 工具提示的參數。  
  
### <a name="remarks"></a>備註  
 這個方法會設定初始參數與執行階段類別， [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)時它會建立工具提示使用。 控制當呼叫[CTooltipManager::CreateToolTip](#createtooltip)和工具提示中的傳遞類型，它是其中一個型別所指示`nTypes`，工具提示管理員會建立指定的執行階段類別的執行個體的工具提示控制項由`pRTC`，並將所指定的參數傳遞`pParams`至新的工具提示。  
  
 當您呼叫這個方法時，所有現有的工具提示擁有者會收到 AFX_WM_UPDATETOOLTIPS 訊息而他們必須使用，以重新建立其工具提示[CTooltipManager::CreateToolTip](#createtooltip)。  
  
 `nTypes` 可以是任何有效的工具提示的組合類型[CTooltipManager::CreateToolTip](#createtooltip)用途，或它可以是 AFX_TOOLTIP_TYPE_ALL。 如果您要傳入 AFX_TOOLTIP_TYPE_ALL，會影響所有工具提示的類型。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetTooltipParams`方法`CTooltipManager`類別。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
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
 [輸入] `pTI`  
 TOOLINFO 物件的指標。  
  
 [in、out] `pToolTip`  
 要設定的文字和描述工具提示控制項的指標。  
  
 [輸入] `nType`  
 指定與此工具提示相關聯的控制項類型。  
  
 [輸入] `strText`  
 要設定為工具提示文字的文字。  
  
 [輸入] `lpszDescr`  
 指標的工具提示描述。 可以是`NULL`。  
  
### <a name="remarks"></a>備註  
 值`nType`必須是相同的值`nType`參數[CTooltipManager::CreateToolTip](#createtooltip)當您建立工具提示。  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
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
