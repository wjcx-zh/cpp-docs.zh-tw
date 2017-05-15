---
title: "CCmdTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
dev_langs:
- C++
helpviewer_keywords:
- message maps, CCmdTarget base class
- command targets
- CCmdTarget class
- command routing, command targets
- targets, command
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: 23
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: d58ee8e02c57c48c58f13c7e826fd01a1c0d9f57
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="ccmdtarget-class"></a>CCmdTarget 類別
Microsoft Foundation 類別庫訊息對應架構基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CCmdTarget : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CCmdTarget::CCmdTarget](#ccmdtarget)|建構 `CCmdTarget` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|顯示為沙漏游標的游標。|  
|[CCmdTarget::DoOleVerb](#dooleverb)|會用來執行 OLE 動詞命令所指定的動作。|  
|[CCmdTarget::EnableAutomation](#enableautomation)|允許的 OLE automation`CCmdTarget`物件。|  
|[CCmdTarget::EnableConnections](#enableconnections)|透過連接點，可讓事件引發。|  
|[CCmdTarget::EnableTypeLib](#enabletypelib)|可讓物件的型別程式庫。|  
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|返回上一個資料指標。|  
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|列舉物件的 OLE 動詞命令。|  
|[CCmdTarget::FromIDispatch](#fromidispatch)|將指標傳回至`CCmdTarget`物件相關聯`IDispatch`指標。|  
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|取得主要分派介面識別碼。|  
|[CCmdTarget::GetIDispatch](#getidispatch)|將指標傳回至`IDispatch`物件相關聯`CCmdTarget`物件。|  
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|擷取物件提供的類型資訊介面數目。|  
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|擷取對應於指定之 GUID 的類型描述。|  
|[CCmdTarget::GetTypeLib](#gettypelib)|取得類型程式庫的指標。|  
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|取得類型程式庫快取。|  
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|可讓 automation 方法引動過程。|  
|[CCmdTarget::IsResultExpected](#isresultexpected)|傳回非零，如果自動化函式應傳回值。|  
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|路由和分派命令訊息。|  
|[Ccmdtarget:: Onfinalrelease](#onfinalrelease)|清除後發行的最後一個 OLE 參考。|  
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|還原沙漏游標。|  
  
## <a name="remarks"></a>備註  
 訊息對應會將命令或訊息路由至您撰寫來處理這些成員函式。 （命令是從功能表項目、 命令按鈕或快速鍵的訊息）。  
  
 索引鍵的架構類別衍生自`CCmdTarget`包含[CView](../../mfc/reference/cview-class.md)， [CWinApp](../../mfc/reference/cwinapp-class.md)， [CDocument](../../mfc/reference/cdocument-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，和[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果您想將新的類別，來處理訊息，請從下列其中一種衍生類別`CCmdTarget`-衍生的類別。 您很少會衍生自`CCmdTarget`直接。  
  
 如需命令目標的概觀和`OnCmdMsg`路由，請參閱[命令目標](../../mfc/command-targets.md)，[命令路由](../../mfc/command-routing.md)，和[訊息對應](../../mfc/mapping-messages.md)。  
  
 `CCmdTarget`包含處理的沙漏游標顯示的成員函式。 當您希望產生的命令，以取得執行明顯的時間間隔顯示沙漏游標。  
  
 分派對應，類似於訊息對應，用來公開 OLE automation`IDispatch`功能。 藉由公開這個介面，您的應用程式可以呼叫其他應用程式 （例如 Visual Basic)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="beginwaitcursor"></a>CCmdTarget::BeginWaitCursor  
 呼叫此函式來顯示資料指標為以沙漏來表示，當您希望產生的命令，以取得執行明顯的時間間隔。  
  
```  
void BeginWaitCursor();
```  
  
### <a name="remarks"></a>備註  
 架構會呼叫此函式可讓使用者很忙碌中，例如當**CDocument**物件載入或儲存至檔案本身。  
  
 動作的`BeginWaitCursor`並不一定有效以外的單一訊息處理常式做為其他動作，例如`OnSetCursor`處理，可能會變更資料指標。  
  
 呼叫`EndWaitCursor`還原先前的資料指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="ccmdtarget"></a>CCmdTarget::CCmdTarget  
 建構 `CCmdTarget` 物件。  
  
```  
CCmdTarget();
```  
  
##  <a name="dooleverb"></a>CCmdTarget::DoOleVerb  
 會用來執行 OLE 動詞命令所指定的動作。  
  
```  
BOOL DoOleVerb(
    LONG iVerb,  
    LPMSG lpMsg,  
    HWND hWndParent,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `iVerb`  
 動詞命令的數值識別項。  
  
 `lpMsg`  
 指標[MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958)結構描述 （例如按兩下） 叫用動詞命令的事件。  
  
 `hWndParent`  
 文件視窗的控制代碼，包含物件。  
  
 `lpRect`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含的座標，以像素，定義物件之週框中*hwndParent*。  
  
### <a name="return-value"></a>傳回值  
 如果成功，否則為 FALSE，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 此成員函式基本上是實作[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)。 列舉的可能動作的[CCmdTarget::EnumOleVerbs](#enumoleverbs)。  
  
##  <a name="enableautomation"></a>CCmdTarget::EnableAutomation  
 呼叫此函式可啟用 OLE automation 物件。  
  
```  
void EnableAutomation();
```  
  
### <a name="remarks"></a>備註  
 此函數通常會從物件的建構函式呼叫，並應該只呼叫分派對應已宣告為類別。 如需自動化的詳細資訊，請參閱文章[Automation 用戶端](../../mfc/automation-clients.md)和[automation 伺服程式](../../mfc/automation-servers.md)。  
  
##  <a name="enableconnections"></a>CCmdTarget::EnableConnections  
 透過連接點，可讓事件引發。  
  
```  
void EnableConnections();
```  
  
### <a name="remarks"></a>備註  
 若要啟用的連接點，請在衍生類別的建構函式中呼叫此成員函式。  
  
##  <a name="enabletypelib"></a>CCmdTarget::EnableTypeLib  
 可讓物件的型別程式庫。  
  
```  
void EnableTypeLib();
```  
  
### <a name="remarks"></a>備註  
 此成員函式呼叫的建構函式中您`CCmdTarget`-衍生物件提供類型資訊。 如需詳細資訊，請參閱知識庫文章 Q185720，"如何︰ 從 MFC Automation 伺服程式提供型別資訊。 」 知識庫文件位於[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="endwaitcursor"></a>CCmdTarget::EndWaitCursor  
 已呼叫之後呼叫此函式`BeginWaitCursor`以沙漏游標返回先前的資料指標的成員函式。  
  
```  
void EndWaitCursor();
```  
  
### <a name="remarks"></a>備註  
 架構也會呼叫此成員函式之後又稱為沙漏游標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
##  <a name="enumoleverbs"></a>CCmdTarget::EnumOleVerbs  
 列舉物件的 OLE 動詞命令。  
  
```  
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```  
  
### <a name="parameters"></a>參數  
 `ppenumOleVerb`  
 指標的指標[IEnumOLEVERB](http://msdn.microsoft.com/library/windows/desktop/ms695084)介面。  
  
### <a name="return-value"></a>傳回值  
 如果物件支援至少一個 OLE 指令動詞則為 TRUE (在此情況下\*`ppenumOleVerb`指向**IEnumOLEVERB**列舉程式介面)，否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 此成員函式基本上是實作[IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781)。  
  
##  <a name="fromidispatch"></a>CCmdTarget::FromIDispatch  
 呼叫此函式對應`IDispatch`指標，從自動化成員函式的類別，會接收到`CCmdTarget`可實作介面的物件，`IDispatch`物件。  
  
```  
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```  
  
### <a name="parameters"></a>參數  
 `lpDispatch`  
 `IDispatch` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 指標`CCmdTarget`物件相關聯`lpDispatch`。 此函數會傳回**NULL**如果`IDispatch`物件無法辨識為 Microsoft Foundation Class`IDispatch`物件。  
  
### <a name="remarks"></a>備註  
 此函式的結果是成員函式呼叫的反向`GetIDispatch`。  
  
##  <a name="getdispatchiid"></a>CCmdTarget::GetDispatchIID  
 取得主要分派介面識別碼。  
  
```  
virtual BOOL GetDispatchIID(IID* pIID);
```  
  
### <a name="parameters"></a>參數  
 *pIID*  
 介面 ID 的指標 ( [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931))。  
  
### <a name="return-value"></a>傳回值  
 如果成功，否則為 FALSE，則為 TRUE。 如果成功的話， \* *pIID*設為主要分派介面識別碼。  
  
### <a name="remarks"></a>備註  
 在衍生的類別應該覆寫此成員函式 (如果未覆寫，`GetDispatchIID`會傳回 FALSE)。 請參閱[COleControl](../../mfc/reference/colecontrol-class.md)。  
  
 如需詳細資訊，請參閱知識庫文章 Q185720，"如何︰ 從 MFC Automation 伺服程式提供型別資訊。 」 知識庫文件位於[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="getidispatch"></a>CCmdTarget::GetIDispatch  
 呼叫此成員函式可擷取`IDispatch`指標從 automation 方法來傳回`IDispatch`指標或採用`IDispatch`指標所參考。  
  
```  
LPDISPATCH GetIDispatch(BOOL bAddRef);
```  
  
### <a name="parameters"></a>參數  
 *bAddRef*  
 指定是否要遞增之物件的參考計數。  
  
### <a name="return-value"></a>傳回值  
 `IDispatch`與物件相關聯的指標。  
  
### <a name="remarks"></a>備註  
 針對物件呼叫`EnableAutomation`在其建構函式，使其自動化啟用，此函式傳回的指標的基礎類別實作`IDispatch`，會由用戶端通訊透過`IDispatch`介面。 呼叫此函式會自動將參考加入至指標，因此並不需要呼叫[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)。  
  
##  <a name="gettypeinfocount"></a>CCmdTarget::GetTypeInfoCount  
 擷取物件提供的類型資訊介面數目。  
  
```  
virtual UINT GetTypeInfoCount();
```  
  
### <a name="return-value"></a>傳回值  
 類型資訊介面數目。  
  
### <a name="remarks"></a>備註  
 此成員函式基本上會實作[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)。  
  
 在衍生的類別應該覆寫此函數來傳回所提供的 （0 或 1） 的類型資訊介面數目。 如果未覆寫， **GetTypeInfoCount**傳回 0。 若要覆寫，請使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeLib`和`GetTypeLibCache`。  
  
##  <a name="gettypeinfoofguid"></a>CCmdTarget::GetTypeInfoOfGuid  
 擷取對應於指定之 GUID 的類型描述。  
  
```  
HRESULT GetTypeInfoOfGuid(
    LCID lcid,  
    const GUID& guid,  
    LPTYPEINFO* ppTypeInfo);
```  
  
### <a name="parameters"></a>參數  
 `lcid`  
 地區設定識別碼 ( `LCID`)。  
  
 `guid`  
 [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931)的類型描述。  
  
 `ppTypeInfo`  
 指標的指標`ITypeInfo`介面。  
  
### <a name="return-value"></a>傳回值  
 HRESULT，指出成功或失敗的呼叫。 如果成功的話，*`ppTypeInfo`指向類型資訊介面。  
  
##  <a name="gettypelib"></a>CCmdTarget::GetTypeLib  
 取得類型程式庫的指標。  
  
```  
virtual HRESULT GetTypeLib(
    LCID lcid,  
    LPTYPELIB* ppTypeLib);
```  
  
### <a name="parameters"></a>參數  
 `lcid`  
 地區設定識別碼 ( `LCID`)。  
  
 `ppTypeLib`  
 指標的指標`ITypeLib`介面。  
  
### <a name="return-value"></a>傳回值  
 HRESULT，指出成功或失敗的呼叫。 如果成功的話，*`ppTypeLib`指向類型程式庫的介面。  
  
### <a name="remarks"></a>備註  
 在衍生的類別應該覆寫此成員函式 (如果未覆寫，`GetTypeLib`傳回 TYPE_E_CANTLOADLIBRARY)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeInfoCount`和`GetTypeLibCache`。  
  
##  <a name="gettypelibcache"></a>CCmdTarget::GetTypeLibCache  
 取得類型程式庫快取。  
  
```  
virtual CTypeLibCache* GetTypeLibCache();
```  
  
### <a name="return-value"></a>傳回值  
 指標**CTypeLibCache**物件。  
  
### <a name="remarks"></a>備註  
 在衍生的類別應該覆寫此成員函式 (如果未覆寫， **GetTypeLibCache**傳回 NULL)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeInfoCount`和`GetTypeLib`。  
  
##  <a name="isinvokeallowed"></a>CCmdTarget::IsInvokeAllowed  
 MFC 的實作會呼叫此函式**idispatch:: Invoke**判斷給定的自動化方法 (由`dispid`) 可以叫用。  
  
```  
virtual BOOL IsInvokeAllowed(DISPID dispid);
```  
  
### <a name="parameters"></a>參數  
 `dispid`  
 分派識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果此方法可以叫用，否則為 FALSE，則為 TRUE。  
  
### <a name="remarks"></a>備註  
 如果`IsInvokeAllowed`會傳回 TRUE， **Invoke**繼續進行呼叫的方法; 否則`Invoke`將會失敗，並傳回 E_UNEXPECTED。  
  
 在衍生的類別可以覆寫此函數來傳回適當的值 (如果未覆寫， `IsInvokeAllowed` ，則傳回 TRUE)。 請特別參閱[COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。  
  
##  <a name="isresultexpected"></a>CCmdTarget::IsResultExpected  
 使用`IsResultExpected`來確定用戶端是否預期來自其呼叫 automation 函式的傳回值。  
  
```  
BOOL IsResultExpected();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果自動化函式應傳回值。否則便是 0。  
  
### <a name="remarks"></a>備註  
 OLE 介面會提供有關用戶端會使用或忽略函式呼叫的結果是否 MFC 資訊和 MFC 接著會使用此資訊來判斷要呼叫的結果`IsResultExpected`。 如果傳回值的實際執行時間-或-需要大量資源，您可以增加效率計算傳回的值之前呼叫這個函式。  
  
 只有在用戶端，讓您取得有效的傳回值與其他自動化函式在呼叫 automation 函式，如果已呼叫後，此函數會傳回 0。  
  
 `IsResultExpected`如果呼叫 automation 函式呼叫不在進行中時，傳回非零值。  
  
##  <a name="oncmdmsg"></a>CCmdTarget::OnCmdMsg  
 由架構呼叫以傳送和分派命令訊息，並處理命令的使用者介面物件的更新。  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 包含命令識別碼。  
  
 `nCode`  
 識別命令通知程式碼。 請參閱**備註**如需有關值`nCode`。  
  
 `pExtra`  
 依據的值來使用`nCode`。 請參閱**備註**如需有關`pExtra`。  
  
 `pHandlerInfo`  
 如果沒有**NULL**，`OnCmdMsg`填入**pTarget**和**pmf**成員`pHandlerInfo`結構，而不是分派命令。 此參數通常應該**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果處理訊息; 的非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 這是主要實作的常式架構命令架構。  
  
 在執行階段，`OnCmdMsg`會分派至其他物件的命令，或藉由呼叫根類別中處理命令本身`CCmdTarget::OnCmdMsg`，也沒有實際的訊息對應查閱。 如需完整的預設命令路由說明，請參閱[訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。  
  
 在少數情況下，您可能想要覆寫此成員函式，來延伸架構的標準命令路由。 請參閱[技術提示 21](../../mfc/tn021-command-and-message-routing.md)的命令路由架構的進階詳細資料。  
  
 如果您覆寫`OnCmdMsg`，您必須提供適當的值給`nCode`，命令通知程式碼和`pExtra`，而定的值`nCode`。 下表列出其對應的值︰  
  
|`nCode` 值|`pExtra` 值|  
|-------------------|--------------------|  
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)*|  
|CN_EVENT|AFX_EVENT *|  
|CN_UPDATE_COMMAND_UI|CCmdUI *|  
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)*|  
|CN_OLE_UNREGISTER|NULL|  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]  
  
##  <a name="onfinalrelease"></a>Ccmdtarget:: Onfinalrelease  
 發行或從物件的最後一個 OLE 參考時，由架構呼叫。  
  
```  
virtual void OnFinalRelease();
```  
  
### <a name="remarks"></a>備註  
 此函式可提供特殊處理，這種情況下會覆寫。 預設實作會刪除物件。  
  
##  <a name="restorewaitcursor"></a>CCmdTarget::RestoreWaitCursor  
 呼叫此函式以還原適當的沙漏游標系統游標後已變更 （例如之後的訊息方塊已開啟和關閉執行長時間作業時）。  
  
```  
void RestoreWaitCursor();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 ACDUAL](../../visual-cpp-samples.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp 類別](../../mfc/reference/cwinapp-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)   
 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver 類別](../../mfc/reference/coledispatchdriver-class.md)

