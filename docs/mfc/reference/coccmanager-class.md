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
ms.openlocfilehash: c2a49e3396879e5f1e0864ab5342b57541c6b36c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865934"
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
|[COccManager：： CreateContainer](#createcontainer)|建立 `COleContainer` 物件。|
|[COccManager::CreateDlgControls](#createdlgcontrols)|建立由相關聯 `COleContainer` 物件主控的 ActiveX 控制項。|
|[COccManager：： CreateSite](#createsite)|建立 `COleClientSite` 物件。|
|[COccManager::GetDefBtnCode](#getdefbtncode)|抓取預設按鈕的程式碼。|
|[COccManager::IsDialogMessage](#isdialogmessage)|決定對話訊息的目標。|
|[COccManager::IsLabelControl](#islabelcontrol)|判斷指定的控制項是否為標籤控制項。|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|判斷目前的助憶鍵是否符合指定之控制項的助憶鍵。|
|[COccManager：： OnEvent](#onevent)|嘗試處理指定的事件。|
|[COccManager：:P ostCreateDialog](#postcreatedialog)|釋放在對話建立期間配置的資源。|
|[COccManager：:P reCreateDialog](#precreatedialog)|處理 ActiveX 控制項的對話方塊範本。|
|[COccManager::SetDefaultButton](#setdefaultbutton)|切換指定控制項的預設狀態。|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|將任何現有的 ActiveX 控制項與指定之對話方塊範本中的通用控制項隔開。|

## <a name="remarks"></a>備註

基類（`CNoTrackObject`）是未記載的基類（位於 AFXTLS 中。H）。 由 MFC 架構所設計，衍生自 `CNoTrackObject` 類別的類別不會受到記憶體流失偵測的豁免。 不建議您直接從 `CNoTrackObject`衍生。

## <a name="inheritance-hierarchy"></a>繼承階層

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>需求

**標頭：** afxocc。h

##  <a name="createcontainer"></a>COccManager：： CreateContainer

由架構呼叫以建立控制項容器。

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
與自訂網站容器相關聯之 window 物件的指標。

### <a name="return-value"></a>傳回值

新建立之容器的指標;否則為 Null。

### <a name="remarks"></a>備註

如需建立自訂網站的詳細資訊，請參閱[COleControlContainer：： AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。

##  <a name="createdlgcontrols"></a>COccManager::CreateDlgControls

呼叫此函式可建立*pOccDialogInfo*參數所指定的 ActiveX 控制項。

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

*pWndParent*<br/>
對話方塊物件父系的指標。

*lpszResourceName*<br/>
要建立之資源的名稱。

*pOccDialogInfo*<br/>
用來建立對話方塊物件之對話方塊範本的指標。

*lpResource*<br/>
資源的指標。

### <a name="return-value"></a>傳回值

如果成功建立控制項，則為非零;否則為零。

##  <a name="createsite"></a>COccManager：： CreateSite

由架構呼叫，以建立由*pCtrlCont*所指向之容器所裝載的控制網站。

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>參數

*pCtrlCont*<br/>
裝載新控制項網站之控制項容器的指標。

### <a name="return-value"></a>傳回值

新建立之控制項網站的指標。

### <a name="remarks"></a>備註

覆寫此函式，以使用[COleControlSite](../../mfc/reference/colecontrolsite-class.md)衍生的類別來建立自訂控制項網站。

每個控制項容器都可以裝載多個網站。 建立具有多個 `CreateSite`呼叫的其他網站。

##  <a name="getdefbtncode"></a>COccManager::GetDefBtnCode

呼叫此函式可判斷控制項是否為預設的 [推送] 按鈕。

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含按鈕控制項的視窗物件。

### <a name="return-value"></a>傳回值

下列其中一個值：

- DLGC_DEFPUSHBUTTON 控制項是對話方塊中的預設按鈕。

- DLGC_UNDEFPUSHBUTTON 控制項不是對話方塊中的預設按鈕。

- **0**控制項不是按鈕。

##  <a name="isdialogmessage"></a>COccManager::IsDialogMessage

由架構呼叫以判斷訊息是否適用于指定的對話方塊，如果是，則會處理訊息。

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*pWndDlg*<br/>
訊息之預定目標對話的指標。

*lpMsg*<br/>
`MSG` 結構的指標，其中包含要檢查的訊息。

### <a name="return-value"></a>傳回值

如果已處理訊息，則為非零值;否則為零。

### <a name="remarks"></a>備註

`IsDialogMessage` 的預設行為是檢查鍵盤訊息，並將其轉換成對應對話方塊的選取專案。 例如，按下 TAB 鍵時，會選取下一個控制項或控制項群組。

覆寫此函式，為傳送至指定對話的訊息提供自訂行為。

##  <a name="islabelcontrol"></a>COccManager::IsLabelControl

呼叫此函式可判斷指定的控制項是否為標籤控制項。

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含控制項之視窗的指標。

### <a name="return-value"></a>傳回值

如果控制項是標籤，則為非零值;否則為零

### <a name="remarks"></a>備註

標籤控制項就像順序中下一個控制項的標籤一樣。

##  <a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic

呼叫此函式可判斷目前的助憶鍵是否與控制項所表示的相符。

```
static BOOL AFX_CDECL IsMatchingMnemonic(
    CWnd* pWnd,
    LPMSG lpMsg);

static BOOL AFX_CDECL IsMatchingMnemonic(
    COleControlSiteOrWnd* pWnd,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含控制項之視窗的指標。

*lpMsg*<br/>
包含要比對之助憶鍵的訊息指標。

### <a name="return-value"></a>傳回值

如果助憶鍵與控制項相符，則為非零值。否則為零

### <a name="remarks"></a>備註

##  <a name="onevent"></a>COccManager：： OnEvent

由架構呼叫以處理指定的事件。

```
virtual BOOL OnEvent(
    CCmdTarget* pCmdTarget,
    UINT idCtrl,
    AFX_EVENT* pEvent,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>參數

*pCmdTarget*<br/>
嘗試處理事件之 `CCmdTarget` 物件的指標

*idCtrl*<br/>
控制項的資源識別碼。

*pEvent*<br/>
正在處理的事件。

*pHandlerInfo*<br/>
如果不是 Null，`OnEvent` 會填入 `AFX_CMDHANDLERINFO` 結構的 `pTarget` 和 `pmf` 成員，而不是分派命令。 通常，這個參數應該是 Null。

### <a name="return-value"></a>傳回值

如果事件已處理，則為非零，否則為零。

### <a name="remarks"></a>備註

覆寫此函式以自訂預設事件處理常式。

##  <a name="precreatedialog"></a>COccManager：:P reCreateDialog

由架構呼叫，以處理 ActiveX 控制項的對話方塊範本，然後再建立實際的對話方塊。

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` 結構，其中包含對話方塊範本以及對話方塊所裝載的任何 ActiveX 控制項的資訊。

*pOrigTemplate*<br/>
要在建立對話方塊時使用之對話方塊範本的指標。

### <a name="return-value"></a>傳回值

用來建立對話方塊之對話方塊範本結構的指標。

### <a name="remarks"></a>備註

預設行為會呼叫 `SplitDialogTemplate`，判斷是否有任何 ActiveX 控制項存在，然後傳回結果對話方塊範本。

覆寫此函式，以自訂建立裝載 ActiveX 控制項之對話方塊的進程。

##  <a name="postcreatedialog"></a>COccManager：:P ostCreateDialog

由架構呼叫以釋放配置給對話方塊範本的記憶體。

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO` 結構，其中包含對話方塊範本以及對話方塊所裝載的任何 ActiveX 控制項的資訊。

### <a name="remarks"></a>備註

這個記憶體是由對 `SplitDialogTemplate`的呼叫所配置，並用於對話方塊中任何裝載的 ActiveX 控制項。

覆寫此函式，以自訂清除對話方塊物件所使用之任何資源的進程。

##  <a name="setdefaultbutton"></a>COccManager::SetDefaultButton

呼叫此函式可將控制項設定為預設按鈕。

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含控制項之視窗的指標。

*bDefault*<br/>
如果控制項應該成為預設按鈕，則為非零。否則為零。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  控制項必須設定 OLEMISC_ACTSLIKEBUTTON 狀態位。 如需 OLEMISC 旗標的詳細資訊，請參閱 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)主題。

##  <a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate

由架構呼叫，以從通用對話方塊控制項分割 ActiveX 控制項。

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>參數

*pTemplate*<br/>
要檢查之對話方塊範本的指標。

*ppOleDlgItems*<br/>
屬於 ActiveX 控制項之對話方塊專案的指標清單。

### <a name="return-value"></a>傳回值

僅包含非 ActiveX 控制項之對話方塊範本結構的指標。 如果沒有 ActiveX 控制項存在，則會傳回 Null。

### <a name="remarks"></a>備註

如果找到任何 ActiveX 控制項，則會分析範本，並建立只包含非 ActiveX 控制項的新範本。 在此程式期間找到的任何 ActiveX 控制項都會加入至*ppOleDlgItems*。

如果範本中沒有任何 ActiveX 控制項，則會傳回 Null *。*

> [!NOTE]
>  配置給新範本的記憶體會在 `PostCreateDialog` 函式中釋放。

覆寫此函式以自訂此進程。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
