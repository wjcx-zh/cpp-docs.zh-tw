---
title: CCmdTarget 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: 4e93f167b9cb28a83c42220fa58b17d5c4845a75
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894285"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 類別

Microsoft Foundation 類別庫訊息對應架構的基底類別。

## <a name="syntax"></a>語法

```
class CCmdTarget : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|建構 `CCmdTarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|顯示為沙漏游標的游標。|
|[CCmdTarget::DoOleVerb](#dooleverb)|會導致執行 OLE 動詞命令所指定的動作。|
|[CCmdTarget::EnableAutomation](#enableautomation)|可讓 OLE 自動化`CCmdTarget`物件。|
|[CCmdTarget::EnableConnections](#enableconnections)|透過連接點，可讓事件引發。|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|可讓物件的型別程式庫。|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|若要返回先前的資料指標。|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|列舉物件的 OLE 動詞命令。|
|[CCmdTarget::FromIDispatch](#fromidispatch)|將指標傳回至`CCmdTarget`相關聯的物件`IDispatch`指標。|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|取得主要分派介面 id。|
|[CCmdTarget::GetIDispatch](#getidispatch)|將指標傳回至`IDispatch`相關聯的物件`CCmdTarget`物件。|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|擷取物件提供的型別資訊介面數目。|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|擷取對應至指定之 GUID 的型別描述。|
|[CCmdTarget::GetTypeLib](#gettypelib)|型別程式庫取得的指標。|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|取得類型程式庫快取。|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|可讓自動化方法引動過程。|
|[CCmdTarget::IsResultExpected](#isresultexpected)|傳回非零值，如果 automation 函式應傳回的值。|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|路由和分派命令訊息。|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|清除之後釋放最後一個 OLE 參考。|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|還原沙漏游標。|

## <a name="remarks"></a>備註

訊息對應會將命令或訊息路由至您撰寫來處理它們的成員函式。 （命令是從功能表項目、 命令按鈕或加速鍵訊息）。

金鑰架構類別衍生自`CCmdTarget`包括[CView](../../mfc/reference/cview-class.md)， [CWinApp](../../mfc/reference/cwinapp-class.md)， [CDocument](../../mfc/reference/cdocument-class.md)， [CWnd](../../mfc/reference/cwnd-class.md)，以及[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果您想讓新類別來處理訊息時，衍生類別的其中一種`CCmdTarget`-衍生的類別。 您很少會衍生的類別`CCmdTarget`直接。

如需命令目標的概觀並`OnCmdMsg`路由，請參閱[命令目標](../../mfc/command-targets.md)，[命令路由](../../mfc/command-routing.md)，和[訊息對應](../../mfc/mapping-messages.md)。

`CCmdTarget` 包含處理的沙漏游標顯示的成員函式。 當您預期才會明顯的時間間隔來執行命令時，請顯示沙漏游標。

分派對應，類似於訊息對應，可用於公開 OLE automation`IDispatch`功能。 藉由公開這個介面，您的應用程式可以呼叫其他應用程式 （例如 Visual Basic)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor

呼叫此函式可顯示為沙漏游標，預期才會明顯的時間間隔執行的命令。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>備註

架構會呼叫此函式可向使用者顯示為忙碌中，例如當`CDocument`物件載入，或將本身儲存至檔案。

動作`BeginWaitCursor`並不一定有效以外的單一訊息處理常式做為其他動作，例如`OnSetCursor`處理，可能會變更資料指標。

呼叫`EndWaitCursor`還原先前的資料指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget

建構 `CCmdTarget` 物件。

```
CCmdTarget();
```

##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb

會導致執行 OLE 動詞命令所指定的動作。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
動詞命令的數值識別項。

*lpMsg*<br/>
指標[MSG](/windows/desktop/api/winuser/ns-winuser-msg)結構描述 （例如按兩下） 叫用動詞命令的事件。

*hWndParent*<br/>
文件視窗的控制代碼，包含物件。

*lpRect*<br/>
指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含的座標，像素為單位，可定義物件的週框矩形*hwndParent*。

### <a name="return-value"></a>傳回值

如果成功，否則為 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

此成員函式基本上會實作[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb)。 藉由可列舉的可能動作[CCmdTarget::EnumOleVerbs](#enumoleverbs)。

##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation

呼叫此函式可啟用 OLE automation 物件。

```
void EnableAutomation();
```

### <a name="remarks"></a>備註

此函式通常會從物件的建構函式呼叫，而且應該只在分派對應已被宣告為類別才呼叫。 如需自動化的詳細資訊，請參閱文章[Automation 用戶端](../../mfc/automation-clients.md)並[Automation 伺服程式](../../mfc/automation-servers.md)。

##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections

透過連接點，可讓事件引發。

```
void EnableConnections();
```

### <a name="remarks"></a>備註

若要啟用的連接點，請在衍生類別的建構函式呼叫此成員函式。

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

可讓物件的型別程式庫。

```
void EnableTypeLib();
```

### <a name="remarks"></a>備註

建構函式中呼叫此成員函式程式`CCmdTarget`-衍生物件，如果它會提供類型資訊。

##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor

呼叫此函式之後呼叫了`BeginWaitCursor`以沙漏游標返回先前的資料指標的成員函式。

```
void EndWaitCursor();
```

### <a name="remarks"></a>備註

架構也會呼叫此成員函式之後就叫做沙漏游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs

列舉物件的 OLE 動詞命令。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>參數

*ppenumOleVerb*<br/>
指標的指標[IEnumOLEVERB](/windows/desktop/api/oleidl/nn-oleidl-ienumoleverb)介面。

### <a name="return-value"></a>傳回值

如果物件支援至少一個 OLE 指令動詞則為 TRUE (在此情況下\* *ppenumOleVerb*指向`IEnumOLEVERB`列舉值介面)，否則為 FALSE。

### <a name="remarks"></a>備註

此成員函式基本上會實作[Enumverbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs)。

##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch

呼叫此函式來對應`IDispatch`指標，從 automation 類別中，成員函式會接收到`CCmdTarget`可實作介面的物件`IDispatch`物件。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
`IDispatch` 物件的指標。

### <a name="return-value"></a>傳回值

指標`CCmdTarget`相關聯的物件*lpDispatch*。 此函式會傳回 NULL，如果`IDispatch`物件無法辨識為 Microsoft Foundation Class`IDispatch`物件。

### <a name="remarks"></a>備註

此函式的結果是成員函式呼叫的反向`GetIDispatch`。

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

取得主要分派介面 id。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>參數

*pIID*<br/>
介面識別碼的指標 ( [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931))。

### <a name="return-value"></a>傳回值

如果成功，否則為 FALSE，則為 TRUE。 如果成功， \* *pIID*設為主要分派介面 id。

### <a name="remarks"></a>備註

在衍生的類別應該覆寫此成員函式 (如果未覆寫，`GetDispatchIID`會傳回 FALSE)。 請參閱[COleControl](../../mfc/reference/colecontrol-class.md)。

##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch

呼叫此成員函式，來擷取`IDispatch`指標從自動化方法來傳回`IDispatch`指標或採用`IDispatch`所參考的指標。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>參數

*bAddRef*<br/>
指定是否要遞增參考計數物件。

### <a name="return-value"></a>傳回值

`IDispatch`與物件相關聯的指標。

### <a name="remarks"></a>備註

針對物件呼叫`EnableAutomation`其建構函式，即可啟用自動化，此函式傳回的指標的基礎類別實作`IDispatch`所用的用戶端通訊透過`IDispatch`介面。 會自動呼叫此函式將參考加入至指標，因此不需要呼叫[iunknown:: Addref](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)。

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

擷取物件提供的型別資訊介面數目。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>傳回值

型別資訊介面數目。

### <a name="remarks"></a>備註

此成員函式基本上會實作[IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

在衍生的類別應該覆寫這個函式來傳回 （0 或 1） 所提供的型別資訊介面數目。 如果未覆寫，`GetTypeInfoCount`會傳回 0。 若要覆寫，請使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeLib`和`GetTypeLibCache`。

##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid

擷取對應至指定之 GUID 的型別描述。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>參數

*lcid*<br/>
地區設定識別碼 ( `LCID`)。

*guid*<br/>
[GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)的型別描述。

*ppTypeInfo*<br/>
指標的指標`ITypeInfo`介面。

### <a name="return-value"></a>傳回值

HRESULT，指出成功或失敗的呼叫。 如果成功， \* *ppTypeInfo*指向類型資訊介面。

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

型別程式庫取得的指標。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>參數

*lcid*<br/>
地區設定識別項 (LCID)。

*ppTypeLib*<br/>
指標的指標`ITypeLib`介面。

### <a name="return-value"></a>傳回值

HRESULT，指出成功或失敗的呼叫。 如果成功， \* *ppTypeLib*指向類型程式庫介面。

### <a name="remarks"></a>備註

在衍生的類別應該覆寫此成員函式 (如果未覆寫，`GetTypeLib`傳回 TYPE_E_CANTLOADLIBRARY)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeInfoCount`和`GetTypeLibCache`。

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

取得類型程式庫快取。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>傳回值

`CTypeLibCache` 物件的指標。

### <a name="remarks"></a>備註

在衍生的類別應該覆寫此成員函式 (如果未覆寫，`GetTypeLibCache`會傳回 NULL)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)巨集，也會實作`GetTypeInfoCount`和`GetTypeLib`。

##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed

MFC 的實作會呼叫此函式`IDispatch::Invoke`以判斷指定的自動化方法 (由*dispid*) 可以叫用。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
分派識別碼。

### <a name="return-value"></a>傳回值

如果此方法可以叫用，否則為 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

如果`IsInvokeAllowed`會傳回 TRUE，`Invoke`繼續進行呼叫的方法; 否則`Invoke`將會失敗，傳回 E_UNEXPECTED。

在衍生的類別可以覆寫這個函式來傳回適當的值 (如果未覆寫， `IsInvokeAllowed` ，則傳回 TRUE)。 請參閱特別[COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。

##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected

使用`IsResultExpected`來確定用戶端是否預期來自其呼叫 automation 函式的傳回值。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>傳回值

Automation 函式應傳回值; 如果為非零否則為 0。

### <a name="remarks"></a>備註

OLE 介面提供以 MFC 用戶端是使用或忽略函式呼叫的結果相關的資訊和 MFC 會使用這項資訊判斷呼叫的結果`IsResultExpected`。 如果傳回值的實際執行時間-或-需要大量資源，您可以藉由計算傳回值之前呼叫此函式來提高效率。

一次，讓您將從其他自動化函式取得有效的傳回值，如果它們從呼叫 automation 函式，呼叫用戶端，此函數會傳回 0。

`IsResultExpected` 如果呼叫 automation 函式呼叫不在進行中時，會傳回非零值。

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

由架構呼叫以傳送和分派命令訊息，以及處理命令的使用者介面物件的更新。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含命令 id。

*nCode*<br/>
識別命令通知程式碼。 請參閱**備註**如需有關值*則 nCode*。

*pExtra*<br/>
依據值來使用*則 nCode*。 請參閱**備註**如需詳細資訊*pExtra*。

*pHandlerInfo*<br/>
如果不是 NULL，`OnCmdMsg`填寫*pTarget*並*pmf*的成員*pHandlerInfo*結構，而不是分派命令。 一般而言，這個參數應該是 NULL。

### <a name="return-value"></a>傳回值

處理訊息的; 如果為非零否則為 0。

### <a name="remarks"></a>備註

這是主要的實作常式的命令架構。

在執行階段`OnCmdMsg`分派至其他物件的命令，或藉由呼叫的根類別會處理命令本身`CCmdTarget::OnCmdMsg`，它會執行實際的訊息對應查閱。 如需完整的預設命令路由說明，請參閱 <<c0> [ 訊息處理和對應的主題](../../mfc/message-handling-and-mapping.md)。

在少數情況下，您可能想要覆寫此成員函式，來擴充架構的標準命令路由。 請參閱[技術提示 21](../../mfc/tn021-command-and-message-routing.md)的命令路由架構的進階詳細資料。

如果您覆寫`OnCmdMsg`，您必須提供適當的值*則 nCode*，命令通知程式碼，並*pExtra*，這取決於值*則 nCode*. 下表列出其對應的值：

|*nCode* value|*pExtra* value|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease

在發行至或從物件的最後一個 OLE 參考時，由架構呼叫。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>備註

此函式可提供特殊處理，這種情況下會覆寫。 預設實作會刪除物件。

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

呼叫此函式以還原適當的沙漏游標系統資料指標之後已經變更 （例如後的訊息方塊已開啟和關閉執行長時間作業時）。

```
void RestoreWaitCursor();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 ACDUAL](../../visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver 類別](../../mfc/reference/coledispatchdriver-class.md)
