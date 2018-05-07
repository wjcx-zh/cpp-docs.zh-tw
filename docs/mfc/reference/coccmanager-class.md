---
title: COccManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b292196eb6ac8178ba43f0e66bd4814368c916fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[COccManager::CreateContainer](#createcontainer)|建立**COleContainer**物件。|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|建立由相關聯的 ActiveX 控制項`COleContainer`物件。|  
|[COccManager::CreateSite](#createsite)|建立 `COleClientSite` 物件。|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|擷取預設按鈕的程式碼。|  
|[COccManager::IsDialogMessage](#isdialogmessage)|判斷目標的對話訊息。|  
|[COccManager::IsLabelControl](#islabelcontrol)|判斷指定的控制項是否為 label 控制項。|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|判斷目前的助憶鍵是否符合指定之控制項的助憶鍵。|  
|[COccManager::OnEvent](#onevent)|嘗試處理指定的事件。|  
|[COccManager::PostCreateDialog](#postcreatedialog)|釋出配置期間建立對話方塊資源。|  
|[COccManager::PreCreateDialog](#precreatedialog)|處理 ActiveX 控制項的對話方塊範本。|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|切換為指定的控制項的預設狀態。|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|指定的對話方塊範本中的通用控制項可將任何現有的 ActiveX 控制項。|  
  
## <a name="remarks"></a>備註  
 基底類別， **CNoTrackObject**，是未記載之基底類別 （位於 AFXTLS。H)。 設計來供 MFC 架構中，類別衍生自**CNoTrackObject**類別不受記憶體遺漏偵測。 不建議您直接從衍生**CNoTrackObject**。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxocc.h  
  
##  <a name="createcontainer"></a>  COccManager::CreateContainer  
 若要建立的控制項容器架構呼叫。  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 自訂站台容器相關聯的視窗物件的指標。  
  
### <a name="return-value"></a>傳回值  
 變數的指標，新建的容器，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如需有關如何建立自訂網站的詳細資訊，請參閱[COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。  
  
##  <a name="createdlgcontrols"></a>  COccManager::CreateDlgControls  
 呼叫此函式以建立所指定的 ActiveX 控制項`pOccDialogInfo`參數。  
  
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
 *pWndParent*  
 父系對話方塊物件的指標。  
  
 `lpszResourceName`  
 正在建立的資源名稱。  
  
 `pOccDialogInfo`  
 對話方塊範本用來建立對話方塊物件指標。  
  
 `lpResource`  
 資源的指標。  
  
### <a name="return-value"></a>傳回值  
 如果控制項已成功; 建立為非零否則為零。  
  
##  <a name="createsite"></a>  COccManager::CreateSite  
 由架構呼叫以建立控制項的站台，由容器所指`pCtrlCont`。  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>參數  
 `pCtrlCont`  
 裝載新的控制項站台控制容器的指標。  
  
### <a name="return-value"></a>傳回值  
 指標，新建的控制項站台。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來建立自訂控制項網站的 url，使用您[COleControlSite](../../mfc/reference/colecontrolsite-class.md)-衍生的類別。  
  
 每個控制項容器可以裝載多個站台。 建立含有多個呼叫的其他站台`CreateSite`。  
  
##  <a name="getdefbtncode"></a>  COccManager::GetDefBtnCode  
 呼叫此函式可判斷控制項是否為預設按鈕。  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 視窗物件，包含按鈕控制項。  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
- **DLGC_DEFPUSHBUTTON**控制項是對話方塊中的預設按鈕。  
  
- **DLGC_UNDEFPUSHBUTTON**控制項不是對話方塊中的預設按鈕。  
  
- **0**控制項不是一個按鈕。  
  
##  <a name="isdialogmessage"></a>  COccManager::IsDialogMessage  
 由架構呼叫以判斷是否訊息適用於指定的對話方塊中，而且，如果是，處理訊息。  
  
```  
virtual BOOL IsDialogMessage(
    CWnd* pWndDlg,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>參數  
 *pWndDlg*  
 預期的目標對話方塊訊息的指標。  
  
 `lpMsg`  
 指標`MSG`結構，其中包含要檢查的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果已處理訊息為非零否則為零。  
  
### <a name="remarks"></a>備註  
 預設行為`IsDialogMessage`是檢查鍵盤訊息並將它們轉換成對應的對話方塊中選取項目。 比方說，TAB 鍵，按下時，會選取下一個控制項或群組的控制項。  
  
 覆寫此函式可為訊息傳送至指定的對話方塊中提供自訂行為。  
  
##  <a name="islabelcontrol"></a>  COccManager::IsLabelControl  
 呼叫此函式可判斷指定的控制項是否為 label 控制項。  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含控制項視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果控制項是標籤。否則為零  
  
### <a name="remarks"></a>備註  
 Label 控制項是就像是任何控制項是下一步 在順序中的標籤。  
  
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
 `pWnd`  
 包含控制項視窗的指標。  
  
 `lpMsg`  
 要比對包含助憶鍵的訊息指標。  
  
### <a name="return-value"></a>傳回值  
 如果助憶鍵符合控制項，則為非零否則為零  
  
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
 *pCmdTarget*  
 指標`CCmdTarget`嘗試處理事件的物件  
  
 `idCtrl`  
 控制項的資源識別碼。  
  
 `pEvent`  
 所處理的事件。  
  
 `pHandlerInfo`  
 如果沒有**NULL**，`OnEvent`填入**pTarget**和**pmf**成員**AFX_CMDHANDLERINFO**而不是結構分派命令。 此參數通常應該**NULL**。  
  
### <a name="return-value"></a>傳回值  
 非零，如果事件已處理，否則為零。  
  
### <a name="remarks"></a>備註  
 此函式以自訂預設事件處理程序會覆寫。  
  
##  <a name="precreatedialog"></a>  COccManager::PreCreateDialog  
 由之前要處理的 ActiveX 控制項的對話方塊範本建立實際的對話方塊架構呼叫。  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>參數  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**結構，其中包含對話方塊範本和任何對話方塊所裝載的 ActiveX 控制項的詳細資訊。  
  
 *pOrigTemplate*  
 要用來建立對話方塊中的對話方塊範本指標。  
  
### <a name="return-value"></a>傳回值  
 用來建立 對話方塊的對話方塊範本結構指標。  
  
### <a name="remarks"></a>備註  
 預設行為會呼叫`SplitDialogTemplate`判斷是否有任何 ActiveX 控制項存在，則會傳回結果的對話方塊範本。  
  
 此函式可自訂的建立裝載 ActiveX 控制項的對話方塊程序會覆寫。  
  
##  <a name="postcreatedialog"></a>  COccManager::PostCreateDialog  
 由架構呼叫以釋放記憶體配置給對話方塊範本。  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>參數  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**結構，其中包含對話方塊範本和任何對話方塊所裝載的 ActiveX 控制項的詳細資訊。  
  
### <a name="remarks"></a>備註  
 此記憶體配置呼叫`SplitDialogTemplate`，以及用於在對話方塊中任何裝載 ActiveX 控制項。  
  
 此函式以自訂清除對話方塊物件所使用的任何資源的程序會覆寫。  
  
##  <a name="setdefaultbutton"></a>  COccManager::SetDefaultButton  
 呼叫此函式可將控制項設定為預設按鈕。  
  
```  
static void AFX_CDECL SetDefaultButton(
    CWnd* pWnd,  
    BOOL bDefault);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含控制項視窗的指標。  
  
 `bDefault`  
 如果控制項應成為預設按鈕，則為非零否則為零。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  該控制項必須**OLEMISC_ACTSLIKEBUTTON**狀態設定位元。 如需有關**OLEMISC**旗標，請參閱[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) Windows SDK 中的主題。  
  
##  <a name="splitdialogtemplate"></a>  COccManager::SplitDialogTemplate  
 由架構呼叫以將分割從通用對話方塊控制項的 ActiveX 控制項。  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>參數  
 `pTemplate`  
 要檢查的對話方塊範本指標。  
  
 `ppOleDlgItems`  
 指標對話方塊項目為 ActiveX 控制項的清單。  
  
### <a name="return-value"></a>傳回值  
 包含僅非 ActiveX 控制項的對話方塊範本結構指標。 如果沒有 ActiveX 控制項不存在， **NULL**傳回。  
  
### <a name="remarks"></a>備註  
 如果找不到任何 ActiveX 控制項，分析範本，並建立新的範本，包含只有非 ActiveX 控制項。 此程序期間找到任何 ActiveX 控制項加入至`ppOleDlgItems`。  
  
 如果在範本中，沒有 ActiveX 控制項**NULL**傳回*。*  
  
> [!NOTE]
>  為新範本將會在釋出配置的記憶體`PostCreateDialog`函式。  
  
 此函式以自訂這個程序會覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
