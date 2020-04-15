---
title: COccManager 類別
ms.date: 11/04/2016
f1_keywords:
- COccManager
- AFXOCC/COccManager
- AFXOCC/COccManager::CreateContainer
- AFXOCC/COccManager::CreateDlgControls
- AFXOCC/COccManager::CreateSite
- AFXOCC/COccManager::GetDefBtnCode
- AFXOCC/COccManager::IsDialogMessage
- AFXOCC/COccManager::IsLabelControl
- AFXOCC/COccManager::IsMatchingMnemonic
- AFXOCC/COccManager::OnEvent
- AFXOCC/COccManager::PostCreateDialog
- AFXOCC/COccManager::PreCreateDialog
- AFXOCC/COccManager::SetDefaultButton
- AFXOCC/COccManager::SplitDialogTemplate
helpviewer_keywords:
- COccManager [MFC], CreateContainer
- COccManager [MFC], CreateDlgControls
- COccManager [MFC], CreateSite
- COccManager [MFC], GetDefBtnCode
- COccManager [MFC], IsDialogMessage
- COccManager [MFC], IsLabelControl
- COccManager [MFC], IsMatchingMnemonic
- COccManager [MFC], OnEvent
- COccManager [MFC], PostCreateDialog
- COccManager [MFC], PreCreateDialog
- COccManager [MFC], SetDefaultButton
- COccManager [MFC], SplitDialogTemplate
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
ms.openlocfilehash: 5637a4709e90bb14caff3fe4e396487e62e213e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360355"
---
# <a name="coccmanager-class"></a>COccManager 類別

管理各種自訂控制項網站；由 `COleControlContainer` 和 `COleControlSite` 物件實作。

## <a name="syntax"></a>語法

```
class COccManager : public CNoTrackObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COcc 管理員:建立容器](#createcontainer)|建立 `COleContainer` 物件。|
|[COcc管理員::創建Dlg控制](#createdlgcontrols)|創建由關聯`COleContainer`物件託管的 ActiveX 控制件。|
|[COcc經理:創建網站](#createsite)|建立 `COleClientSite` 物件。|
|[COcc經理:取得DefBtn代碼](#getdefbtncode)|檢索默認按鈕的代碼。|
|[COcc經理::對話消息](#isdialogmessage)|確定對話框消息的目標。|
|[COcc管理員::是標籤控制](#islabelcontrol)|確定指定的控制項是否為標籤控制項。|
|[COcc經理:是匹配的Mnemonic](#ismatchingmnemonic)|確定當前助記符是否與指定控制項的助記符匹配。|
|[COcc經理:在活動](#onevent)|嘗試處理指定事件。|
|[COcc經理::P創造對話](#postcreatedialog)|釋放在創建對話框期間分配的資源。|
|[COcc經理::P重新創建對話](#precreatedialog)|處理 ActiveX 控件的對話方塊樣本。|
|[COcc 管理員:設定預設按鈕](#setdefaultbutton)|切換指定控制項的預設狀態。|
|[COcc管理員:分割對話範本](#splitdialogtemplate)|將任何現有的 ActiveX 控制件與指定對話方塊樣本中的常用控制件分開。|

## <a name="remarks"></a>備註

基類`CNoTrackObject`是未記錄的基類(位於 AFXTLS 中)。H)。 設計為供 MFC 框架使用,派生自`CNoTrackObject`類的 類不受記憶體洩漏檢測。 不建議您直接從`CNoTrackObject`派生。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>需求

**標題:** afxocc.h

## <a name="coccmanagercreatecontainer"></a><a name="createcontainer"></a>COcc 管理員:建立容器

由框架調用以創建控制項容器。

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向與自定義網站容器關聯的視窗物件的指標。

### <a name="return-value"></a>傳回值

指向新創建的容器的指標;指向新創建的容器的指標。否則 NULL。

### <a name="remarks"></a>備註

有關建立自訂網站的詳細資訊,請參閱[COleControl 容器::附加控制網站](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。

## <a name="coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COcc管理員::創建Dlg控制

呼叫此函數以創建由*pOccDialogInfo*參數指定的 ActiveX 控制項。

```
virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    LPCTSTR lpszResourceName,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);

virtual BOOL CreateDlgControls(
    CWnd* pWndParent,
    void* lpResource,
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pwnd 父級*<br/>
指向對話框物件的父級的指標。

*lpsz 資源名稱*<br/>
正在建立的資源的名稱。

*pOccDialog 資訊*<br/>
指向用於創建對話框物件的對話框範本的指標。

*lp資源*<br/>
指向資源的指標。

### <a name="return-value"></a>傳回值

如果控件已成功創建,則非零;否則為零。

## <a name="coccmanagercreatesite"></a><a name="createsite"></a>COcc經理:創建網站

由框架調用以創建一個控制網站,由*pCtrlCont*指向的容器託管。

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>參數

*pCtrlCont*<br/>
指向承載新控制件網站的控制容器的指標。

### <a name="return-value"></a>傳回值

指向新創建的控制件網站的指標。

### <a name="remarks"></a>備註

重寫此函數,使用[COleControlControlSite](../../mfc/reference/colecontrolsite-class.md)派生類創建自定義控制項網站。

每個控件容器可以承載多個網站。 建立有多個呼叫的其他網站`CreateSite`。

## <a name="coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COcc經理:取得DefBtn代碼

呼叫此函數以確定控制項是否為預設按鈕。

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
包含按鈕控制的視窗物件。

### <a name="return-value"></a>傳回值

下列其中一個值：

- DLGC_DEFPUSHBUTTON控制項是對話框中的預設按鈕。

- DLGC_UNDEFPUSHBUTTON控制項不是對話框中的預設按鈕。

- **0**控制項不是按鈕。

## <a name="coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COcc經理::對話消息

由框架調用以確定消息是否用於指定的對話方塊,如果是,則處理消息。

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*普恩德德格*<br/>
指向消息的預期目標對話框的指標。

*lpMsg*<br/>
指向包含要檢查`MSG`的消息的結構的指標。

### <a name="return-value"></a>傳回值

處理消息時非零;否則為零。

### <a name="remarks"></a>備註

的默認行為`IsDialogMessage`是檢查鍵盤消息並將其轉換為相應對話框的選擇。 例如,按下 TAB 鍵時,選擇下一個控制項或控制元件元件。

重寫此函數,為發送到指定對話方塊的消息提供自定義行為。

## <a name="coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COcc管理員::是標籤控制

呼叫此函數以確定指定的控制項是否為標籤控制項。

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含控制項的視窗的指標。

### <a name="return-value"></a>傳回值

如果控件是標籤,則非零;否則零

### <a name="remarks"></a>備註

標籤控制項類似於排序中下一個控制項的標籤。

## <a name="coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COcc經理:是匹配的Mnemonic

呼叫此函數以確定當前助記符是否與控制項表示的表示匹配。

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含控制項的視窗的指標。

*lpMsg*<br/>
指向要匹配的助記符的消息的指標。

### <a name="return-value"></a>傳回值

如果助記符與控件匹配,則非零;否則零

### <a name="remarks"></a>備註

## <a name="coccmanageronevent"></a><a name="onevent"></a>COcc經理:在活動

由框架調用以處理指定的事件。

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>參數

*pCmdTarget*<br/>
測試事件`CCmdTarget`的物件的指標

*idCtrl*<br/>
控件的資源識別碼。

*pEvent*<br/>
正在處理的事件。

*pHandlerInfo*<br/>
`OnEvent`如果不是 NULL, 請填`pTarget``pmf`寫結構`AFX_CMDHANDLERINFO`的和成員,而不是調度命令。 通常,此參數應為 NULL。

### <a name="return-value"></a>傳回值

如果處理了事件,則非零,否則為零。

### <a name="remarks"></a>備註

重寫此函數以自定義預設事件處理過程。

## <a name="coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COcc經理::P重新創建對話

框架調用在創建實際對話方塊之前處理 ActiveX 控制件的對話方塊樣本。

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>參數

*pOccDialog 資訊*<br/>
包含`_AFX_OCC_DIALOG_INFO`對話方塊範本和對話方塊託管的任何 ActiveX 控制件的資訊。

*pOrigTemplate*<br/>
指向用於創建對話框的對話框的對話框的指標。

### <a name="return-value"></a>傳回值

指向用於創建對話框的對話框的對話框範本結構的指標。

### <a name="remarks"></a>備註

默認行為調用`SplitDialogTemplate`,確定是否存在任何 ActiveX 控件,然後返回由此產生的對話方塊樣本。

重寫此函數以自定義創建承載 ActiveX 控制件的對話方塊的過程。

## <a name="coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COcc經理::P創造對話

框架調用以釋放分配給對話框範本的記憶體。

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialog 資訊*<br/>
包含`_AFX_OCC_DIALOG_INFO`對話方塊範本和對話方塊託管的任何 ActiveX 控制件的資訊。

### <a name="remarks"></a>備註

此記憶體由 調用`SplitDialogTemplate`分配給分配,並用於對話方塊中的任何託管 ActiveX 控制件。

重寫此函數以自定義清理對話框物件使用的任何資源的過程。

## <a name="coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COcc 管理員:設定預設按鈕

調用此函數將控制項設定為預設按鈕。

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含控制項的視窗的指標。

*b預設*<br/>
如果控件應成為默認按鈕,則非零;否則為零。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 控件必須設置OLEMISC_ACTSLIKEBUTTON狀態位。 有關OLEMISC標誌的詳細資訊,請參閱Windows SDK中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)主題。

## <a name="coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COcc管理員:分割對話範本

由框架調用以從公共對話框控制項拆分 ActiveX 控制件。

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>參數

*pTemplate*<br/>
指向要檢查的對話框範本的指標。

*ppOleDlg 專案*<br/>
指向作為 ActiveX 控制件的對話方塊項的指標清單。

### <a name="return-value"></a>傳回值

指向僅包含非 ActiveX 控制件的對話方塊範本結構的指標。 如果不存在 ActiveX 控制項,則傳回 NULL。

### <a name="remarks"></a>備註

如果找到任何 ActiveX 控制件,將分析範本,並創建新樣本,其中僅包含非 ActiveX 控制件。 在此過程中找到的任何 ActiveX 控制項都添加到*ppOleDlgItems*中。

如果範本中沒有 ActiveX 控制項,則傳*回 NULL。*

> [!NOTE]
> 為新範本分配的記憶體將在`PostCreateDialog`函數中釋放。

重寫此函數以自定義此過程。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COle 控制網站類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
