---
title: "COccManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COccManager
dev_langs:
- C++
helpviewer_keywords:
- custom controls [MFC], sites
- COccManager class
- CNoTrackObject class
- ActiveX control containers [C++], control site
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
caps.latest.revision: 20
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
ms.openlocfilehash: 14a75c491a7061d921d6c0c250c6224f4e7d2f04
ms.lasthandoff: 02/24/2017

---
# <a name="coccmanager-class"></a>COccManager 類別
管理各種自訂控制項網站；由 `COleControlContainer` 和 `COleControlSite` 物件實作。  
  
## <a name="syntax"></a>語法  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COccManager::CreateContainer](#createcontainer)|建立**COleContainer**物件。|  
|[COccManager::CreateDlgControls](#createdlgcontrols)|建立裝載由相關聯的 ActiveX 控制項`COleContainer`物件。|  
|[COccManager::CreateSite](#createsite)|建立 `COleClientSite` 物件。|  
|[COccManager::GetDefBtnCode](#getdefbtncode)|擷取預設按鈕的程式碼。|  
|[COccManager::IsDialogMessage](#isdialogmessage)|判斷目標的對話訊息。|  
|[COccManager::IsLabelControl](#islabelcontrol)|判斷指定的控制項是否為 label 控制項。|  
|[COccManager::IsMatchingMnemonic](#ismatchingmnemonic)|判斷目前的助憶鍵是否符合指定之控制項的助憶鍵。|  
|[COccManager::OnEvent](#onevent)|嘗試處理指定的事件。|  
|[COccManager::PostCreateDialog](#postcreatedialog)|釋出配置期間建立對話方塊資源。|  
|[COccManager::PreCreateDialog](#precreatedialog)|處理 ActiveX 控制項的對話方塊範本。|  
|[COccManager::SetDefaultButton](#setdefaultbutton)|切換指定之控制項的預設狀態。|  
|[COccManager::SplitDialogTemplate](#splitdialogtemplate)|在指定的對話方塊範本中的通用控制項可將任何現有的 ActiveX 控制項。|  
  
## <a name="remarks"></a>備註  
 基底類別， **CNoTrackObject**，一個未記載的基底類別 （位於 AFXTLS。H)。 專供 MFC 架構中，類別衍生自**CNoTrackObject**類別不受記憶體遺漏偵測。 不建議您直接從衍生**CNoTrackObject**。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CNoTrackObject`  
  
 `COccManager`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxocc.h  
  
##  <a name="a-namecreatecontainera--coccmanagercreatecontainer"></a><a name="createcontainer"></a>COccManager::CreateContainer  
 若要建立的控制項容器架構呼叫。  
  
```  
virtual COleControlContainer* CreateContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 自訂站台容器相關聯的視窗物件的指標。  
  
### <a name="return-value"></a>傳回值  
 指向新建立的容器。否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如需有關如何建立自訂網站的詳細資訊，請參閱[COleControlContainer::AttachControlSite](../../mfc/reference/colecontrolcontainer-class.md#attachcontrolsite)。  
  
##  <a name="a-namecreatedlgcontrolsa--coccmanagercreatedlgcontrols"></a><a name="createdlgcontrols"></a>COccManager::CreateDlgControls  
 呼叫此函式來建立所指定的 ActiveX 控制項`pOccDialogInfo`參數。  
  
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
 在對話方塊範本，用來建立對話方塊物件指標。  
  
 `lpResource`  
 資源的指標。  
  
### <a name="return-value"></a>傳回值  
 如果控制項已成功; 建立為非零否則為零。  
  
##  <a name="a-namecreatesitea--coccmanagercreatesite"></a><a name="createsite"></a>COccManager::CreateSite  
 若要建立控制項的站台，由容器所指架構呼叫`pCtrlCont`。  
  
```  
virtual COleControlSite* CreateSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>參數  
 `pCtrlCont`  
 裝載新的控制項站台控制容器的指標。  
  
### <a name="return-value"></a>傳回值  
 新建立的控制項站台的指標。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來建立自訂控制項網站的 url，使用您[COleControlSite](../../mfc/reference/colecontrolsite-class.md)-衍生的類別。  
  
 每個控制項容器可以裝載多個站台。 建立其他站台與多個呼叫`CreateSite`。  
  
##  <a name="a-namegetdefbtncodea--coccmanagergetdefbtncode"></a><a name="getdefbtncode"></a>COccManager::GetDefBtnCode  
 呼叫此函式以判斷控制項是否為預設按鈕。  
  
```  
static DWORD AFX_CDECL GetDefBtnCode(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 視窗物件，包含按鈕控制項。  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
- **DLGC_DEFPUSHBUTTON**控制項是在對話方塊中的預設按鈕。  
  
- **DLGC_UNDEFPUSHBUTTON**控制項不是在對話方塊中的預設按鈕。  
  
- **0**控制項不是一個按鈕。  
  
##  <a name="a-nameisdialogmessagea--coccmanagerisdialogmessage"></a><a name="isdialogmessage"></a>COccManager::IsDialogMessage  
 若要判斷是否訊息是針對指定的對話方塊，而且，如果是，處理的訊息架構呼叫。  
  
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
  
 覆寫此函式可為訊息傳送至指定的對話方塊提供自訂行為。  
  
##  <a name="a-nameislabelcontrola--coccmanagerislabelcontrol"></a><a name="islabelcontrol"></a>COccManager::IsLabelControl  
 呼叫此函式可判斷指定的控制項是否為 label 控制項。  
  
```  
static BOOL AFX_CDECL IsLabelControl(CWnd* pWnd);  
static BOOL AFX_CDECL IsLabelControl(COleControlSiteOrWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 包含控制項視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果控制項是標籤。否則為零  
  
### <a name="remarks"></a>備註  
 Label 控制項指的作用就像任何控制項是依順序排列的下一步的標籤。  
  
##  <a name="a-nameismatchingmnemonica--coccmanagerismatchingmnemonic"></a><a name="ismatchingmnemonic"></a>COccManager::IsMatchingMnemonic  
 呼叫此函式來判斷目前的助憶鍵是否符合表示的控制項。  
  
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
 指標，包含這個助憶鍵來比對的訊息。  
  
### <a name="return-value"></a>傳回值  
 如果助憶鍵比對的控制項，為非零否則為零  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoneventa--coccmanageronevent"></a><a name="onevent"></a>COccManager::OnEvent  
 處理指定的事件架構呼叫。  
  
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
 如果不是**NULL**，`OnEvent`填入**pTarget**和**pmf**成員**AFX_CMDHANDLERINFO**結構，而不是分派命令。 通常，這個參數應該是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果已處理事件，否則為零的非零值。  
  
### <a name="remarks"></a>備註  
 若要自訂預設事件處理程序，此函式會覆寫。  
  
##  <a name="a-nameprecreatedialoga--coccmanagerprecreatedialog"></a><a name="precreatedialog"></a>COccManager::PreCreateDialog  
 之前要處理的 ActiveX 控制項的對話方塊範本建立實際的對話方塊架構呼叫。  
  
```  
virtual const DLGTEMPLATE* PreCreateDialog(
    _AFX_OCC_DIALOG_INFO* pOccDialogInfo,  
    const DLGTEMPLATE* pOrigTemplate);
```  
  
### <a name="parameters"></a>參數  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**結構，其中包含對話方塊範本和任何對話方塊所裝載的 ActiveX 控制項的詳細資訊。  
  
 *pOrigTemplate*  
 對話方塊範本，以供建立對話方塊指標。  
  
### <a name="return-value"></a>傳回值  
 用來建立對話方塊中的對話方塊範本結構的指標。  
  
### <a name="remarks"></a>備註  
 預設行為會呼叫`SplitDialogTemplate`判斷是否有任何 ActiveX 控制項存在，然後傳回結果的對話方塊範本。  
  
 覆寫這個函式來自訂建立裝載 ActiveX 控制項 對話方塊中的程序。  
  
##  <a name="a-namepostcreatedialoga--coccmanagerpostcreatedialog"></a><a name="postcreatedialog"></a>COccManager::PostCreateDialog  
 若要釋放記憶體配置的對話方塊範本架構呼叫。  
  
```  
virtual void PostCreateDialog(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>參數  
 `pOccDialogInfo`  
 **_AFX_OCC_DIALOG_INFO**結構，其中包含對話方塊範本和任何對話方塊所裝載的 ActiveX 控制項的詳細資訊。  
  
### <a name="remarks"></a>備註  
 這個記憶體配置呼叫`SplitDialogTemplate`，和用於對話方塊中的任何裝載 ActiveX 控制項。  
  
 此函式以自訂清除對話方塊物件所使用的任何資源的程序會覆寫。  
  
##  <a name="a-namesetdefaultbuttona--coccmanagersetdefaultbutton"></a><a name="setdefaultbutton"></a>COccManager::SetDefaultButton  
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
 非零，如果控制項的預設按鈕。否則為零。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  控制項必須要有**OLEMISC_ACTSLIKEBUTTON**狀態設定位元。 如需有關**OLEMISC**旗標，請參閱[OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497)中的主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesplitdialogtemplatea--coccmanagersplitdialogtemplate"></a><a name="splitdialogtemplate"></a>COccManager::SplitDialogTemplate  
 若要分割從通用對話方塊控制項的 ActiveX 控制項架構呼叫。  
  
```  
virtual DLGTEMPLATE* SplitDialogTemplate(
    const DLGTEMPLATE* pTemplate,  
    DLGITEMTEMPLATE** ppOleDlgItems);
```  
  
### <a name="parameters"></a>參數  
 `pTemplate`  
 要檢查的對話方塊範本指標。  
  
 `ppOleDlgItems`  
 指標對話方塊項目做為 ActiveX 控制項的清單。  
  
### <a name="return-value"></a>傳回值  
 包含只有非 ActiveX 控制項的對話方塊範本結構指標。 如果沒有 ActiveX 控制項不存在， **NULL**傳回。  
  
### <a name="remarks"></a>備註  
 如果找不到任何 ActiveX 控制項，範本就會分析，並建立新的範本，包含只有非 ActiveX 控制項。 此過程中發現任何 ActiveX 控制項加入至`ppOleDlgItems`。  
  
 如果在範本中，有沒有 ActiveX 控制項**NULL**傳回*。*  
  
> [!NOTE]
>  為新範本釋放配置的記憶體`PostCreateDialog`函式。  
  
 此函式以自訂這個程序會覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlSite 類別](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)

