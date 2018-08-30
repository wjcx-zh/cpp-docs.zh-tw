---
title: COleControlSite 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
dev_langs:
- C++
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f79917e34a749048696f320a8311978acc2739f4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202851"
---
# <a name="colecontrolsite-class"></a>COleControlSite 類別
提供自訂用戶端控制項介面的支援。  
  
## <a name="syntax"></a>語法  
  
```  
class COleControlSite : public CCmdTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControlSite::COleControlSite](#colecontrolsite)|建構 `COleControlSite` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|將裝載控制項的預設屬性繫結至資料來源。|  
|[COleControlSite::BindProperty](#bindproperty)|將裝載的控制項屬性繫結至資料來源。|  
|[COleControlSite::CreateControl](#createcontrol)|建立裝載的 ActiveX 控制項。|  
|[COleControlSite::DestroyControl](#destroycontrol)|終結裝載的控制項。|  
|[COleControlSite::DoVerb](#doverb)|執行特定動詞的裝載的控制項。|  
|[COleControlSite::EnableDSC](#enabledsc)|可讓資料來源控制項站台。|  
|[COleControlSite::EnableWindow](#enablewindow)|可讓控制項站台。|  
|[COleControlSite::FreezeEvents](#freezeevents)|指定控制項站台接受事件。|  
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|擷取裝載控制項的預設按鈕程式碼。|  
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|擷取控制項的識別項。|  
|[COleControlSite::GetEventIID](#geteventiid)|擷取的事件介面裝載控制項的 ID。|  
|[COleControlSite::GetExStyle](#getexstyle)|擷取控制項站台延伸的樣式。|  
|[COleControlSite::GetProperty](#getproperty)|擷取特定的裝載的控制項屬性。|  
|[COleControlSite::GetStyle](#getstyle)|擷取控制項站台的樣式。|  
|[COleControlSite::GetWindowText](#getwindowtext)|擷取裝載控制項的文字。|  
|[COleControlSite::InvokeHelper](#invokehelper)|裝載控制項的特定方法來叫用。|  
|[COleControlSite::InvokeHelperV](#invokehelperv)|裝載的控制項具有變數引數清單的特定方法來叫用。|  
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|判斷控制項是否為預設按鈕，在視窗中。|  
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|檢查控制項站台的可見狀態。|  
|[COleControlSite::ModifyStyle](#modifystyle)|修改目前的延伸樣式的控制項站台。|  
|[COleControlSite::ModifyStyleEx](#modifystyleex)|修改控制項站台的目前樣式。|  
|[COleControlSite::MoveWindow](#movewindow)|變更控制項站台的位置。|  
|[COleControlSite::QuickActivate](#quickactivate)|快速啟動裝載的控制項。|  
|[COleControlSite::SafeSetProperty](#safesetproperty)|設定的屬性或方法的控制項，而不擲回例外狀況的機會。|  
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|在視窗中設定的預設按鈕。|  
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|擷取控制項的識別項。|  
|[COleControlSite::SetFocus](#setfocus)|將焦點設定至控制項站台。|  
|[COleControlSite::SetProperty](#setproperty)|設定裝載控制項的特定屬性。|  
|[COleControlSite::SetPropertyV](#setpropertyv)|設定裝載的控制項具有變數引數清單的特定屬性。|  
|[COleControlSite::SetWindowPos](#setwindowpos)|設定控制項站台位置。|  
|[COleControlSite::SetWindowText](#setwindowtext)|設定裝載控制項的文字。|  
|[COleControlSite::ShowWindow](#showwindow)|顯示或隱藏控制項站台。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControlSite::GetControlInfo](#getcontrolinfo)|擷取鍵盤資訊和裝載控制項的助憶鍵。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|判斷裝載的控制項是否為將無視窗控制項。|  
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|包含有關控制項的鍵盤處理。|  
|[COleControlSite::m_dwEventSink](#m_dweventsink)|控制項的連接點的 cookie。|  
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|裝載控制項的其他狀態。|  
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|`IPropertyNotifySink` Cookie 的控制項。|  
|[COleControlSite::m_dwStyle](#m_dwstyle)|裝載控制項的樣式。|  
|[COleControlSite::m_hWnd](#m_hwnd)|控制項站台的控制代碼。|  
|[COleControlSite::m_iidEvents](#m_iidevents)|裝載控制項的事件介面的識別碼。|  
|[COleControlSite::m_nID](#m_nid)|裝載控制項的 ID。|  
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|指標`IOleInPlaceActiveObject`裝載控制項的物件。|  
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|裝載控制項的容器。|  
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|指標`IOleInPlaceObject`裝載控制項的物件。|  
|[COleControlSite::m_pObject](#m_pobject)|指標`IOleObjectInterface`控制項的介面。|  
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|指標`IOleInPlaceObjectWindowless`控制項的介面。|  
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|裝載控制項的視窗物件指標。|  
|[COleControlSite::m_rect](#m_rect)|控制項站台的維度。|  
  
## <a name="remarks"></a>備註  
 這項支援是供內嵌的 ActiveX 控制項取得資訊的位置和範圍，其顯示站台、 其 moniker，其使用者介面、 其環境的屬性和其容器所提供的其他資源的主要方法。 `COleControlSite` 完整實作[IOleControlSite](/windows/desktop/api/ocidl/nn-ocidl-iolecontrolsite)， [IOleInPlaceSite](/windows/desktop/api/oleidl/nn-oleidl-ioleinplacesite)， [IOleClientSite](/windows/desktop/api/oleidl/nn-oleidl-ioleclientsite)， [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink)， `IBoundObjectSite`，`INotifyDBEvents`， [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md)介面。 此外，也被實作 IDispatch 介面 （環境的屬性和事件接收提供支援）。  
  
 若要建立 ActiveX 控制項站台使用`COleControlSite`，自`COleControlSite`。 在您`CWnd`-容器 （例如，您的對話方塊） 的衍生的類別覆寫`CWnd::CreateControlSite`函式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlSite`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxocc.h  
  
##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty  
 將呼叫物件的預設簡單繫結的屬性，做為標記類型程式庫中的繫結至基礎資料來源控制項的資料來源、 使用者名稱、 密碼和 SQL 屬性所定義的資料指標。  
  
```  
virtual void BindDefaultProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    LPCTSTR szFieldName,  
    CWnd* pDSCWnd);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 指定要繫結至資料來源控制項的資料繫結控制項屬性的 DISPID。  
  
 *vtProp*  
 指定要繫結屬性的型別 — 比方說，VT_BSTR、 VT_VARIANT、 等等。  
  
 *szFieldName*  
 指定資料來源控制項，此屬性會繫結所提供的資料指標中的資料行的名稱。  
  
 *pDSCWnd*  
 指標`CWnd`-裝載資料來源控制項的屬性會繫結的衍生的物件。  
  
### <a name="remarks"></a>備註  
 `CWnd`呼叫此函式的物件必須是資料繫結控制項。  
  
##  <a name="bindproperty"></a>  COleControlSite::BindProperty  
 呼叫物件的簡單繫結的屬性，為標示的型別程式庫中的繫結至基礎資料來源控制項的資料來源、 使用者名稱、 密碼和 SQL 屬性所定義的資料指標。  
  
```  
virtual void BindProperty(
    DISPID dwDispId,  
    CWnd* pWndDSC);
```  
  
### <a name="parameters"></a>參數  
 *dwDispId*  
 指定要繫結至資料來源控制項的資料繫結控制項屬性的 DISPID。  
  
 *pWndDSC*  
 指標`CWnd`-裝載資料來源控制項的屬性會繫結的衍生的物件。  
  
### <a name="remarks"></a>備註  
 `CWnd`呼叫此函式的物件必須是資料繫結控制項。  
  
##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite  
 建構新`COleControlSite`物件。  
  
```  
explicit COleControlSite(COleControlContainer* pCtrlCont);
```  
  
### <a name="parameters"></a>參數  
 *pCtrlCont*  
 控制項的容器 （這表示裝載 AtiveX 控制項的視窗） 指標。  
  
### <a name="remarks"></a>備註  
 此函式會呼叫[COccManager::CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer)函式。 如需有關自訂建立容器的詳細資訊，請參閱[COccManager::CreateSite](../../mfc/reference/coccmanager-class.md#createsite)。  
  
##  <a name="createcontrol"></a>  COleControlSite::CreateControl  
 建立 ActiveX 控制項，由`COleControlSite`物件。  
  
```  
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);

 
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,  
    REFCLSID clsid,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const POINT* ppt,  
    const SIZE* psize,  
    UINT nID,  
    CFile* pPersist = NULL,  
    BOOL bStorage = FALSE,  
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pWndCtrl*  
 表示控制項的視窗物件的指標。  
  
 *clsid*  
 控制項的唯一類別 ID。  
  
 *lpszWindowName*  
 要在控制項中顯示的文字指標。 （如果有的話），請設定 winodw 的標題或文字屬性的值。  
  
 *cheaderctrl:: Create*  
 視窗樣式。 底下會列出可用的樣式**備註**一節。  
  
 *rect*  
 指定控制項的大小和位置。 它可以是`CRect`物件或`RECT`結構。  
  
 *nID*  
 指定控制項的子視窗識別碼。  
  
 *pPersist*  
 指標`CFile`包含控制項的永續性狀態。 預設值是 NULL，表示控制項，而不還原其狀態從任何持續性儲存體初始化本身。 如果不是 NULL，它應該是一個指向`CFile`-衍生物件，包含控制項的永續性資料，資料流或儲存體的形式。 這項資料可以儲存在用戶端上啟用。 `CFile`可以包含其他資料，但必須設定為永續性資料的第一個位元組時呼叫它讀寫指標`CreateControl`。  
  
 *bStorage*  
 指出是否在資料*pPersist*應解譯為`IStorage`或`IStream`資料。 如果中的資料*pPersist*是儲存體*bStorage*應該是 TRUE。 如果中的資料*pPersist*是資料流*bStorage*應該是 FALSE。 預設值為 FALSE。  
  
 *bstrLicKey*  
 選擇性的授權金鑰資料。 這項資料只能在建立需要的執行階段授權金鑰的控制項。 如果此控制項支援授權，您必須提供授權金鑰建立的控制項才會成功。 預設值是 NULL。  
  
 *ppt*  
 指標`POINT`結構，包含控制項的左上角。 控制項的大小取決於 windows 7 *psize*。 *Ppt*並*psize*值是選擇性的方法，來指定大小和位置 opf 控制項。  
  
 *psize*  
 指標`SIZE`結構，包含控制項的大小。 值來決定左上角*ppt*。 *Ppt*並*psize*值是選擇性的方法，來指定大小和位置 opf 控制項。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 只是 Windows 的子集*cheaderctrl:: Create*旗標受到`CreateControl`:  
  
- WS_VISIBLE 會建立一開始即可見的視窗。 如果您想看見立即，像一般的 windows 控制項的必要項。  
  
- WS_DISABLED 會建立一開始會停用的視窗。 停用的視窗無法接收來自使用者的輸入。 如果控制項具有已啟用屬性，可以設定。  
  
- WS_BORDER 會建立具有精簡列框線的視窗。 如果控制項的框線樣式屬性，可以設定。  
  
- WS_GROUP 指定控制項群組的第一個控制項。 使用者可以變更鍵盤焦點從群組中的一個控制項到下一個使用方向鍵。 之後的第一個控制項屬於相同的群組，以 WS_GROUP 樣式定義的所有控制項。 WS_GROUP 樣式的下一個控制項結束該群組，並開始下一步 群組。  
  
- WS_TABSTOP 指定當使用者按下 TAB 鍵時，可以接收鍵盤焦點的控制項。 按下 TAB 鍵若 WS_TABSTOP 樣式的下一個控制項来變更鍵盤焦點。  
  
 您可以使用第二個多載來建立預設大小的控制項。  
  
##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl  
 終結`COleControlSite`物件。  
  
```  
virtual BOOL DestroyControl();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 一旦完成，該物件會從記憶體釋放，以及任何指向該物件已不再有效。  
  
##  <a name="doverb"></a>  COleControlSite::DoVerb  
 執行指定的動詞命令。  
  
```  
virtual HRESULT DoVerb(
    LONG nVerb,  
    LPMSG lpMsg = NULL);
```  
  
### <a name="parameters"></a>參數  
 *nVerb*  
 指定要執行的動詞命令。 它可以包含下列其中一項：  
  
|值|意義|符號|  
|-----------|-------------|------------|  
|0|主動詞命令|OLEIVERB_PRIMARY|  
|-1|次要的動詞命令|(無)|  
|1|顯示供編輯的物件。|OLEIVERB_SHOW|  
|-2|編輯另一個視窗中的項目。|OLEIVERB_OPEN|  
|-3|隱藏物件。|OLEIVERB_HIDE|  
|-4|控制會就地啟動。|OLEIVERB_UIACTIVATE|  
|-5|控制會就地啟動，而不需要額外的使用者介面項目。|OLEIVERB_INPLACEACTIVATE|  
|-7|顯示控制項的屬性。|OLEIVERB_PROPERTIES|  
  
 *lpMsg*  
 造成要啟動的項目之訊息的指標。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 透過控制項的直接呼叫此函式`IOleObject`介面，以執行指定的動詞命令。 如果此函式呼叫而擲回例外狀況，則會傳回 HRESULT 錯誤碼。  
  
 如需詳細資訊，請參閱 < [IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb) Windows SDK 中。  
  
##  <a name="enabledsc"></a>  COleControlSite::EnableDSC  
 可讓資料來源控制項站台。  
  
```  
virtual void EnableDSC();
```  
  
### <a name="remarks"></a>備註  
 由架構呼叫以啟用和初始化資料來源控制項站台。 覆寫這個函式，以提供自訂的行為。  
  
##  <a name="enablewindow"></a>  COleControlSite::EnableWindow  
 啟用或停用滑鼠和鍵盤輸入到控制站台。  
  
```  
virtual BOOL EnableWindow(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 *bEnable*  
 指定是否要啟用或停用視窗： 如果視窗輸入被啟用，否則為 FALSE，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果之前已停用的視窗，否則為 0。  
  
##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents  
 指定控制項站台，將處理或忽略從控制項所引發的事件。  
  
```  
void FreezeEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>參數  
 *bFreeze*  
 指定控制項站台是否想要停止接受事件。 非零值，如果控制項不接受事件;否則為零。  
  
### <a name="remarks"></a>備註  
 如果*bFreeze*為 TRUE 時，控制項站台要求要停止帶入事件的控制項。 如果*bFreeze*為 FALSE 時，控制項站台要求繼續引發事件的控制項。  
  
> [!NOTE]
>  控制項不需要停止引發事件，如果要求控制項站台。 它可以繼續引發，但控制項站台將會忽略所有後續的事件。  
  
##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo  
 擷取控制項的鍵盤助憶鍵和鍵盤行為的相關資訊。  
  
```  
void GetControlInfo();
```  
  
### <a name="remarks"></a>備註  
 資訊會儲存在[COleControlSite::m_ctlInfo](#m_ctlinfo)。  
  
##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode  
 判斷控制項是否為預設按鈕。  
  
```  
DWORD GetDefBtnCode();
```  
  
### <a name="return-value"></a>傳回值  
 可為下列其中一個值：  
  
- DLGC_DEFPUSHBUTTON 控制項是對話方塊中的 [預設] 按鈕。  
  
- DLGC_UNDEFPUSHBUTTON 控制項不是對話方塊中的 [預設] 按鈕。  
  
- **0**控制項不是一個按鈕。  
  
##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID  
 擷取控制項的識別項。  
  
```  
virtual int GetDlgCtrlID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制項的對話方塊項目識別項。  
  
##  <a name="geteventiid"></a>  COleControlSite::GetEventIID  
 擷取控制項的預設事件介面的指標。  
  
```  
BOOL GetEventIID(IID* piid);
```  
  
### <a name="parameters"></a>參數  
 *piid*  
 指標的介面 id。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功，否則為 0。 如果成功， *piid*包含控制項的預設事件介面的介面識別碼。  
  
##  <a name="getexstyle"></a>  COleControlSite::GetExStyle  
 擷取視窗的延伸的樣式。  
  
```  
virtual DWORD GetExStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [控制] 視窗的延伸樣式。  
  
### <a name="remarks"></a>備註  
 若要擷取規則的樣式，請呼叫[COleControlSite::GetStyle](#getstyle)。  
  
##  <a name="getproperty"></a>  COleControlSite::GetProperty  
 取得所指定的控制項屬性*dwDispID*。  
  
```  
virtual void GetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    void* pvProp) const;  
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性，在控制項的預設上找到的分派識別碼`IDispatch`介面，以擷取。  
  
 *vtProp*  
 指定要擷取屬性的型別。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *pvProp*  
 將會收到屬性值的變數位址。 它必須符合所指定的型別*vtProp*。  
  
### <a name="remarks"></a>備註  
 透過傳回的值*pvProp*。  
  
##  <a name="getstyle"></a>  COleControlSite::GetStyle  
 擷取控制項站台的樣式。  
  
```  
virtual DWORD GetStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 視窗的樣式。  
  
### <a name="remarks"></a>備註  
 如需可能值的清單，請參閱 < [Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 若要擷取的控制項站台的延伸的樣式，請呼叫[COleControlSite::GetExStyle](#getexstyle)。  
  
##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText  
 擷取控制項的目前文字。  
  
```  
virtual void GetWindowText(CString& str) const;  
```  
  
### <a name="parameters"></a>參數  
 *str*  
 參考`CString`物件，包含控制項的目前文字。  
  
### <a name="remarks"></a>備註  
 如果此控制項支援標題內建屬性，則會傳回此值。 如果不支援標題內建屬性，則會傳回文字屬性的值。  
  
##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper  
 叫用方法或屬性所指定*dwDispID*，在所指定的內容中*wFlags*。  
  
```  
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo, ...);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性或方法，在控制項上找到的分派識別碼`IDispatch`介面，以叫用。  
  
 *wFlags*  
 描述的 idispatch:: Invoke 的呼叫內容的旗標。 可能*wFlags*值，請參閱`IDispatch::Invoke`Windows SDK 中。  
  
 *vtRet*  
 指定傳回值的類型。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *pvRet*  
 要接收屬性值或傳回值之變數的位址。 它必須符合所指定的型別*vtRet*。  
  
 *pbParamInfo*  
 以 null 終止的字串的指定類型的下列參數的位元組指標*pbParamInfo*。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *...*  
 變數清單的參數，在指定的型別*pbParamInfo*。  
  
### <a name="remarks"></a>備註  
 *PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 變數引數清單被以...語法宣告。  
  
 此函式會將參數轉換為 VARIANTARG 值，然後再叫用`IDispatch::Invoke`控制項上的方法。 如果呼叫`IDispatch::Invoke`失敗，此函式會擲回例外狀況。 如果所傳回的狀態碼`IDispatch::Invoke`已`DISP_E_EXCEPTION`，此函式會擲回`COleDispatchException`物件，否則就會擲回`COleException`。  
  
##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV  
 叫用方法或屬性所指定*dwDispID*，在所指定的內容中*wFlags*。  
  
```  
virtual void InvokeHelperV(
    DISPID dwDispID,  
    WORD wFlags,  
    VARTYPE vtRet,  
    void* pvRet,  
    const BYTE* pbParamInfo,  
    va_list argList);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性或方法，在控制項上找到的分派識別碼`IDispatch`介面，以叫用。  
  
 *wFlags*  
 描述的 idispatch:: Invoke 的呼叫內容的旗標。  
  
 *vtRet*  
 指定傳回值的類型。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *pvRet*  
 要接收屬性值或傳回值之變數的位址。 它必須符合所指定的型別*vtRet*。  
  
 *pbParamInfo*  
 以 null 終止的字串的指定類型的下列參數的位元組指標*pbParamInfo*。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *argList*  
 變數引數清單的指標。  
  
### <a name="remarks"></a>備註  
 *PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 可以使用傳遞額外參數的方法或屬性所叫用*va_list*參數。  
  
 一般而言，會呼叫此函式`COleControlSite::InvokeHelper`。  
  
##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton  
 判斷控制項是否為預設按鈕。  
  
```  
BOOL IsDefaultButton();
```  
  
### <a name="return-value"></a>傳回值  
 如果控制項為非零的預設按鈕，在視窗中，否則為零。  
  
##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled  
 判斷是否已啟用控制項站台。  
  
```  
virtual BOOL IsWindowEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零值如果已啟用控制項，否則為零。  
  
### <a name="remarks"></a>備註  
 從控制項的已啟用內建屬性，擷取值。  
  
##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless  
 判斷物件是否為將無視窗控制項。  
  
```  
BOOL m_bIsWindowless;  
```  
  
### <a name="remarks"></a>備註  
 非零值如果控制項有沒有任何視窗，否則為零。  
  
##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo  
 控制要如何處理鍵盤輸入的資訊。  
  
```  
CONTROLINFO m_ctlInfo;  
```  
  
### <a name="remarks"></a>備註  
 這項資訊會儲存在[檓 CONTROLINFO](/windows/desktop/api/ocidl/ns-ocidl-tagcontrolinfo)結構。  
  
##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink  
 包含控制項的事件接收器中的連接點的 cookie。  
  
```  
DWORD m_dwEventSink;  
```  
  
##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus  
 包含有關控制項的其他資訊。  
  
```  
DWORD m_dwMiscStatus;  
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc)Windows SDK 中。  
  
##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink  
 包含[IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) cookie。  
  
```  
DWORD m_dwPropNotifySink;  
```  
  
##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle  
 包含控制項的視窗樣式。  
  
```  
DWORD m_dwStyle;  
```  
  
##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd  
 如果控制項是無視窗，包含控制項的 HWND，則為 NULL。  
  
```  
HWND m_hWnd;  
```  
  
##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents  
 包含控制項的預設事件接收器介面的介面 ID。  
  
```  
IID m_iidEvents;  
```  
  
##  <a name="m_nid"></a>  COleControlSite::m_nID  
 包含控制項的對話方塊項目 id。  
  
```  
UINT m_nID;  
```  
  
##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject  
 包含[和](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject)控制項的介面。  
  
```  
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;  
```  
  
##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont  
 包含控制項的容器 （表示的形式）。  
  
```  
COleControlContainer* m_pCtrlCont;  
```  
  
##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject  
 包含`IOleInPlaceObject` [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject)控制項的介面。  
  
```  
LPOLEINPLACEOBJECT m_pInPlaceObject;  
```  
  
##  <a name="m_pobject"></a>  COleControlSite::m_pObject  
 包含`IOleObjectInterface`控制項的介面。  
  
```  
LPOLEOBJECT m_pObject;  
```  
  
##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject  
 包含`IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)控制項的介面。  
  
```  
IOleInPlaceObjectWindowless* m_pWindowlessObject;  
```  
  
##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl  
 包含一個指向`CWnd`物件，表示控制項本身。  
  
```  
CWnd* m_pWndCtrl;  
```  
  
##  <a name="m_rect"></a>  COleControlSite::m_rect  
 包含控制項，相對於容器的視窗界限。  
  
```  
CRect m_rect;  
```  
  
##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle  
 修改控制項的樣式。  
  
```  
virtual BOOL ModifyStyle(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *dwRemove*  
 若要從目前的視窗樣式會移除樣式。  
  
 *dwAdd*  
 若要從目前的視窗樣式加入樣式。  
  
 *nFlags*  
 定位旗標的視窗。 如需可能值的清單，請參閱 < [SetWindowPos](https://msdn.microsoft.com/library/windows/desktop/ms633545) Windows SDK 中的函式。  
  
### <a name="return-value"></a>傳回值  
 如果樣式已變更，否則為零，非零值。  
  
### <a name="remarks"></a>備註  
 將修改控制項的內建 Enabled 屬性，以符合 WS_DISABLED 的設定。 將修改控制項的內建的框線樣式屬性，以符合 WS_BORDER 的要求的設定。 所有其他樣式會直接套用到控制項的視窗控制代碼，如果有的話。  
  
 修改控制項的視窗樣式。 要加入或移除的樣式可以結合使用的位元 OR ( &#124; ) 運算子。 請參閱[CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679)可用的視窗樣式的相關資訊的 Windows SDK 中的函式。  
  
 如果*nFlags*為非零值，`ModifyStyle`呼叫 Win32 函式`SetWindowPos`，並重新繪製視窗，結合*nFlags*具有下列四個旗標：  
  
- SWP_NOSIZE 會保留目前的大小。  
  
- SWP_NOMOVE 會保留目前的位置。  
  
- SWP_NOZORDER 會保留目前的 Z 順序。  
  
- SWP_NOACTIVATE 不會啟動視窗。  
  
 若要修改視窗的延伸樣式，請呼叫[ModifyStyleEx](#modifystyleex)。  
  
##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx  
 修改控制項的延伸的樣式。  
  
```  
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,  
    DWORD dwAdd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *dwRemove*  
 若要從目前的視窗樣式會移除延伸的樣式。  
  
 *dwAdd*  
 若要從目前的視窗樣式新增延伸的樣式。  
  
 *nFlags*  
 定位旗標的視窗。 如需可能值的清單，請參閱 < [SetWindowPos](https://msdn.microsoft.com/library/windows/desktop/ms633545) Windows SDK 中的函式。  
  
### <a name="return-value"></a>傳回值  
 如果樣式已變更，否則為零，非零值。  
  
### <a name="remarks"></a>備註  
 控制項的內建的 Appearance 屬性將會修改以符合 WS_EX_CLIENTEDGE 的設定。 所有其他延伸的視窗樣式會直接套用到控制項的視窗控制代碼，如果有的話。  
  
 修改擴充控制項的站台物件的樣式的視窗。 要加入或移除的樣式可以結合使用的位元 OR ( &#124; ) 運算子。 請參閱[CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680)可用的視窗樣式的相關資訊的 Windows SDK 中的函式。  
  
 如果*nFlags*為非零值，`ModifyStyleEx`呼叫 Win32 函式`SetWindowPos`，並重新繪製視窗，結合*nFlags*具有下列四個旗標：  
  
- SWP_NOSIZE 會保留目前的大小。  
  
- SWP_NOMOVE 會保留目前的位置。  
  
- SWP_NOZORDER 會保留目前的 Z 順序。  
  
- SWP_NOACTIVATE 不會啟動視窗。  
  
 若要修改視窗的延伸樣式，請呼叫[ModifyStyle](#modifystyle)。  
  
##  <a name="movewindow"></a>  COleControlSite::MoveWindow  
 變更控制項的位置。  
  
```  
virtual void MoveWindow(
    int x,  
    int y,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 *x*  
 左側視窗的新位置。  
  
 *y*  
 視窗頂端的新位置。  
  
 *nWidth*  
 新視窗的寬度  
  
 *nHeight*  
 新視窗的高度。  
  
##  <a name="quickactivate"></a>  COleControlSite::QuickActivate  
 快速啟動內含的控制項。  
  
```  
virtual BOOL QuickActivate();
```  
  
### <a name="return-value"></a>傳回值  
 非零值如果已啟用控制項站台，否則為零。  
  
### <a name="remarks"></a>備註  
 使用者會覆寫控制項的建立程序時，才應該呼叫此函式。  
  
 `IPersist*::Load`和`IPersist*::InitNew`快速啟動發生後，就應該呼叫方法。 在快速啟動過程中，控制項應該建立其容器的接收的連接。 不過，這些連線不會即時直到`IPersist*::Load`或`IPersist*::InitNew`已呼叫。  
  
##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty  
 設定所指定的控制項屬性*dwDispID*。  
  
```  
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性或方法，在控制項上找到的分派識別碼`IDispatch`介面，以設定。  
  
 *vtProp*  
 指定要設定屬性的型別。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *...*  
 所指定之類型的單一參數*vtProp*。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  不同於`SetProperty`和`SetPropertyV`，如果發生錯誤 （例如，嘗試設定不存在的屬性），會擲回任何例外狀況。  
  
##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton  
 將控制項設為預設按鈕。  
  
```  
void SetDefaultButton(BOOL bDefault);
```  
  
### <a name="parameters"></a>參數  
 *bDefault*  
 如果控制項應該成為預設按鈕，為非零否則為零。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  控制項必須有 OLEMISC_ACTSLIKEBUTTON 狀態位元組。  
  
##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID  
 變更控制項的對話方塊中的項目識別項的值。  
  
```  
virtual int SetDlgCtrlID(int nID);
```  
  
### <a name="parameters"></a>參數  
 *nID*  
 新的識別碼值。  
  
### <a name="return-value"></a>傳回值  
 如果成功，在前一個對話方塊項目識別碼的視窗;否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setfocus"></a>  COleControlSite::SetFocus  
 將焦點設定至控制項。  
  
```  
virtual CWnd* SetFocus();  
virtual CWnd* SetFocus(LPMSG lpmsg);
```  
  
### <a name="parameters"></a>參數  
 *lpmsg*  
 指標[MSG 結構](../../mfc/reference/msg-structure1.md)。 此結構中包含 Windows 訊息觸發`SetFocus`要求在目前的控制站所包含的控制項。  
  
### <a name="return-value"></a>傳回值  
 先前擁有焦點的視窗的指標。  
  
##  <a name="setproperty"></a>  COleControlSite::SetProperty  
 設定所指定的控制項屬性*dwDispID*。  
  
```  
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,  
    VARTYPE vtProp, ...);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性或方法，在控制項上找到的分派識別碼`IDispatch`介面，以設定。  
  
 *vtProp*  
 指定要設定屬性的型別。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *...*  
 所指定之類型的單一參數*vtProp*。  
  
### <a name="remarks"></a>備註  
 如果`SetProperty`遇到錯誤，擲回例外狀況。  
  
 例外狀況的類型取決於嘗試設定屬性或方法的傳回值。 如果傳回的值是`DISP_E_EXCEPTION`，則`COleDispatchExcpetion`擲回，否則為`COleException`。  
  
##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV  
 設定所指定的控制項屬性*dwDispID*。  
  
```  
virtual void SetPropertyV(
    DISPID dwDispID,  
    VARTYPE vtProp,  
    va_list argList);
```  
  
### <a name="parameters"></a>參數  
 *dwDispID*  
 識別屬性或方法，在控制項上找到的分派識別碼`IDispatch`介面，以設定。  
  
 *vtProp*  
 指定要設定屬性的型別。 如需可能的值，請參閱 < 備註 > 一節[coledispatchdriver:: Invokehelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)。  
  
 *argList*  
 引數清單的指標。  
  
### <a name="remarks"></a>備註  
 方法或屬性所叫用的額外參數可以是 passeed 使用*arg_list*參數。 如果`SetProperty`遇到錯誤，擲回例外狀況。  
  
 例外狀況的類型取決於嘗試設定屬性或方法的傳回值。 如果傳回的值是`DISP_E_EXCEPTION`，則`COleDispatchExcpetion`擲回，否則為`COleException`。  
  
##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos  
 設定大小、 位置和疊置順序控制項站台。  
  
```  
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>參數  
 *pWndInsertAfter*  
 視窗的指標。  
  
 *x*  
 左側視窗的新位置。  
  
 *y*  
 視窗頂端的新位置。  
  
 *cx*  
 新視窗的寬度  
  
 *cy*  
 新視窗的高度。  
  
 *nFlags*  
 指定視窗大小及定位旗標。 如需可能的值，請參閱 < 備註 > 一節[SetWindowPos](https://msdn.microsoft.com/library/windows/desktop/ms633545) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 非零值如果成功，否則為零。  
  
##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText  
 設定控制項站台的文字。  
  
```  
virtual void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>參數  
 *lpszString*  
 以 null 終止的字串來作為新的標題或控制項文字的指標。  
  
### <a name="remarks"></a>備註  
 此函式會先嘗試設定標題的內建屬性。 如果不支援標題內建屬性，改為設定文字屬性。  
  
##  <a name="showwindow"></a>  COleControlSite::ShowWindow  
 設定視窗的顯示狀態。  
  
```  
virtual BOOL ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>參數  
 *nCmdShow*  
 指定要顯示的控制項站台的方式。 它必須是下列值之一：  
  
- SW_HIDE 會隱藏此視窗，並將啟用傳遞至另一個視窗。  
  
- SW_MINIMIZE 視窗最小化，並啟動系統的清單中的最上層視窗。  
  
- SW_RESTORE 啟動並顯示視窗。 如果視窗是最小化或最大化，則 Windows 會將它還原至其原始大小和位置。  
  
- SW_SHOW 啟動視窗並將它顯示在其目前的大小和位置。  
  
- Sw_showmaximized 其中一個啟動的視窗，並顯示最大化視窗。  
  
- SW_SHOWMINIMIZED 啟動視窗並將它顯示為圖示。  
  
- SW_SHOWMINNOACTIVE 以圖示顯示視窗。 目前使用中視窗保持作用中。  
  
- SW_SHOWNA 顯示視窗在其目前的狀態。 目前使用中視窗保持作用中。  
  
- SW_SHOWNOACTIVATE 顯示視窗中的最新的大小和位置。 目前使用中視窗保持作用中。  
  
- SW_SHOWNORMAL 啟動並顯示視窗。 如果視窗是最小化或最大化，則 Windows 會將它還原至其原始大小和位置。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果視窗是先前可見的。0，表示之前隱藏的視窗。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
