---
title: "CPaneDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneDialog
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog::OnLButtonDblClk method
- CPaneDialog::OnLButtonDown method
- CPaneDialog::CreateObject method
- CPaneDialog::OnUpdateCmdUI method
- CPaneDialog constructor
- CPaneDialog::OnEraseBkgnd method
- CPaneDialog class
- CPaneDialog::OnWindowPosChanging method
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 85c7e338382758dd809fb770c5ab14860e362da8
ms.lasthandoff: 02/24/2017

---
# <a name="cpanedialog-class"></a>CPaneDialog 類別
`CPaneDialog`類別支援非強制回應，可停駐對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|預設建構函式。|  
|`CPaneDialog::~CPaneDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|建立可停駐對話方塊並將它附加`CPaneDialog`物件。|  
|`CPaneDialog::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CPaneDialog::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|處理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息。 (重新定義`CBasePane::HandleInitDialog`。)|  
|`CPaneDialog::OnEraseBkgnd`|處理[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)訊息。 (重新定義[CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|  
|`CPaneDialog::OnLButtonDblClk`|處理[需要知道 WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)訊息。 (重新定義[CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|  
|`CPaneDialog::OnLButtonDown`|處理[WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607)訊息。 (重新定義[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|  
|`CPaneDialog::OnUpdateCmdUI`|若要更新對話方塊視窗架構呼叫。 (覆寫[CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。)|  
|`CPaneDialog::OnWindowPosChanging`|處理[WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653)訊息。 (重新定義[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定的 OLE 控制項容器的對話方塊範本。|  
  
## <a name="remarks"></a>備註  
 建構`CPaneDialog`兩個步驟中的物件。 首先，建構您的程式碼中的物件。 其次，呼叫[CPaneDialog::Create](#create)。 您必須指定有效的資源範本名稱或範本識別碼，並將指標傳遞給父視窗。 否則，在建立程序會失敗。 對話方塊中，必須指定 WS_CHILD 和 WS_VISIBLE 樣式。 我們建議您同時指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 樣式。 如需詳細資訊，請參閱[視窗樣式](window-styles.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpanedialog.h  
  
##  <a name="a-namecreatea--cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Create  
 建立停駐對話方塊並將它附加`CPaneDialog`物件。  
  
```  
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID,  
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

 
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszWindowName`  
 停駐對話方塊的名稱。  
  
 [in] `pParentWnd`  
 父視窗的指標。  
  
 [in] `bHasGripper`  
 `TRUE`若要建立使用標題 （移駐夾）; 停駐對話方塊否則， `FALSE`。  
  
 [in] `lpszTemplateName`  
 資源的對話方塊範本的名稱。  
  
 [in] `nStyle`  
 視窗樣式。  
  
 [in] `nID`  
 控制項 id。  
  
 [in] `nIDTemplate`  
 在對話方塊範本資源識別碼。  
  
 [in] `dwTabbedStyle`  
 使用者控制項的另一個窗格拖放這個控制項窗格的標題時，所造成的索引標籤式視窗的樣式。 預設值是 `AFX_CBRS_REGULAR_TABS`。 如需詳細資訊，請參閱 < 備註 > 一節[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
 [in] `dwControlBarStyle`  
 其他的樣式屬性。 預設值是 `AFX_DEFAULT_DOCKING_PANE_STYLE`。 如需詳細資訊，請參閱 < 備註 > 一節[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法中的`CPaneDialog`類別。 這個範例是屬於[設定窗格大小範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_SetPaneSize #&2;](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize #&3;](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="a-namehandleinitdialoga--cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog  
 處理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息。  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `wParam`  
 接受預設鍵盤焦點的控制項的控制代碼。  
  
 [in] `lParam`  
 指定額外的初始化資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。 此外，`TRUE`將鍵盤焦點設定為指定的控制項`wParam`參數。`FALSE`可防止設定預設鍵盤焦點。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法初始化控制項和對話方塊的外觀。 架構會呼叫這個方法之前會顯示對話方塊。  
  
##  <a name="a-namesetoccdialoginfoa--cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo  
 指定的 OLE 控制項容器的對話方塊範本。  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `pOccDialogInfo`  
 對話方塊範本，用來建立對話方塊物件的指標。 此參數值接著會傳遞至[COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 這個方法支援[COccManager](../../mfc/reference/coccmanager-class.md)管理 OLE 控制項的網站和 ActiveX 控制項的類別。 _AFX_OCC_DIALOG_INFO 結構 afxocc.h 標頭檔中定義。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [視窗樣式](../../mfc/reference/window-styles.md)




