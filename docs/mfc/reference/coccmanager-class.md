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
ms.openlocfilehash: a83f58b8de2411577d9fc025f7a8f8dc535ea8b3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276646"
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
|[COccManager::CreateContainer](#createcontainer)|建立 `COleContainer` 物件。|
|[COccManager::CreateDlgControls](#createdlgcontrols)|建立 ActiveX 控制項，由相關聯裝載`COleContainer`物件。|
|[COccManager::CreateSite](#createsite)|建立 `COleClientSite` 物件。|
|[COccManager::GetDefBtnCode](#getdefbtncode)|擷取預設按鈕的程式碼。|
|[COccManager::IsDialogMessage](#isdialogmessage)|判斷目標的對話訊息。|
|[COccManager::IsLabelControl](#islabelcontrol)|判斷指定的控制項是否為 label 控制項。|
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|判斷目前的助憶鍵是否符合指定之控制項的助憶鍵。|
|[COccManager::OnEvent](#onevent)|嘗試處理指定的事件。|
|[COccManager::PostCreateDialog](#postcreatedialog)|釋出配置期間建立對話方塊資源。|
|[COccManager::PreCreateDialog](#precreatedialog)|處理適用於 ActiveX 控制項的對話方塊範本。|
|[COccManager::SetDefaultButton](#setdefaultbutton)|切換指定的控制項的預設狀態。|
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|分開指定的對話方塊範本中的通用控制項中的任何現有的 ActiveX 控制項。|

## <a name="remarks"></a>備註

基底類別， `CNoTrackObject`，是未記載的基底類別 （位於 AFXTLS。H)。 主要是供 MFC 架構中，類別衍生自`CNoTrackObject`類別免套用的記憶體流失偵測。 不建議您直接從衍生`CNoTrackObject`。

## <a name="inheritance-hierarchy"></a>繼承階層

`CNoTrackObject`

`COccManager`

## <a name="requirements"></a>需求

**標頭：** afxocc.h

##  <a name="createcontainer"></a>  COccManager::CreateContainer

由架構呼叫以建立控制項的容器。

```
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
自訂站台容器相關聯的視窗物件的指標。

### <a name="return-value"></a>傳回值

新建立的容器; 指標否則為 NULL。

### <a name="remarks"></a>備註

如需有關如何建立自訂網站的詳細資訊，請參閱 < [COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。

##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls

呼叫此函式以建立所指定的 ActiveX 控制項*pOccDialogInfo*參數。

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
對話方塊物件的父代指標。

*lpszResourceName*<br/>
正在建立資源的名稱。

*pOccDialogInfo*<br/>
指標，用來建立對話方塊物件的對話方塊範本。

*lpResource*<br/>
資源的指標。

### <a name="return-value"></a>傳回值

如果控制項已成功; 建立為非零否則為零。

##  <a name="createsite"></a>  COccManager::CreateSite

由架構呼叫以建立控制項的站台，由容器所指*pCtrlCont*。

```
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>參數

*pCtrlCont*<br/>
裝載新的控制項站台的控制項容器指標。

### <a name="return-value"></a>傳回值

新建立的控制項站台指標。

### <a name="remarks"></a>備註

覆寫這個函式來建立自訂控制項站台，使用您[COleControlSite](../../mfc/reference/colecontrolsite-class.md)-衍生的類別。

每個控制項容器可以裝載多個站台。 建立含有多個呼叫的其他站台`CreateSite`。

##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode

呼叫此函式來判斷控制項是否為預設按鈕。

```
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
視窗物件，包含按鈕控制項。

### <a name="return-value"></a>傳回值

下列其中一個值：

- DLGC_DEFPUSHBUTTON 控制項是對話方塊中的 [預設] 按鈕。

- DLGC_UNDEFPUSHBUTTON 控制項不是對話方塊中的 [預設] 按鈕。

- **0**控制項不是一個按鈕。

##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage

由架構呼叫以判斷是否訊息是針對指定的對話方塊中，因此，如果是，處理訊息。

```
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,
    LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*pWndDlg*<br/>
預期的目標對話方塊中，訊息的指標。

*lpMsg*<br/>
指標`MSG`結構，其中包含要檢查的訊息。

### <a name="return-value"></a>傳回值

如果訊息已處理，非零值。否則為零。

### <a name="remarks"></a>備註

預設行為`IsDialogMessage`是檢查是否有鍵盤訊息，並將它們轉換成對應的對話方塊中的選取項目。 比方說，TAB 鍵，按下時，會選取下一個控制項群組。

此函式可為訊息傳送至指定的對話方塊中提供自訂行為來覆寫。

##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl

呼叫此函式可判斷指定的控制項是否為 label 控制項。

```
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含控制項視窗的指標。

### <a name="return-value"></a>傳回值

非零值，如果控制項的標籤。否則為零

### <a name="remarks"></a>備註

標籤控制項是其中的作用就像任何控制項是下一步 在此順序中的標籤。

##  <a name="ismatchingmnemonic"></a>  COccManager::IsMatchingMnemonic

呼叫此函式可判斷目前的助憶鍵是否符合表示的控制項。

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
包含控制項視窗的指標。

*lpMsg*<br/>
指標，包含這個助憶鍵來比對的訊息。

### <a name="return-value"></a>傳回值

如果助憶鍵符合控制項中，為非零否則為零

### <a name="remarks"></a>備註

##  <a name="onevent"></a>  COccManager::OnEvent

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
指標`CCmdTarget`嘗試處理事件的物件

*idCtrl*<br/>
控制項的資源識別碼。

*pEvent*<br/>
所處理的事件。

*pHandlerInfo*<br/>
如果不是 NULL，`OnEvent`填寫`pTarget`並`pmf`的成員`AFX_CMDHANDLERINFO`結構，而不是分派命令。 一般而言，這個參數應該是 NULL。

### <a name="return-value"></a>傳回值

如果事件已處理，否則為零，非零值。

### <a name="remarks"></a>備註

覆寫此函式以自訂預設事件處理程序。

##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog

由架構呼叫以處理 ActiveX 控制項的對話方塊範本，然後再建立實際的對話方塊。

```
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,
    const DLGTEMPLATE* pOrigTemplate);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO`結構，其中包含有關對話方塊範本和任何由對話方塊裝載的 ActiveX 控制項。

*pOrigTemplate*<br/>
對話方塊範本，以便用來建立對話方塊中的指標。

### <a name="return-value"></a>傳回值

用來建立對話方塊中的對話方塊範本結構指標。

### <a name="remarks"></a>備註

預設行為會呼叫`SplitDialogTemplate`決定是否有任何 ActiveX 控制項存在，則會傳回結果的對話方塊範本。

覆寫此函式可自訂的建立裝載 ActiveX 控制項的對話方塊程序。

##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog

由架構呼叫以釋出配置給對話方塊範本的記憶體。

```
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>參數

*pOccDialogInfo*<br/>
`_AFX_OCC_DIALOG_INFO`結構，其中包含有關對話方塊範本和任何由對話方塊裝載的 ActiveX 控制項。

### <a name="remarks"></a>備註

這個記憶體配置呼叫`SplitDialogTemplate`，和用於任何裝載的 ActiveX 控制項在對話方塊中。

覆寫此函式以自訂清除對話方塊物件所使用的任何資源的程序。

##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton

呼叫此函式可將控制項設定為預設按鈕。

```
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,
    BOOL bDefault);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含控制項視窗的指標。

*bDefault*<br/>
如果控制項應該成為預設按鈕，為非零否則為零。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  控制項必須有 OLEMISC_ACTSLIKEBUTTON 狀態位元組。 如需有關 OLEMISC 旗標的詳細資訊，請參閱[OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) Windows SDK 中的主題。

##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate

由架構呼叫以將分割從通用對話方塊控制項的 ActiveX 控制項。

```
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,
    DLGITEMTEMPLATE** ppOleDlgItems);
```

### <a name="parameters"></a>參數

*pTemplate*<br/>
要檢查的對話方塊範本的指標。

*ppOleDlgItems*<br/>
指標對話方塊項目做為 ActiveX 控制項的清單。

### <a name="return-value"></a>傳回值

包含只有非 ActiveX 控制項對話方塊範本結構的指標。 如果沒有 ActiveX 控制項，則會傳回 NULL。

### <a name="remarks"></a>備註

如果找不到任何 ActiveX 控制項，範本就會分析，並建立新的範本，包含只有非 ActiveX 控制項。 此過程中發現任何 ActiveX 控制項加入至*ppOleDlgItems*。

如果沒有在範本中的 ActiveX 控制項，則會傳回 NULL *。*

> [!NOTE]
>  為新的範本會釋出配置的記憶體`PostCreateDialog`函式。

覆寫此函式以自訂此處理序。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)<br/>
[COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
