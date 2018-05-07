---
title: CPaneDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36f620f0a29e7d1715e7cb5bfb83c0685f97f643
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cpanedialog-class"></a>CPaneDialog 類別
`CPaneDialog`類別支援非強制回應，可停駐對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|預設建構函式。|  
|`CPaneDialog::~CPaneDialog`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|建立可停駐對話方塊，並將它附加至`CPaneDialog`物件。|  
|`CPaneDialog::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CPaneDialog::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|處理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息。 (重新定義`CBasePane::HandleInitDialog`。)|  
|`CPaneDialog::OnEraseBkgnd`|處理[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)訊息。 (重新定義[CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|  
|`CPaneDialog::OnLButtonDblClk`|處理[WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606)訊息。 (重新定義[CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|  
|`CPaneDialog::OnLButtonDown`|處理[WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607)訊息。 (重新定義[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|  
|`CPaneDialog::OnUpdateCmdUI`|由架構呼叫以更新對話方塊視窗。 (覆寫[cdockablepane:: Onupdatecmdui](http://msdn.microsoft.com/en-us/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。)|  
|`CPaneDialog::OnWindowPosChanging`|處理[WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653)訊息。 (重新定義[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定的範本，是一個 OLE 控制項容器 對話方塊。|  
  
## <a name="remarks"></a>備註  
 建構`CPaneDialog`兩個步驟中的物件。 首先，建構您的程式碼中的物件。 第二，呼叫[CPaneDialog::Create](#create)。 您必須指定有效的資源範本名稱或範本識別碼，並將指標傳遞給父視窗。 否則，在建立程序會失敗。 對話方塊中，必須指定 WS_CHILD 和 WS_VISIBLE 樣式。 我們建議您也指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 樣式。 如需詳細資訊，請參閱[視窗樣式](styles-used-by-mfc.md#window-styles)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxpanedialog.h  
  
##  <a name="create"></a>  CPaneDialog::Create  
 建立停駐的對話方塊，並將它附加至`CPaneDialog`物件。  
  
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
 [輸入] `lpszWindowName`  
 [停駐] 對話方塊中的名稱。  
  
 [輸入] `pParentWnd`  
 指向父視窗。  
  
 [輸入] `bHasGripper`  
 `TRUE` 若要建立停駐對話方塊具有標題 （移駐夾）;否則， `FALSE`。  
  
 [輸入] `lpszTemplateName`  
 資源的對話方塊範本的名稱。  
  
 [輸入] `nStyle`  
 視窗樣式。  
  
 [輸入] `nID`  
 控制項 id。  
  
 [輸入] `nIDTemplate`  
 對話方塊範本資源識別碼。  
  
 [輸入] `dwTabbedStyle`  
 使用者控制項的另一個窗格拖放此控制項窗格的標題時，所造成的索引標籤式視窗的樣式。 預設值是 `AFX_CBRS_REGULAR_TABS`。 如需詳細資訊，請參閱 < 備註 > 一節[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
 [輸入] `dwControlBarStyle`  
 其他樣式屬性。 預設值是 `AFX_DEFAULT_DOCKING_PANE_STYLE`。 如需詳細資訊，請參閱 < 備註 > 一節[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果此方法成功。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法中的`CPaneDialog`類別。 這個範例是屬於[設定窗格大小範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog  
 處理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息。  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `wParam`  
 要接收預設鍵盤焦點的控制項的控制代碼。  
  
 [輸入] `lParam`  
 指定額外的初始化資料。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。 此外，`TRUE`將鍵盤焦點設定為所指定的控制項`wParam`參數;`FALSE`防止設定預設鍵盤焦點。  
  
### <a name="remarks"></a>備註  
 架構會使用這個方法初始化控制項和對話方塊的外觀。 架構會呼叫這個方法之前會顯示對話方塊。  
  
##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo  
 指定的範本，是一個 OLE 控制項容器 對話方塊。  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pOccDialogInfo`  
 對話方塊範本用來建立對話方塊物件的指標。 此參數的值之後會傳遞至[COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。  
  
### <a name="return-value"></a>傳回值  
 一定是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 這個方法支援[COccManager](../../mfc/reference/coccmanager-class.md)管理 OLE 控制項網站以及 ActiveX 控制項的類別。 _AFX_OCC_DIALOG_INFO 結構 afxocc.h 標頭檔中定義。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)   
 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)



