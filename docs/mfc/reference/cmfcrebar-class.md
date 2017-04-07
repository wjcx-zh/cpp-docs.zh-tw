---
title: "CMFCReBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs:
- C++
helpviewer_keywords:
- CMFCReBar class
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
caps.latest.revision: 27
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
ms.openlocfilehash: 5ec432cb8cf70d31c04c718fd7e802ee9c099763
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcrebar-class"></a>CMFCReBar 類別
A`CMFCReBar`物件會提供配置、 持續性和 rebar 控制項的狀態資訊的控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|將 rebar 群組列。|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(覆寫[CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)。)|  
|[CMFCReBar::CanFloat](#canfloat)|(覆寫[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|  
|[CMFCReBar::Create](#create)|建立 rebar 控制項並將它附加`CMFCReBar`物件。|  
|[CMFCReBar::EnableDocking](#enabledocking)|(覆寫[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|可直接存取基礎[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)通用控制項。|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(覆寫[CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)。)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(覆寫[CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)。)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(覆寫[CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/e139f06a-9793-4ee2-bc3d-517389368c77)。)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(覆寫[CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)。)|  
  
## <a name="remarks"></a>備註  
 A`CMFCReBar`物件可以包含各種子視窗。 這包括編輯方塊、 工具列和清單方塊。 您可以以程式設計方式調整大小 rebar 或使用者可以手動拖曳調整大小 rebar 的移駐夾列。 您也可以設定 rebar 物件的背景，您所選擇的點陣圖。  
  
 Rebar 物件運作起來就像一個工具列物件。 Rebar 控制項可以包含一或多個群組列，而且每個群組列可以包含移駐夾列、 點陣圖、 文字標籤和子視窗。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCReBar`類別。 此範例示範如何建立 rebar 控制項和群組列加入。 寬功能為內部的工具列。 此程式碼片段是一部分[Rebar 測試範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_RebarTest #&1;](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest #&2;](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRebar.h  
  
##  <a name="addbar"></a>CMFCReBar::AddBar  
 將 rebar 群組列。  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pBar`  
 要插入至 rebar 是子視窗的指標。 參考的物件必須具有**WS_CHILD**視窗樣式。  
  
 [in] `pszText`  
 指定要顯示 rebar 上的文字。 文字不是子視窗的一部分。 相反地，它會顯示在 rebar 本身。  
  
 [in][out]`pbmp`  
 指定要顯示 rebar 背景點陣圖。  
  
 [in] `dwStyle`  
 包含要套用至群組列的樣式。 如頻外樣式的完整清單，請參閱描述`fStyle`中[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) Windows SDK 文件中的結構。  
  
 [in] `clrFore`  
 代表 rebar 的前景色彩。  
  
 [in] `clrBack`  
 代表 rebar 的背景色彩。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果群組列已成功新增至 rebar;否則， `FALSE`。  
  
##  <a name="create"></a>CMFCReBar::Create  
 建立 rebar 控制項並將它附加[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)物件。  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pParentWnd`  
 Rebar 控制項的父視窗的指標。  
  
 [in] `dwCtrlStyle`  
 指定 rebar 控制項的樣式。 預設樣式的值是**RBS_BANDBORDERS**，它會顯示縮小範圍，來分隔相鄰群組列的 rebar 控制項的程式碼行。 如需有效的樣式，請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 文件中。  
  
 [in] `dwStyle`  
 Rebar 控制項的視窗樣式。 如需有效的樣式，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `nID`  
 Rebar 的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 建立 rebar否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl  
 可直接存取`CReBarCtrl`為基礎的通用控制項`CMFCReBar`物件。  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考基礎`CReBarCtrl`物件。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以充分利用 Windows rebar 通用控制項功能來自訂您 rebar 時。  
  
##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>參數  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="canfloat"></a>CMFCReBar::CanFloat  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="enabledocking"></a>CMFCReBar::EnableDocking  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwDockStyle`  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT GetReBarBandInfoSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>參數  
 [in] `CPoint`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>參數  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwAlignment`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl 類別](../../mfc/reference/crebarctrl-class.md)   
 [CPane 類別](../../mfc/reference/cpane-class.md)

