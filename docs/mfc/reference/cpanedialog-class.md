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
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502986"
---
# <a name="cpanedialog-class"></a>CPaneDialog 類別

`CPaneDialog`類別支援非模式、可停駐的對話方塊。

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
|[CPaneDialog::Create](#create)|建立可停駐的對話方塊, 並將其`CPaneDialog`附加至物件。|
|`CPaneDialog::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CPaneDialog::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)訊息。 (重新`CBasePane::HandleInitDialog`定義)。|
|`CPaneDialog::OnEraseBkgnd`|處理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)訊息。 (重新定義[CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd))。|
|`CPaneDialog::OnLButtonDblClk`|處理[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk)訊息。 (重新定義[CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk))。|
|`CPaneDialog::OnLButtonDown`|處理[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown)訊息。 (重新定義[CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown))。|
|`CPaneDialog::OnUpdateCmdUI`|由架構呼叫以更新對話方塊視窗。 (覆寫[CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md)。)|
|`CPaneDialog::OnWindowPosChanging`|處理[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging)訊息。 (重新定義[CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging))。|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|指定做為 OLE 控制項容器之對話方塊的範本。|

## <a name="remarks"></a>備註

以兩個步驟來建立物件。`CPaneDialog` 首先, 在您的程式碼中建立物件。 第二, 呼叫[CPaneDialog:: Create](#create)。 您必須指定有效的資源範本名稱或範本識別碼, 並將指標傳遞至父視窗。 否則, 建立程式將會失敗。 對話方塊必須指定 WS_CHILD 和 WS_VISIBLE 樣式。 我們建議您也要指定 WS_CLIPCHILDREN 和 WS_CLIPSIBLINGS 樣式。 如需詳細資訊, 請參閱[視窗樣式](styles-used-by-mfc.md#window-styles)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>需求

**標頭:** afxpanedialog。h

##  <a name="create"></a>CPaneDialog:: Create

建立停駐對話方塊, 並將其附加至`CPaneDialog`物件。

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
在固定對話方塊的名稱。

*pParentWnd*<br/>
在指向父視窗。

*bHasGripper*<br/>
在TRUE 表示建立具有標題 (移駐站) 的停駐對話方塊;否則為 FALSE。

*lpszTemplateName*<br/>
在資源對話方塊範本的名稱。

*nStyle*<br/>
在Windows 樣式。

*nID*<br/>
在控制項識別碼。

*nIDTemplate*<br/>
在對話方塊範本的資源識別碼。

*dwTabbedStyle*<br/>
在當使用者將另一個控制項窗格拖曳至這個控制項窗格的標題時, 所產生的索引標籤式視窗樣式。 預設值為 AFX_CBRS_REGULAR_TABS。 如需詳細資訊, 請參閱[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法的「備註」一節。

*dwControlBarStyle*<br/>
在其他樣式屬性。 預設值為 AFX_DEFAULT_DOCKING_PANE_STYLE。 如需詳細資訊, 請參閱[CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)方法的「備註」一節。

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範如何`Create` `CPaneDialog`在類別中使用方法。 這個範例是 [[設定窗格大小] 範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)訊息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
在控制項的控制碼, 用來接收預設鍵盤焦點。

*lParam*<br/>
在指定其他初始化資料。

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。 此外, TRUE 也會將鍵盤焦點設定為*wParam*參數所指定的控制項;FALSE 可避免設定預設的鍵盤焦點。

### <a name="remarks"></a>備註

架構會使用這個方法來初始化控制項和對話方塊的外觀。 架構會在顯示對話方塊之前呼叫這個方法。

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

指定做為 OLE 控制項容器之對話方塊的範本。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
在用來建立對話方塊物件之對話方塊範本的指標。 這個參數的值後續會傳遞至[COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>傳回值

一律為 TRUE。

### <a name="remarks"></a>備註

這個方法支援[COccManager](../../mfc/reference/coccmanager-class.md)類別, 它會管理 OLE 控制項網站和 ActiveX 控制項。 _AFX_OCC_DIALOG_INFO 結構定義于 afxocc 標頭檔中。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)<br/>
[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
