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
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364130"
---
# <a name="cpanedialog-class"></a>CPaneDialog 類別

該`CPaneDialog`類支援一個無模式、可停靠的對話方塊。

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
|[CPane對話:建立](#create)|創建可停靠的對話框並將其附加到`CPaneDialog`物件。|
|`CPaneDialog::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CPaneDialog::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CPaneDialog::手柄對話](#handleinitdialog)|處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 ( 重新`CBasePane::HandleInitDialog`定義 .)|
|`CPaneDialog::OnEraseBkgnd`|處理[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息。 (重新定義[Cwnd:onEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|處理[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk)消息。 (重新定義[Cwnd:onButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|處理[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown)消息。 (重新定義[Cwnd::打開按鈕](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|由框架調用以更新對話框視窗。 ( 覆寫[可嵌入窗格:開啟更新 CmdUI](cdockablepane-class.md)。)|
|`CPaneDialog::OnWindowPosChanging`|處理[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging)消息。 (重新定義[Cwnd:在 WindowPos 更改](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::設置OccDialog資訊](#setoccdialoginfo)|指定作為 OLE 控制元件容器的對話框的樣本。|

## <a name="remarks"></a>備註

分兩`CPaneDialog`步構造物件。 首先,在代碼中構造物件。 第二,呼叫[CPaneDialog:建立](#create)。 您必須指定有效的資源範本名稱或範本 ID,並將指標傳遞給父視窗。 否則,創建過程將失敗。 該對話框必須指定WS_CHILD和WS_VISIBLE樣式。 我們建議您也指定WS_CLIPCHILDREN和WS_CLIPSIBLINGS樣式。 有關詳細資訊,請參閱[視窗樣式](styles-used-by-mfc.md#window-styles)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPane對話](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>需求

**標題:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPane對話:建立

創建停靠對話框並將其附加到`CPaneDialog`物件。

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

*lpsz 視窗名稱*<br/>
[在]停靠對話框的名稱。

*pparentwnd*<br/>
[在]指向父視窗。

*b哈斯格裡珀*<br/>
[在]TRUE 以創建帶有標題(夾持器)的停靠對話方塊;否則,FALSE。

*lpszTemplate 名稱*<br/>
[在]資源對話框範本的名稱。

*nStyle*<br/>
[在]Windows 樣式。

*nID*<br/>
[在]控件識別碼。

*nIDTemplate*<br/>
[在]對話框範本的資源 ID。

*dwTabbed 樣式*<br/>
[在]當使用者將另一個控制器窗格拖動到此控制元件窗格的標題上時,該選項卡式視窗的樣式。 默認值為AFX_CBRS_REGULAR_TABS。 有關詳細資訊,請參閱[CBasePane:createEx](../../mfc/reference/cbasepane-class.md#createex)方法的備註部分。

*dwControlBar 樣式*<br/>
[在]其他樣式屬性。 默認值為AFX_DEFAULT_DOCKING_PANE_STYLE。 有關詳細資訊,請參閱[CBasePane:createEx](../../mfc/reference/cbasepane-class.md#createex)方法的備註部分。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下面的示例演示如何在`Create``CPaneDialog`類中使用 方法。 此示例是[「設定窗格大小」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::手柄對話

處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
[在]處理接收默認鍵盤焦點的控制項。

*lParam*<br/>
[在]指定其他初始化數據。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。 此外,TRUE 將鍵盤焦點設置到*wParam*參數指定的控制件;FALSE 可防止設置預設鍵盤焦點。

### <a name="remarks"></a>備註

框架使用此方法初始化控制件和對話框的外觀。 框架在顯示對話框之前調用此方法。

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::設置OccDialog資訊

指定作為 OLE 控制元件容器的對話框的樣本。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialog 資訊*<br/>
[在]指向用於創建對話框物件的對話框範本的指標。 此參數的值隨後傳遞到[COccManager:createDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)方法。

### <a name="return-value"></a>傳回值

一律為 TRUE。

### <a name="remarks"></a>備註

此方法支援[COccManager](../../mfc/reference/coccmanager-class.md)類,該類管理 OLE 控制網站和 ActiveX 控件。 _AFX_OCC_DIALOG_INFO結構在 afxocc.h 標頭檔中定義。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)
