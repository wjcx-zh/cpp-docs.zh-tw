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
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816344"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 類別

MFC 程式庫訊息對應架構的基類。

## <a name="syntax"></a>語法

```
class CCmdTarget : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCmdTarget：： CCmdTarget](#ccmdtarget)|建構 `CCmdTarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCmdTarget：： BeginWaitCursor](#beginwaitcursor)|將游標顯示為沙漏游標。|
|[CCmdTarget：:D oOleVerb](#dooleverb)|造成執行 OLE 動詞指定的動作。|
|[CCmdTarget：： EnableAutomation](#enableautomation)|允許 `CCmdTarget` 物件的 OLE automation。|
|[CCmdTarget：： EnableConnections](#enableconnections)|啟用透過連接點引發事件的功能。|
|[CCmdTarget：： EnableTypeLib](#enabletypelib)|啟用物件的類型程式庫。|
|[CCmdTarget：： EndWaitCursor](#endwaitcursor)|回到上一個資料指標。|
|[CCmdTarget：： EnumOleVerbs](#enumoleverbs)|列舉物件的 OLE 動詞。|
|[CCmdTarget：： FromIDispatch](#fromidispatch)|傳回與 `IDispatch` 指標相關聯之 `CCmdTarget` 物件的指標。|
|[CCmdTarget：： GetDispatchIID](#getdispatchiid)|取得主要分派介面識別碼。|
|[CCmdTarget：： GetIDispatch](#getidispatch)|傳回與 `CCmdTarget` 物件相關聯之 `IDispatch` 物件的指標。|
|[CCmdTarget：： GetTypeInfoCount](#gettypeinfocount)|抓取物件提供的類型資訊介面數目。|
|[CCmdTarget：： GetTypeInfoOfGuid](#gettypeinfoofguid)|抓取對應于指定之 GUID 的類型描述。|
|[CCmdTarget：： GetTypeLib](#gettypelib)|取得類型程式庫的指標。|
|[CCmdTarget：： GetTypeLibCache](#gettypelibcache)|取得類型程式庫快取。|
|[CCmdTarget：： IsInvokeAllowed](#isinvokeallowed)|啟用自動化方法調用。|
|[CCmdTarget：： IsResultExpected](#isresultexpected)|如果 automation 函數應該傳回值，則傳回非零。|
|[CCmdTarget：： OnCmdMsg](#oncmdmsg)|路由及分派命令訊息。|
|[CCmdTarget：： OnFinalRelease](#onfinalrelease)|在最後一個 OLE 參考發行之後清除。|
|[CCmdTarget：： RestoreWaitCursor](#restorewaitcursor)|還原沙漏游標。|

## <a name="remarks"></a>備註

訊息對應會將命令或訊息路由傳送至您撰寫來處理它們的成員函式。 （命令是來自功能表項目、命令按鈕或快速鍵的訊息）。

衍生自 `CCmdTarget` 的主要架構類別包括[CView](../../mfc/reference/cview-class.md)、 [CWinApp](../../mfc/reference/cwinapp-class.md)、 [CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)和[CFrameWnd](../../mfc/reference/cframewnd-class.md)。 如果您想要新的類別來處理訊息，請從這些 `CCmdTarget`衍生類別的其中一個來衍生類別。 您很少會直接從 `CCmdTarget` 衍生類別。

如需命令目標和 `OnCmdMsg` 路由的總覽，請參閱[命令目標](../../mfc/command-targets.md)、[命令路由](../../mfc/command-routing.md)和[對應訊息](../../mfc/mapping-messages.md)。

`CCmdTarget` 包含處理沙漏游標顯示的成員函式。 當您預期命令會花很明顯的時間間隔來執行時，請顯示沙漏游標。

分派對應（類似于訊息對應）是用來公開 OLE automation `IDispatch` 功能。 藉由公開此介面，其他應用程式（例如 Visual Basic）就可以呼叫您的應用程式。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="beginwaitcursor"></a>CCmdTarget：： BeginWaitCursor

呼叫此函式可在您預期命令採取明顯的時間間隔執行時，將游標顯示為沙漏。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>備註

架構會呼叫這個函式來顯示其忙碌中的使用者，例如當 `CDocument` 物件將本身載入或儲存至檔案時。

`BeginWaitCursor` 的動作不一定會在單一訊息處理常式之外生效，因為其他動作（例如 `OnSetCursor` 處理）可能會變更資料指標。

呼叫 `EndWaitCursor` 以還原先前的資料指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget：： CCmdTarget

建構 `CCmdTarget` 物件。

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget：:D oOleVerb

造成執行 OLE 動詞指定的動作。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
動詞命令的數值識別碼。

*lpMsg*<br/>
訊息結構的指標，描述叫用動詞[命令的事件](/windows/win32/api/winuser/ns-winuser-msg)（例如按兩下）。

*hWndParent*<br/>
文件視窗的控制代碼，包含物件。

*lpRect*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標，其中包含在*hwndParent*中定義物件周框的座標（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

此成員函式基本上是 IOleObject 的實作為[：:D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)。 可能的動作是由[CCmdTarget：： EnumOleVerbs](#enumoleverbs)所列舉。

##  <a name="enableautomation"></a>CCmdTarget：： EnableAutomation

呼叫此函式可啟用物件的 OLE automation。

```
void EnableAutomation();
```

### <a name="remarks"></a>備註

此函式通常是從您物件的函式呼叫，而且只有在已針對類別宣告分派對應時，才會呼叫這個函式。 如需有關自動化的詳細資訊，請參閱[Automation 用戶端](../../mfc/automation-clients.md)和[automation 伺服器](../../mfc/automation-servers.md)文章。

##  <a name="enableconnections"></a>CCmdTarget：： EnableConnections

啟用透過連接點引發事件的功能。

```
void EnableConnections();
```

### <a name="remarks"></a>備註

若要啟用連接點，請在衍生類別的函式中呼叫這個成員函式。

##  <a name="enabletypelib"></a>CCmdTarget：： EnableTypeLib

啟用物件的類型程式庫。

```
void EnableTypeLib();
```

### <a name="remarks"></a>備註

如果提供型別資訊，請在 `CCmdTarget`衍生物件的函式中呼叫這個成員函式。

##  <a name="endwaitcursor"></a>CCmdTarget：： EndWaitCursor

在您呼叫 `BeginWaitCursor` 成員函式從沙漏游標回到上一個資料指標之後，請呼叫這個函式。

```
void EndWaitCursor();
```

### <a name="remarks"></a>備註

架構也會呼叫這個成員函式，但它也稱為沙漏游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget：： EnumOleVerbs

列舉物件的 OLE 動詞。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>參數

*ppenumOleVerb*<br/>
指向[IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)介面指標的指標。

### <a name="return-value"></a>傳回值

如果物件至少支援一個 OLE 動詞命令，則為 TRUE （在此情況下，\* *ppenumOleVerb*會指向 `IEnumOLEVERB` 列舉值介面），否則為 FALSE。

### <a name="remarks"></a>備註

此成員函式基本上是[IOleObject：： EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)的執行。

##  <a name="fromidispatch"></a>CCmdTarget：： FromIDispatch

呼叫此函式可將從類別的 automation 成員函式接收的 `IDispatch` 指標對應到實作用 `IDispatch` 物件介面的 `CCmdTarget` 物件。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
`IDispatch` 物件的指標。

### <a name="return-value"></a>傳回值

與*lpDispatch*相關聯之 `CCmdTarget` 物件的指標。 如果 `IDispatch` 物件無法被辨識為 Microsoft Foundation Class `IDispatch` 物件，此函式會傳回 Null。

### <a name="remarks"></a>備註

此函式的結果是對成員函式的呼叫 `GetIDispatch`的反向。

##  <a name="getdispatchiid"></a>CCmdTarget：： GetDispatchIID

取得主要分派介面識別碼。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>參數

*pIID*<br/>
介面識別碼（ [GUID](/previous-versions/cc317743(v%3dmsdn.10))）的指標。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。 如果成功，\* *pIID*會設定為主要分派介面識別碼。

### <a name="remarks"></a>備註

衍生類別應該覆寫這個成員函式（如果未覆寫，`GetDispatchIID` 會傳回 FALSE）。 請參閱[COleControl](../../mfc/reference/colecontrol-class.md)。

##  <a name="getidispatch"></a>CCmdTarget：： GetIDispatch

呼叫這個成員函式，從傳回 `IDispatch` 指標或以傳址方式接受 `IDispatch` 指標的自動化方法，抓取 `IDispatch` 的指標。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>參數

*bAddRef*<br/>
指定是否要遞增物件的參考計數。

### <a name="return-value"></a>傳回值

與物件相關聯的 `IDispatch` 指標。

### <a name="remarks"></a>備註

對於在其函式中呼叫 `EnableAutomation` 的物件，使其自動化啟用時，此函式會傳回 `IDispatch` 的基礎類別實作用指標，而用戶端會使用此介面透過 `IDispatch` 介面進行通訊。 呼叫此函式會自動將參考加入至指標，因此不需要呼叫[IUnknown：： AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)。

##  <a name="gettypeinfocount"></a>CCmdTarget：： GetTypeInfoCount

抓取物件提供的類型資訊介面數目。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>傳回值

類型資訊介面的數目。

### <a name="remarks"></a>備註

這個成員函式基本上會實作為[IDispatch：： GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

衍生類別應該覆寫此函式，以傳回所提供的類型資訊介面數目（0或1）。 如果未覆寫，`GetTypeInfoCount` 會傳回0。 若要覆寫，請使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，這也會實行 `GetTypeLib` 和 `GetTypeLibCache`。

##  <a name="gettypeinfoofguid"></a>CCmdTarget：： GetTypeInfoOfGuid

抓取對應于指定之 GUID 的類型描述。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>參數

*lcid*<br/>
地區設定識別碼（`LCID`）。

*guid*<br/>
型別描述的[GUID](/previous-versions/cc317743(v%3dmsdn.10)) 。

*ppTypeInfo*<br/>
指向 `ITypeInfo` 介面之指標的指標。

### <a name="return-value"></a>傳回值

表示呼叫成功或失敗的 HRESULT。 如果成功，\* *ppTypeInfo*會指向類型資訊介面。

##  <a name="gettypelib"></a>CCmdTarget：： GetTypeLib

取得類型程式庫的指標。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>參數

*lcid*<br/>
地區設定識別項 (LCID)。

*ppTypeLib*<br/>
指向 `ITypeLib` 介面指標的指標。

### <a name="return-value"></a>傳回值

表示呼叫成功或失敗的 HRESULT。 如果成功，\* *ppTypeLib*會指向類型程式庫介面。

### <a name="remarks"></a>備註

衍生類別應該覆寫這個成員函式（如果未覆寫，`GetTypeLib` 會傳回 TYPE_E_CANTLOADLIBRARY）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，這也會實行 `GetTypeInfoCount` 和 `GetTypeLibCache`。

##  <a name="gettypelibcache"></a>CCmdTarget：： GetTypeLibCache

取得類型程式庫快取。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>傳回值

`CTypeLibCache` 物件的指標。

### <a name="remarks"></a>備註

衍生類別應該覆寫這個成員函式（如果未覆寫，`GetTypeLibCache` 會傳回 Null）。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏，這也會實行 `GetTypeInfoCount` 和 `GetTypeLib`。

##  <a name="isinvokeallowed"></a>CCmdTarget：： IsInvokeAllowed

MFC 的 `IDispatch::Invoke` 的執行會呼叫這個函式，以判斷是否可以叫用指定的 automation 方法（由*dispid*識別）。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>參數

*dispid*<br/>
分派識別碼。

### <a name="return-value"></a>傳回值

如果可以叫用方法，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

如果 `IsInvokeAllowed` 傳回 TRUE，`Invoke` 會繼續呼叫方法;否則，`Invoke` 將會失敗，並傳回 E_UNEXPECTED。

衍生類別可以覆寫這個函式，以傳回適當的值（如果未覆寫，`IsInvokeAllowed` 會傳回 TRUE）。 請參閱特定[COleControl：： IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)。

##  <a name="isresultexpected"></a>CCmdTarget：： IsResultExpected

使用 `IsResultExpected`，以確定用戶端是否預期會從其對 automation 函數的呼叫傳回值。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>傳回值

如果 automation 函數應該傳回值，則為非零。否則為0。

### <a name="remarks"></a>備註

OLE 介面會提供資訊給 MFC，指出用戶端是否使用或忽略函式呼叫的結果，而 MFC 則會使用這項資訊來判斷 `IsResultExpected`呼叫的結果。 如果傳回值的生產環境是需要大量時間或資源，您可以在計算傳回值之前呼叫此函式，以提高效率。

此函式只會傳回0次，因此，如果您從用戶端呼叫的 automation 函式呼叫它們，則會從其他自動化函式取得有效的傳回值。

如果未進行 automation 函數呼叫，`IsResultExpected` 會傳回非零值。

##  <a name="oncmdmsg"></a>CCmdTarget：： OnCmdMsg

由架構呼叫以路由傳送和分派命令訊息，以及處理命令使用者介面物件的更新。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含命令 ID。

*nCode*<br/>
識別命令通知碼。 如需*nCode*值的詳細資訊，請參閱**備註**。

*pExtra*<br/>
根據*nCode*的值使用。 如需*pExtra*的詳細資訊，請參閱**備註**。

*pHandlerInfo*<br/>
如果不是 Null，`OnCmdMsg` 會填入*pHandlerInfo*結構的*pTarget*和*pmf*成員，而不是分派命令。 通常，這個參數應該是 Null。

### <a name="return-value"></a>傳回值

如果已處理訊息，則為非零值。否則為0。

### <a name="remarks"></a>備註

這是架構命令架構的主要執行常式。

在執行時間，`OnCmdMsg` 會將命令分派給其他物件，或藉由呼叫根類別 `CCmdTarget::OnCmdMsg`（其會執行實際的訊息對應查閱）來處理命令本身。 如需預設命令路由的完整描述，請參閱[訊息處理和對應主題](../../mfc/message-handling-and-mapping.md)。

在罕見的情況下，您可能會想要覆寫此成員函式，以擴充架構的標準命令路由。 如需命令路由架構的先進詳細資料，請參閱[技術提示 21](../../mfc/tn021-command-and-message-routing.md) 。

如果您覆寫 `OnCmdMsg`，則必須為*nCode*、命令通知碼和*pExtra*提供適當的值，這取決於*nCode*的值。 下表列出其對應的值：

|*nCode*值|*pExtra*值|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>CCmdTarget：： OnFinalRelease

當物件的最後一個 OLE 參考被釋放時，由架構呼叫。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>備註

覆寫此函式，以提供這種情況的特殊處理。 預設的執行會刪除物件。

##  <a name="restorewaitcursor"></a>CCmdTarget：： RestoreWaitCursor

呼叫此函式可在系統資料指標變更之後，還原適當的沙漏游標（例如，在訊息方塊開啟後關閉，然後在長時間的作業中關閉）。

```
void RestoreWaitCursor();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 ACDUAL:](../../overview/visual-cpp-samples.md)<br/>
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
