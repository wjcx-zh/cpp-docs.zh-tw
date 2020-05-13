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
ms.openlocfilehash: 1ef7040f3be1e4c30a6dc19e6093727299c9f1c3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752721"
---
# <a name="ccmdtarget-class"></a>CCmdTarget 類別

微軟基礎類庫消息映射體系結構的基類。

## <a name="syntax"></a>語法

```
class CCmdTarget : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CmD目標::CMD目標](#ccmdtarget)|建構 `CCmdTarget` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMD目標::開始等待游標](#beginwaitcursor)|將游標顯示為沙漏游標。|
|[CmdTarget::DoOleVerb](#dooleverb)|導致執行由 OLE 謂詞指定的操作。|
|[CmD目標::啟用自動化](#enableautomation)|允許`CCmdTarget`物件進行 OLE 自動化。|
|[CmD 目標:開啟連線](#enableconnections)|啟用在連接點上觸發事件。|
|[CmD 目標::啟用類型Lib](#enabletypelib)|啟用物件的類型庫。|
|[CmD目標::結束等待游標](#endwaitcursor)|返回到上一個游標。|
|[Cmd目標::枚舉](#enumoleverbs)|枚舉物件的 OLE 謂詞。|
|[Cmd目標::從I調度](#fromidispatch)|返回指向與`IDispatch`指標關聯的`CCmdTarget`物件的指標。|
|[CmD目標::取得調度IID](#getdispatchiid)|獲取主調度介面 ID。|
|[CmD目標::取得I調度](#getidispatch)|返回指向與`IDispatch``CCmdTarget`對象關聯的物件的指標。|
|[CmD目標::取得類型資訊計數](#gettypeinfocount)|檢索物件提供的類型資訊介面的數量。|
|[Cmd目標::取得資訊](#gettypeinfoofguid)|擷取對應到所指定 GUID 的型別描述。|
|[CmD目標::取得類型Lib](#gettypelib)|獲取指向類型庫的指標。|
|[CmD目標::取得類型LibCache](#gettypelibcache)|獲取類型庫緩存。|
|[Cmd目標::已呼叫](#isinvokeallowed)|啟用自動化方法調用。|
|[Cmd目標::預期結果](#isresultexpected)|如果自動化函數應返回值,則返回非零。|
|[CmD目標::OnCmdMsg](#oncmdmsg)|路由和調度命令消息。|
|[Cmd目標::最終發佈](#onfinalrelease)|釋放最後一個 OLE 參考後進行清理。|
|[Cmd目標::恢復等待游標](#restorewaitcursor)|恢復沙漏游標。|

## <a name="remarks"></a>備註

消息對應將命令或消息路由到您編寫處理這些命令或消息的成員函數。 (命令是來自功能表項、命令按鈕或快捷鍵的消息。

`CCmdTarget`來自的關鍵框架類包括CView、CWinApp、CDocument、CWnd和[CFrameWnd。](../../mfc/reference/cframewnd-class.md) [CView](../../mfc/reference/cview-class.md) [CWinApp](../../mfc/reference/cwinapp-class.md) [CDocument](../../mfc/reference/cdocument-class.md) [CWnd](../../mfc/reference/cwnd-class.md) 如果希望新類處理消息,則從這些`CCmdTarget`派生類之一派生類。 您很少直接從`CCmdTarget`派生類。

有關`OnCmdMsg`指令目標與路由的概述,請參閱[命令目標](../../mfc/command-targets.md), 請參考指令與[映](../../mfc/command-routing.md)[射訊息](../../mfc/mapping-messages.md)。

`CCmdTarget`包括處理沙漏游標顯示的成員函數。 當您希望命令需要一個明顯的時間間隔執行時,顯示沙漏游標。

調度對應於消息映射,用於公開 OLE 自動化`IDispatch`功能。 通過公開此介面,其他應用程式(如 Visual Basic)可以調用到應用程式中。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ccmdtargetbeginwaitcursor"></a><a name="beginwaitcursor"></a>CMD目標::開始等待游標

調用此函數,當希望命令需要一個明顯的時間間隔執行時,將游標顯示為沙漏。

```cpp
void BeginWaitCursor();
```

### <a name="remarks"></a>備註

框架呼叫此函數是為了向使用者顯示它正忙,例如當`CDocument`物件載入或保存到檔中時。

的操作`BeginWaitCursor`並不總是在單個消息處理程式之外有效,因為其他操作(`OnSetCursor`如處理)可能會更改游標。

調用`EndWaitCursor`以還原上一個游標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetccmdtarget"></a><a name="ccmdtarget"></a>CmD目標::CMD目標

建構 `CCmdTarget` 物件。

```
CCmdTarget();
```

## <a name="ccmdtargetdooleverb"></a><a name="dooleverb"></a>CmdTarget::DoOleVerb

導致執行由 OLE 謂詞指定的操作。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*iVerb*<br/>
動詞的數值標識符。

*lpMsg*<br/>
指向描述調用謂詞的事件(如按兩下)的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構的指標。

*hWnd 父母*<br/>
文件視窗的控制代碼，包含物件。

*lpRect*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)結構的指標,該結構以像素為單位定義物件的邊界矩形,以*hwndParent*。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

此成員函數基本上是[IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)) 的實現。 可能的操作由[CCmdTarget::枚舉EmeOleVerbs](#enumoleverbs)枚舉。

## <a name="ccmdtargetenableautomation"></a><a name="enableautomation"></a>CmD目標::啟用自動化

調用此函數以啟用物件的 OLE 自動化。

```cpp
void EnableAutomation();
```

### <a name="remarks"></a>備註

此函數通常從物件的構造函數調用,並且僅當已聲明類調度映射時才應調用。 有關自動化的詳細資訊,請參閱[文章"自動化用戶端](../../mfc/automation-clients.md)"和["自動化伺服器](../../mfc/automation-servers.md)"。

## <a name="ccmdtargetenableconnections"></a><a name="enableconnections"></a>CmD 目標:開啟連線

啟用在連接點上觸發事件。

```cpp
void EnableConnections();
```

### <a name="remarks"></a>備註

要啟用連接點,請調用派生類的構造函數中的此成員函數。

## <a name="ccmdtargetenabletypelib"></a><a name="enabletypelib"></a>CmD 目標::啟用類型Lib

啟用物件的類型庫。

```cpp
void EnableTypeLib();
```

### <a name="remarks"></a>備註

如果`CCmdTarget`派生對象的構造函數提供類型資訊,則調用此成員函數。

## <a name="ccmdtargetendwaitcursor"></a><a name="endwaitcursor"></a>CmD目標::結束等待游標

調用`BeginWaitCursor`成員函數後調用此函數,以便從沙漏游標返回到上一個游標。

```cpp
void EndWaitCursor();
```

### <a name="remarks"></a>備註

框架在調用沙漏游標后還會調用此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="ccmdtargetenumoleverbs"></a><a name="enumoleverbs"></a>Cmd目標::枚舉

枚舉物件的 OLE 謂詞。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>參數

*佩納姆奧勒Verb*<br/>
指向[IEnumOLEVERB 介面](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)的指標。

### <a name="return-value"></a>傳回值

如果物件支援至少一個 OLE 謂詞(在\*這種情況下 *,ppenOleVerb*指向`IEnumOLEVERB`枚舉器介面),則為 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

此成員函數基本上是[IOleObject::enumVerbs 的](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)實現。

## <a name="ccmdtargetfromidispatch"></a><a name="fromidispatch"></a>Cmd目標::從I調度

調用此函數將從類`IDispatch`的自動化成員函數接收的指標映射到實現`CCmdTarget``IDispatch`物件介面的物件中。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>參數

*lpDispatch*<br/>
`IDispatch` 物件的指標。

### <a name="return-value"></a>傳回值

指向與`CCmdTarget`*lpDispatch*關聯的物件的指標。 如果物件未識別為`IDispatch`Microsoft`IDispatch`基礎類 物件,則此功能將返回 NULL。

### <a name="remarks"></a>備註

此函數的結果是對成員函數的調用的相反。 `GetIDispatch`

## <a name="ccmdtargetgetdispatchiid"></a><a name="getdispatchiid"></a>CmD目標::取得調度IID

獲取主調度介面 ID。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>參數

*pIID*<br/>
指向介面 ID 的指標([GUID](/視窗/win32/api/guiddef/ns-guiddef-guid)。

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE,否則為 FALSE。 如果成功\**,pIID*將設置為主調度介面 ID。

### <a name="remarks"></a>備註

派生類應覆蓋此成員函數(如果不重寫,`GetDispatchIID`則返回 FALSE)。 請參考[COleControl](../../mfc/reference/colecontrol-class.md)。

## <a name="ccmdtargetgetidispatch"></a><a name="getidispatch"></a>CmD目標::取得I調度

調用此成員函數從返回`IDispatch``IDispatch`指標或通過引用獲取`IDispatch`指標的自動化方法檢索指標。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>參數

*bAddRef*<br/>
指定是否增加物件的引用計數。

### <a name="return-value"></a>傳回值

與`IDispatch`物件關聯的指標。

### <a name="remarks"></a>備註

對於在其構造函數`EnableAutomation`中調用的物件,使其啟用自動化,此函數返回一個指標,指向通過`IDispatch``IDispatch`介面通信的用戶端使用的基類實現。 呼叫此函數會自動新增對指標的引用,因此不必呼叫[IUnknown:::AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)。

## <a name="ccmdtargetgettypeinfocount"></a><a name="gettypeinfocount"></a>CmD目標::取得類型資訊計數

檢索物件提供的類型資訊介面的數量。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>傳回值

類型資訊介面的數量。

### <a name="remarks"></a>備註

此成員函數基本上實現了[IDispatch:getTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

派生類應重寫此函數以返回提供的類型資訊介面數(0 或 1)。 如果未重寫,`GetTypeInfoCount`則返回 0。 要重寫,請使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏,該宏`GetTypeLib``GetTypeLibCache`還實現 和 。

## <a name="ccmdtargetgettypeinfoofguid"></a><a name="gettypeinfoofguid"></a>Cmd目標::取得資訊

擷取對應到所指定 GUID 的型別描述。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>參數

*lcid*<br/>
區域設定識別碼`LCID`( 。

*guid*<br/>
類型描述的 [GUID](/視窗/win32/api/guiddef/ns-guiddef-guid。

*ppTypeInfo*<br/>
指向介面的`ITypeInfo`指標。

### <a name="return-value"></a>傳回值

指示呼叫成功或失敗的 HRESULT。 如果成功\**,ppTypeInfo*將指向類型資訊介面。

## <a name="ccmdtargetgettypelib"></a><a name="gettypelib"></a>CmD目標::取得類型Lib

獲取指向類型庫的指標。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>參數

*lcid*<br/>
地區設定識別項 (LCID)。

*ppTypeLib*<br/>
指向介面的`ITypeLib`指標。

### <a name="return-value"></a>傳回值

指示呼叫成功或失敗的 HRESULT。 如果成功\**,ppTypeLib*將指向類型庫介面。

### <a name="remarks"></a>備註

派生類應覆蓋此成員函數(如果不重寫,`GetTypeLib`則返回TYPE_E_CANTLOADLIBRARY)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏,該宏`GetTypeInfoCount``GetTypeLibCache`還實現 和 。

## <a name="ccmdtargetgettypelibcache"></a><a name="gettypelibcache"></a>CmD目標::取得類型LibCache

獲取類型庫緩存。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>傳回值

`CTypeLibCache` 物件的指標。

### <a name="remarks"></a>備註

派生類應覆寫此成員函數(如果不重寫`GetTypeLibCache`, 則傳回 NULL)。 使用[IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)宏,該宏`GetTypeInfoCount``GetTypeLib`還實現 和 。

## <a name="ccmdtargetisinvokeallowed"></a><a name="isinvokeallowed"></a>Cmd目標::已呼叫

MFC 的實現調用此函`IDispatch::Invoke`數 ,以確定是否可以調用給定的自動化方法(由*dispid*標識)。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>參數

*不一部分*<br/>
調度識別碼。

### <a name="return-value"></a>傳回值

如果可以調用該方法,則為 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

如果`IsInvokeAllowed`返回 TRUE,`Invoke`則繼續調用 方法;如果返回 TRUE,則繼續調用 方法。否則,`Invoke`將失敗,返回E_UNEXPECTED。

派生類可以重寫此函數以返回適當的值(如果不重寫,`IsInvokeAllowed`則返回 TRUE)。 請特別參見[COleControl:是呼叫允許](../../mfc/reference/colecontrol-class.md#isinvokeallowed)的 。

## <a name="ccmdtargetisresultexpected"></a><a name="isresultexpected"></a>Cmd目標::預期結果

用於`IsResultExpected`確定用戶端是否期望從調用自動化函數返回值。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>傳回值

如果自動化函數應返回值,則非零;否則 0。

### <a name="remarks"></a>備註

OLE 介面向 MFC 提供有關用戶端是否正在使用或忽略函數調用結果的資訊,而 MFC 則使用`IsResultExpected`此資訊來確定調用 的結果。 如果返回值的生產是時間或資源密集型,則可以在計算返回值之前調用此函數來提高效率。

此函數僅返回 0 一次,以便從用戶端調用的自動化函數中調用它們,則從其他自動化函數中獲取有效返回值。

`IsResultExpected`如果在自動化函數調用未進行時調用,則返回非零值。

## <a name="ccmdtargetoncmdmsg"></a><a name="oncmdmsg"></a>CmD目標::OnCmdMsg

由框架呼叫以路由和調度命令訊息,並處理命令使用者介面物件的更新。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>參數

*nID*<br/>
包含命令識別碼。

*n代碼*<br/>
標識命令通知代碼。 有關*nCode*的值的詳細資訊,請參閱**備註**。

*pExtra*<br/>
根據*nCode*的值使用。 有關*pExtra*的更多資訊,請參閱**備註**。

*pHandlerInfo*<br/>
如果不是`OnCmdMsg`NULL, 請填寫*pHandlerInfo*結構的*pTarget*和*pmf*成員,而不是調度命令。 通常,此參數應為 NULL。

### <a name="return-value"></a>傳回值

處理消息時非零;否則 0。

### <a name="remarks"></a>備註

這是框架命令體系結構的主要實現例程。

在執行時,`OnCmdMsg`將命令調度到其他物件,或者透過呼叫 root 類來處理`CCmdTarget::OnCmdMsg`命令本身, 該類執行實際的消息映射查找。 有關預設指令路由的完整說明,請參閱[訊息處理和映射主題](../../mfc/message-handling-and-mapping.md)。

在極少數情況下,您可能希望重寫此成員函數以擴展框架的標準命令路由。 有關命令路由體系結構的高級詳細資訊,請參閱[技術說明 21。](../../mfc/tn021-command-and-message-routing.md)

`OnCmdMsg`如果重寫 ,則必須提供*nCode、* 命令通知代碼和*pExtra*的相應值,具體取決於*nCode*的值。 下表列出了其相應的值:

|*n代碼*值|*p額外*值|
|-------------------|--------------------|
|CN_COMMAND|[CmDUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

## <a name="ccmdtargetonfinalrelease"></a><a name="onfinalrelease"></a>Cmd目標::最終發佈

釋放物件或物件的最後一個 OLE 引用時,由框架調用。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>備註

重寫此函數以為此情況提供特殊處理。 預設實現將刪除該物件。

## <a name="ccmdtargetrestorewaitcursor"></a><a name="restorewaitcursor"></a>Cmd目標::恢復等待游標

呼叫此函數以在系統游標更改後(例如,在長時間操作期間打開消息框然後關閉後)還原相應的沙漏游標。

```cpp
void RestoreWaitCursor();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument 類別](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate 類別](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp 類別](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)<br/>
[COle排程驅動程式類別](../../mfc/reference/coledispatchdriver-class.md)
