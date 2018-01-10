---
title: "CMFCDropDownToolBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
dev_langs: C++
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: "37"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7a2f53fa75d8637445e155043d6a40787402accb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar 類別
當使用者按住最上層工具列按鈕時出現的工具列。  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>語法  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(覆寫 `CPane::AllowShowOnPaneMenu`。)|  
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(覆寫[CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap)。)|  
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(覆寫[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar)。)|  
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||  
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||  
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(覆寫 `CMFCToolBar::OnSendCommand`。)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(覆寫[CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/571a38ab-2a56-4968-9796-273516126f80)。)|  
  
### <a name="remarks"></a>備註  
 A`CMFCDropDownToolBar`物件結合工具列的視覺外觀與行為的快顯功能表。 當使用者按住下拉式工具列按鈕 (請參閱[CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md))、 下拉式清單出現工具列，而且使用者可以選取從下拉式清單工具列按鈕，請捲動，放開滑鼠按鈕。 使用者選取下拉式清單工具列中的按鈕之後，該按鈕會顯示為最上層工具列上的 [目前] 按鈕。  
  
 下拉式工具列無法自訂或停駐，而且它並沒有分割的狀態。  
  
 下圖顯示`CMFCDropDownToolBar`物件：  
  
 ![Cmfcdropdowntoolbar 範例](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")  
  
 您建立`CMFCDropDownToolBar`物件相同的方式建立一般工具列 (請參閱[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md))。  
  
 插入為父工具列的下拉式清單工具列：  
  
 1. 為父工具列資源的按鈕保留假的資源 ID。  
  
 2. 建立`CMFCDropDownToolBarButton`物件，其中包含下拉式工具列 (如需詳細資訊，請參閱[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton))。  
  
 3. 取代的 dummy 按鈕`CMFCDropDownToolBarButton`物件使用[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)。  
  
 如需有關工具列按鈕的詳細資訊，請參閱[逐步解說： 將工具列控制項](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 如需下拉式工具列的範例，請參閱範例專案 VisualStudioDemo。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法中的`CMFCDropDownToolBar`類別。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdropdowntoolbar.h  
  
##  <a name="allowshowonpanemenu"></a>CMFCDropDownToolBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="loadbitmap"></a>CMFCDropDownToolBar::LoadBitmap  
 從應用程式資源載入工具列影像。  
  
```  
virtual BOOL LoadBitmap(
    UINT uiResID,  
    UINT uiColdResID=0,  
    UINT uiMenuResID=0,  
    BOOL bLocked=FALSE,  
    UINT uiDisabledResID=0,  
    UINT uiMenuDisabledResID=0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiResID`  
 參考作用中工具列影像之點陣圖的資源 ID。  
  
 [輸入] `uiColdResID`  
 參考非作用中工具列影像之點陣圖的資源 ID。  
  
 [輸入] `uiMenuResID`  
 參考標準功能表影像之點陣圖的資源 ID。  
  
 [輸入] `bLocked`  
 `TRUE`若要鎖定工具列，否則`FALSE`。  
  
 [輸入] `uiDisabledResID`  
 參考已停用工具列影像之點陣圖的資源 ID。  
  
 [輸入] `uiMenuDisabledResID`  
 參考已停用功能表影像之點陣圖的資源 ID。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，則為非零，否則為零。  
  
### <a name="remarks"></a>備註  
 [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法會呼叫這個方法來載入與工具列相關聯的映像。 覆寫這個方法可執行影像資源的自訂載入。  
  
 呼叫 `LoadBitmapEx` 方法可在建立工具列之後載入其他影像。  
  
##  <a name="loadtoolbar"></a>CMFCDropDownToolBar::LoadToolBar  

  
```  
virtual BOOL LoadToolBar(
    UINT uiResID,  
    UINT uiColdResID = 0,  
    UINT uiMenuResID = 0,
    BOOL = FALSE,  
    UINT uiDisabledResID = 0,  
    UINT uiMenuDisabledResID = 0,  
    UINT uiHotResID = 0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiResID`  
 [輸入] `uiColdResID`  
 [輸入] `uiMenuResID`  
 [輸入] `BOOL`  
 [輸入] `uiDisabledResID`  
 [輸入] `uiMenuDisabledResID`  
 [輸入] `uiHotResID`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttonup"></a>CMFCDropDownToolBar::OnLButtonUp  

  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nFlags`  
 [輸入] `point`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onmousemove"></a>CMFCDropDownToolBar::OnMouseMove  

  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nFlags`  
 [輸入] `point`  
  
### <a name="remarks"></a>備註  
  
##  <a name="onsendcommand"></a>CMFCDropDownToolBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pButton`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatecmdui"></a>CMFCDropDownToolBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pTarget`  
 [輸入] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [CMFCDropDownToolbarButton 類別](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [逐步解說：將控制項放在工具列上](../../mfc/walkthrough-putting-controls-on-toolbars.md)



