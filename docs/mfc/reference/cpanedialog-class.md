---
title: CPaneDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: c78b8f2cd19e87fa559c3f9bbd24d07543d887c5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769741"
---
# <a name="cpanedialog-class"></a>CPaneDialog 類別

`CPaneDialog`類別支援非強制回應，可停駐的對話方塊。

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
|[CPaneDialog::Create](#create)|建立可停駐的對話方塊，並將它附加至`CPaneDialog`物件。|
|`CPaneDialog::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CPaneDialog::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|會處理[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)訊息。 (重新定義`CBasePane::HandleInitDialog`。)|
|`CPaneDialog::OnEraseBkgnd`|會處理[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)訊息。 (重新定義[CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)。)|
|`CPaneDialog::OnLButtonDblClk`|會處理[需要知道 WM_LBUTTONDBLCLK](/windows/desktop/inputdev/wm-lbuttondblclk)訊息。 (重新定義[CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)。)|
|`CPaneDialog::OnLButtonDown`|會處理[WM_LBUTTONDOWN](/windows/desktop/inputdev/wm-lbuttondown)訊息。 (重新定義[CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)。)|
|`CPaneDialog::OnUpdateCmdUI`|由架構呼叫以更新對話方塊視窗。 (覆寫[cdockablepane:: Onupdatecmdui](cdockablepane-class.md)。)|
|`CPaneDialog::OnWindowPosChanging`|會處理[WM_WINDOWPOSCHANGING](/windows/desktop/winmsg/wm-windowposchanging)訊息。 (重新定義[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)。)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定對話方塊中，是一個 OLE 控制項容器的範本。|

## <a name="remarks"></a>備註

建構`CPaneDialog`兩個步驟中的物件。 首先，建構您的程式碼中的物件。 其次，呼叫[CPaneDialog::Create](#create)。 您必須指定有效的資源範本名稱或範本識別碼，並將指標傳遞給父視窗。 否則，在建立程序會失敗。 對話方塊中，必須指定 WS_CHILD 和 WS_VISIBLE 樣式。 我們建議，您也可以指定所需 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 樣式。 如需詳細資訊，請參閱 <<c0> [ 的視窗樣式](styles-used-by-mfc.md#window-styles)。

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

建立停駐的對話方塊中，並將它附加至`CPaneDialog`物件。

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

*lpszWindowName*<br/>
[in][停駐] 對話方塊中的名稱。

*pParentWnd*<br/>
[in]父視窗的點。

*bHasGripper*<br/>
[in]使用標題 (gripper); 建立停駐的對話方塊中，則為 TRUE否則為 FALSE。

*lpszTemplateName*<br/>
[in]資源的對話方塊範本的名稱。

*nStyle*<br/>
[in]Windows 樣式。

*nID*<br/>
[in]控制項 id。

*nIDTemplate*<br/>
[in]對話方塊範本資源識別碼。

*dwTabbedStyle*<br/>
[in]使用者控制項的另一個窗格拖放這個控制項窗格的標題時所產生的索引標籤式視窗的樣式。 預設值是 AFX_CBRS_REGULAR_TABS。 如需詳細資訊，請參閱的 < 備註 > 一節[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。

*dwControlBarStyle*<br/>
[in]其他的樣式屬性。 預設值是 AFX_DEFAULT_DOCKING_PANE_STYLE。 如需詳細資訊，請參閱的 < 備註 > 一節[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)方法。

### <a name="return-value"></a>傳回值

如果這個方法成功，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範如何使用`Create`方法中的`CPaneDialog`類別。 此範例中是屬於[設定窗格大小範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

會處理[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)訊息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
[in]接受預設的鍵盤焦點之控制項的控制代碼。

*lParam*<br/>
[in]指定額外的初始化資料。

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。 此外，TRUE 設定所指定的控制項的鍵盤焦點*wParam*參數;FALSE 可避免設定預設鍵盤焦點。

### <a name="remarks"></a>備註

架構會使用這個方法初始化的控制項和對話方塊的外觀。 它會顯示對話方塊之前，架構會呼叫這個方法。

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

指定對話方塊中，是一個 OLE 控制項容器的範本。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
[in]對話方塊範本，用來建立對話方塊物件的指標。 此參數的值會接著傳遞至[COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>傳回值

永遠為 TRUE。

### <a name="remarks"></a>備註

這個方法支援[COccManager](../../mfc/reference/coccmanager-class.md)類別，用來管理 OLE 控制項站台和 ActiveX 控制項。 _AFX_OCC_DIALOG_INFO 結構 afxocc.h 標頭檔中定義。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)<br/>
[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
