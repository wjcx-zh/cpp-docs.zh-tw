---
title: COleControlSite 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504309"
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
|[COleControlSite::BindDefaultProperty](#binddefaultproperty)|將主控控制項的預設屬性系結至資料來源。|
|[COleControlSite::BindProperty](#bindproperty)|將主控控制項的屬性系結至資料來源。|
|[COleControlSite::CreateControl](#createcontrol)|建立主控的 ActiveX 控制項。|
|[COleControlSite::DestroyControl](#destroycontrol)|終結主控的控制項。|
|[COleControlSite::DoVerb](#doverb)|執行主控控制項的特定動詞。|
|[COleControlSite::EnableDSC](#enabledsc)|啟用控制網站的資料來源。|
|[COleControlSite::EnableWindow](#enablewindow)|啟用控制網站。|
|[COleControlSite::FreezeEvents](#freezeevents)|指定控制項網站是否接受事件。|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|抓取主控控制項的預設按鈕程式碼。|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|抓取控制項的識別碼。|
|[COleControlSite::GetEventIID](#geteventiid)|抓取主控控制項之事件介面的識別碼。|
|[COleControlSite::GetExStyle](#getexstyle)|抓取控制網站的延伸樣式。|
|[COleControlSite::GetProperty](#getproperty)|抓取主控控制項的特定屬性。|
|[COleControlSite::GetStyle](#getstyle)|抓取控制網站的樣式。|
|[COleControlSite::GetWindowText](#getwindowtext)|抓取裝載控制項的文字。|
|[COleControlSite::InvokeHelper](#invokehelper)|叫用主控控制項的特定方法。|
|[COleControlSite::InvokeHelperV](#invokehelperv)|使用引數的可變清單, 叫用裝載控制項的特定方法。|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|決定控制項是否為視窗中的預設按鈕。|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|檢查控制項網站的可見狀態。|
|[COleControlSite::ModifyStyle](#modifystyle)|修改控制網站的目前擴充樣式。|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|修改控制網站的目前樣式。|
|[COleControlSite::MoveWindow](#movewindow)|變更控制網站的位置。|
|[COleControlSite::QuickActivate](#quickactivate)|快速啟動主控的控制項。|
|[COleControlSite::SafeSetProperty](#safesetproperty)|設定控制項的屬性或方法, 而不會擲回例外狀況。|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|設定視窗中的預設按鈕。|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|抓取控制項的識別碼。|
|[COleControlSite::SetFocus](#setfocus)|將焦點設定為控制網站。|
|[COleControlSite::SetProperty](#setproperty)|設定主控控制項的特定屬性。|
|[COleControlSite::SetPropertyV](#setpropertyv)|使用引數清單來設定裝載控制項的特定屬性。|
|[COleControlSite::SetWindowPos](#setwindowpos)|設定控制網站的位置。|
|[COleControlSite::SetWindowText](#setwindowtext)|設定主控控制項的文字。|
|[COleControlSite::ShowWindow](#showwindow)|顯示或隱藏控制網站。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|抓取主控控制項的鍵盤資訊和助憶鍵。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|判斷主控控制項是否為無視窗控制項。|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|包含控制項鍵盤處理的相關資訊。|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|控制項的連接點的 cookie。|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|裝載控制項的其他狀態。|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|控制項`IPropertyNotifySink`的 cookie。|
|[COleControlSite::m_dwStyle](#m_dwstyle)|主控控制項的樣式。|
|[COleControlSite::m_hWnd](#m_hwnd)|控制網站的控制碼。|
|[COleControlSite::m_iidEvents](#m_iidevents)|裝載控制項之事件介面的識別碼。|
|[COleControlSite::m_nID](#m_nid)|主控控制項的識別碼。|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|主控控制項之`IOleInPlaceActiveObject`物件的指標。|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|主控控制項的容器。|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|主控控制項之`IOleInPlaceObject`物件的指標。|
|[COleControlSite::m_pObject](#m_pobject)|控制項`IOleObjectInterface`介面的指標。|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|控制項`IOleInPlaceObjectWindowless`介面的指標。|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|裝載控制項的視窗物件指標。|
|[COleControlSite::m_rect](#m_rect)|控制網站的維度。|

## <a name="remarks"></a>備註

這項支援是內嵌 ActiveX 控制項取得其顯示網站位置與範圍、其名字標記、其使用者介面、其環境屬性以及其容器所提供的其他資源之相關資訊的主要方式。 `COleControlSite`完整執行[IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite)、 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)、 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) `IBoundObjectSite`、、 `INotifyDBEvents`、 [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md)介面。 此外, IDispatch 介面 (提供環境屬性和事件接收器的支援) 也會一併執行。

若要使用`COleControlSite`來建立 ActiveX 控制項網站, 請從`COleControlSite`衍生類別。 在容器的衍生類別中 (例如, 您的對話方塊) 會覆`CWnd::CreateControlSite`寫函數。 `CWnd`

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>需求

**標頭:** afxocc。h

##  <a name="binddefaultproperty"></a>  COleControlSite::BindDefaultProperty

將呼叫物件的預設簡單系結屬性 (如類型程式庫中所標記), 系結至資料來源控制項的 DataSource、使用者名稱、密碼和 SQL 屬性所定義的基礎資料指標。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
在要系結至資料來源控制項的資料繫結控制項上, 指定 DISPID 的屬性。

*vtProp*<br/>
指定要系結之屬性的類型, 例如 VT_BSTR、VT_VARIANT 等等。

*szFieldName*<br/>
在資料來源控制項所提供的資料指標中, 指定要系結屬性的資料行名稱。

*pDSCWnd*<br/>
衍生物件的指標`CWnd`, 其裝載屬性將系結至的資料來源控制項。

### <a name="remarks"></a>備註

您`CWnd`呼叫這個函式的物件必須是資料繫結控制項。

##  <a name="bindproperty"></a>  COleControlSite::BindProperty

將呼叫物件的簡單系結屬性 (如類型程式庫中所標記) 系結至資料來源控制項的 DataSource、使用者名稱、密碼和 SQL 屬性所定義的基礎資料指標。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>參數

*dwDispId*<br/>
在要系結至資料來源控制項的資料繫結控制項上, 指定 DISPID 的屬性。

*pWndDSC*<br/>
衍生物件的指標`CWnd`, 其裝載屬性將系結至的資料來源控制項。

### <a name="remarks"></a>備註

您`CWnd`呼叫這個函式的物件必須是資料繫結控制項。

##  <a name="colecontrolsite"></a>  COleControlSite::COleControlSite

建立新`COleControlSite`的物件。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>參數

*pCtrlCont*<br/>
控制項容器的指標 (表示裝載 AtiveX 控制項的視窗)。

### <a name="remarks"></a>備註

此函式是由[COccManager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer)函數所呼叫。 如需自訂容器建立的詳細資訊, 請參閱[COccManager:: CreateSite](../../mfc/reference/coccmanager-class.md#createsite)。

##  <a name="createcontrol"></a>COleControlSite:: CreateControl

建立由`COleControlSite`物件主控的 ActiveX 控制項。

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

*pWndCtrl*<br/>
代表控制項的視窗物件指標。

*clsid*<br/>
控制項的唯一類別 ID。

*lpszWindowName*<br/>
要在控制項中顯示的文字指標。 設定 winodw 標題或文字屬性的值 (如果有的話)。

*dwStyle*<br/>
視窗樣式。 可用的樣式列在 [**備註**] 區段底下。

*rect*<br/>
指定控制項的大小和位置。 它可以`CRect`是物件`RECT`或結構。

*nID*<br/>
指定控制項的子視窗識別碼。

*pPersist*<br/>
的指標, `CFile`其中包含控制項的持續狀態。 預設值為 Null, 表示控制項會自行初始化, 而不會從任何持續性儲存體還原其狀態。 如果不是 Null, 它應該是衍生物件的`CFile`指標, 其中包含控制項的持續性資料 (以資料流程或儲存體的形式)。 這項資料可能已儲存在用戶端先前的啟用中。 可以包含其他資料, 但在`CreateControl`呼叫時, 必須將其讀寫指標設定為持續性資料的第一個位元組。 `CFile`

*bStorage*<br/>
指出*pPersist*中的資料是否應解讀為`IStorage`或`IStream`資料。 如果*pPersist*中的資料是儲存體, 則*BSTORAGE*應為 TRUE。 如果*pPersist*中的資料是資料流程, *BSTORAGE*應該是 FALSE。 預設值為 FALSE。

*bstrLicKey*<br/>
選擇性的授權金鑰資料。 只有在建立需要執行時間授權金鑰的控制項時, 才需要此資料。 如果控制項支援授權, 您必須提供授權金鑰, 才能成功建立控制項。 預設值為 Null。

*ppt*<br/>
`POINT`結構的指標, 其中包含控制項的左上角。 控制項的大小取決於*psize*的值。 *Ppt*和*psize*值是選擇性的方法, 可指定控制項的 opf 大小和位置。

*psize*<br/>
`SIZE`結構的指標, 其中包含控制項的大小。 左上角是由*ppt*的值決定。 *Ppt*和*psize*值是選擇性的方法, 可指定控制項的 opf 大小和位置。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

僅支援`CreateControl`部分的 Windows *dwStyle*旗標:

- WS_VISIBLE 會建立一開始顯示的視窗。 如果您想要立即顯示控制項 (例如一般視窗), 則為必要。

- WS_DISABLED 會建立一開始停用的視窗。 停用的視窗無法接收使用者的輸入。 如果控制項具有已啟用的屬性, 則可以設定。

- WS_BORDER 會建立具有細線條框線的視窗。 如果控制項具有 BorderStyle 屬性, 則可以設定。

- WS_GROUP 指定控制項群組的第一個控制項。 使用者可以使用方向鍵, 將鍵盤焦點從群組中的一個控制項變更為下一個。 在第一個控制項屬於相同群組之後, 以 WS_GROUP 樣式定義的所有控制項。 下一個具有 WS_GROUP 樣式的控制項會結束群組, 並啟動下一個群組。

- WS_TABSTOP 指定當使用者按下 TAB 鍵時, 可接收鍵盤焦點的控制項。 按 TAB 鍵會將鍵盤焦點變更為 WS_TABSTOP 樣式的下一個控制項。

使用第二個多載來建立預設大小的控制項。

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

`COleControlSite`終結物件。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

完成後, 物件會從記憶體釋放, 而且物件的任何指標都不再有效。

##  <a name="doverb"></a>  COleControlSite::DoVerb

執行指定的動詞。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>參數

*nVerb*<br/>
指定要執行的指令動詞。 它可以包含下列其中一項:

|值|意義|符號|
|-----------|-------------|------------|
|0|主動詞命令|OLEIVERB_PRIMARY|
|-1|次要動詞|(無)|
|1|顯示要編輯的物件。|OLEIVERB_SHOW|
|-2|在個別視窗中編輯專案。|OLEIVERB_OPEN|
|-3|隱藏物件。|OLEIVERB_HIDE|
|-4|就地啟用控制項。|OLEIVERB_UIACTIVATE|
|-5|就地啟動控制項, 而不需要額外的使用者介面元素。|OLEIVERB_INPLACEACTIVATE|
|-7|顯示控制項的屬性。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
導致啟用專案之訊息的指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

此函式會直接呼叫控制項的`IOleObject`介面, 以執行指定的動詞命令。 如果因此函式呼叫而擲回例外狀況, 則會傳回 HRESULT 錯誤碼。

如需詳細資訊, 請參閱 Windows SDK 中的[IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="enabledsc"></a>  COleControlSite::EnableDSC

啟用控制網站的資料來源。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>備註

由架構呼叫, 以啟用及初始化控制網站的資料來源。 覆寫此函式以提供自訂的行為。

##  <a name="enablewindow"></a>  COleControlSite::EnableWindow

啟用或停用控制網站的滑鼠和鍵盤輸入。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
指定是否要啟用或停用視窗:如果要啟用視窗輸入, 則為 TRUE, 否則為 FALSE。

### <a name="return-value"></a>傳回值

如果視窗先前已停用, 則為非零, 否則為0。

##  <a name="freezeevents"></a>COleControlSite::FreezeEvents

指定控制項網站是否會處理或忽略從控制項引發的事件。

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>參數

*bFreeze*<br/>
指定控制項站台是否想要停止接受事件。 如果控制項不接受事件則為非零;否則為零。

### <a name="remarks"></a>備註

如果*bFreeze*為 TRUE, 則控制網站會要求控制項停止帶入事件。 如果*bFreeze*為 FALSE, 則控制網站會要求控制項繼續引發事件。

> [!NOTE]
>  控制項不需要在控制網站要求時停止引發事件。 它可以繼續引發, 但控制網站會忽略所有後續事件。

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

抓取控制項的鍵盤助憶鍵和鍵盤行為的相關資訊。

```
void GetControlInfo();
```

### <a name="remarks"></a>備註

這項資訊會儲存在[COleControlSite:: m_ctlInfo](#m_ctlinfo)中。

##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode

決定控制項是否為預設的 [推送] 按鈕。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>傳回值

可為下列其中一個值：

- DLGC_DEFPUSHBUTTON 控制項是對話方塊中的預設按鈕。

- DLGC_UNDEFPUSHBUTTON 控制項不是對話方塊中的預設按鈕。

- **0**控制項不是按鈕。

##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID

抓取控制項的識別碼。

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>傳回值

控制項的對話方塊專案識別碼。

##  <a name="geteventiid"></a>  COleControlSite::GetEventIID

抓取控制項預設事件介面的指標。

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>參數

*piid*<br/>
介面識別碼的指標。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。 如果成功, *piid*會包含控制項預設事件介面的介面識別碼。

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

抓取視窗的延伸樣式。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>傳回值

控制項視窗的延伸樣式。

### <a name="remarks"></a>備註

若要取得一般樣式, 請呼叫[COleControlSite:: GetStyle](#getstyle)。

##  <a name="getproperty"></a>  COleControlSite::GetProperty

取得*dwDispID*所指定的控制項屬性。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別在控制項的預設`IDispatch`介面上所找到之屬性的分派識別碼。

*vtProp*<br/>
指定要抓取的屬性型別。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvProp*<br/>
將接收屬性值的變數位址。 它必須符合*vtProp*所指定的類型。

### <a name="remarks"></a>備註

此值會透過*pvProp*傳回。

##  <a name="getstyle"></a>  COleControlSite::GetStyle

抓取控制網站的樣式。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>傳回值

視窗的樣式。

### <a name="remarks"></a>備註

如需可能值的清單, 請參閱[Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 若要取得控制網站的擴充樣式, 請呼叫[COleControlSite:: GetExStyle](#getexstyle)。

##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText

抓取控制項的目前文字。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>參數

*str*<br/>
`CString`物件的參考, 其中包含控制項目前的文字。

### <a name="remarks"></a>備註

如果控制項支援 Caption stock 屬性, 則會傳回這個值。 如果不支援標題庫存屬性, 則會傳回 Text 屬性的值。

##  <a name="invokehelper"></a>COleControlSite:: InvokeHelper

在*wFlags*所指定的內容中, 叫用*dwDispID*所指定的方法或屬性。

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要叫用的屬性或方法的分派識別碼 (可在控制項`IDispatch`的介面上找到)。

*wFlags*<br/>
描述對 IDispatch:: Invoke 呼叫之內容的旗標。 如需可能的*wFlags*值`IDispatch::Invoke` , 請參閱 Windows SDK 中的。

*vtRet*<br/>
指定傳回值的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須符合*vtRet*所指定的類型。

*pbParamInfo*<br/>
以 null 結束的位元組字串指標, 指定*pbParamInfo*之後的參數類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
參數的變數清單, 屬於*pbParamInfo*中指定的類型。

### <a name="remarks"></a>備註

*PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 引數的變數清單會以 .。。在語法宣告中。

此函式會將參數轉換為 VARIANTARG 值, 然後`IDispatch::Invoke`在控制項上叫用方法。 若呼叫 `IDispatch::Invoke` 失敗，此函式會擲回例外狀況。 如果所傳回`IDispatch::Invoke`的狀態碼為`DISP_E_EXCEPTION` `COleDispatchException` , 則此函式會擲回物件, 否則`COleException`會擲回。

##  <a name="invokehelperv"></a>COleControlSite::InvokeHelperV

在*wFlags*所指定的內容中, 叫用*dwDispID*所指定的方法或屬性。

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

*dwDispID*<br/>
識別要叫用的屬性或方法的分派識別碼 (可在控制項`IDispatch`的介面上找到)。

*wFlags*<br/>
描述對 IDispatch:: Invoke 呼叫之內容的旗標。

*vtRet*<br/>
指定傳回值的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須符合*vtRet*所指定的類型。

*pbParamInfo*<br/>
以 null 結束的位元組字串指標, 指定*pbParamInfo*之後的參數類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*argList*<br/>
變數引數清單的指標。

### <a name="remarks"></a>備註

*PbParamInfo*參數會指定傳遞至方法或屬性的參數類型。 您可以使用*va_list*參數來傳遞所叫用之方法或屬性的額外參數。

通常, 會呼叫`COleControlSite::InvokeHelper`這個函式。

##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton

決定控制項是否為預設按鈕。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>傳回值

如果控制項是視窗上的預設按鈕, 則為非零, 否則為零。

##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled

決定是否啟用控制網站。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>傳回值

如果已啟用控制項, 則為非零, 否則為零。

### <a name="remarks"></a>備註

此值會從控制項的已啟用內建屬性中抓取。

##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless

判斷物件是否為無視窗控制項。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>備註

如果控制項沒有視窗, 則為非零, 否則為零。

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

控制項如何處理鍵盤輸入的資訊。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>備註

這項資訊會儲存在[CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo)結構中。

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

包含來自控制項事件接收器的連接點 cookie。

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>  COleControlSite::m_dwMiscStatus

包含控制項的其他資訊。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)。

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

包含[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) cookie。

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle

包含控制項的視窗樣式。

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd

包含控制項的 HWND, 如果控制項為無視窗, 則為 Null。

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents

包含控制項預設事件接收介面的介面識別碼。

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

包含控制項的對話方塊專案識別碼。

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

包含控制項的[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)介面。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

包含控制項的容器 (代表表單)。

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

包含控制項`IOleInPlaceObject`的[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)介面。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

包含控制項`IOleObjectInterface`的介面。

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

包含控制項`IOleInPlaceObjectWindowless`的[IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)介面。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

包含代表控制項本身之`CWnd`物件的指標。

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>  COleControlSite::m_rect

包含控制項的界限 (相對於容器的視窗)。

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

*dwRemove*<br/>
要從目前的視窗樣式中移除的樣式。

*dwAdd*<br/>
要從目前視窗樣式新增的樣式。

*nFlags*<br/>
視窗定位旗標。 如需可能值的清單, 請參閱 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函數。

### <a name="return-value"></a>傳回值

如果樣式已變更, 則為非零, 否則為零。

### <a name="remarks"></a>備註

控制項的已啟用庫存屬性將會修改, 以符合 WS_DISABLED 的設定。 控制項的內建框線樣式屬性將會修改, 以符合所要求的 WS_BORDER 設定。 所有其他樣式會直接套用至控制項的視窗控制碼 (如果有的話)。

修改控制項的視窗樣式。 您可以使用位 OR ( &#124; ) 運算子來結合要加入或移除的樣式。 如需可用視窗樣式的詳細資訊, 請參閱 Windows SDK 中的[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)函數。

如果*nFlags*為非零`ModifyStyle`值, 會`SetWindowPos`呼叫 Win32 函式, 並將*nFlags*與下列四個旗標結合, 以重新繪製視窗:

- SWP_NOSIZE 會保留目前的大小。

- SWP_NOMOVE 會保留目前的位置。

- SWP_NOZORDER 會保留目前的 Z 順序。

- SWP_NOACTI加值稅E 不會啟動視窗。

若要修改視窗的延伸樣式, 請呼叫[ModifyStyleEx](#modifystyleex)。

##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx

修改控制項的延伸樣式。

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*dwRemove*<br/>
要從目前視窗樣式中移除的擴充樣式。

*dwAdd*<br/>
要從目前視窗樣式新增的擴充樣式。

*nFlags*<br/>
視窗定位旗標。 如需可能值的清單, 請參閱 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函數。

### <a name="return-value"></a>傳回值

如果樣式已變更, 則為非零, 否則為零。

### <a name="remarks"></a>備註

控制項的「內建外觀」屬性將會修改, 以符合 WS_EX_CLIENTEDGE 的設定。 所有其他延伸視窗樣式會直接套用至控制項的視窗控制碼 (如果有的話)。

修改控制項網站物件的視窗擴充樣式。 您可以使用位 OR ( &#124; ) 運算子來結合要加入或移除的樣式。 如需可用視窗樣式的詳細資訊, 請參閱 Windows SDK 中的[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函數。

如果*nFlags*為非零`ModifyStyleEx`值, 會`SetWindowPos`呼叫 Win32 函式, 並將*nFlags*與下列四個旗標結合, 以重新繪製視窗:

- SWP_NOSIZE 會保留目前的大小。

- SWP_NOMOVE 會保留目前的位置。

- SWP_NOZORDER 會保留目前的 Z 順序。

- SWP_NOACTI加值稅E 不會啟動視窗。

若要修改視窗的延伸樣式, 請呼叫[ModifyStyle](#modifystyle)。

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

*x*<br/>
視窗左側的新位置。

*y*<br/>
視窗頂端的新位置。

*nWidth*<br/>
視窗的新寬度

*nHeight*<br/>
視窗的新高度。

##  <a name="quickactivate"></a>  COleControlSite::QuickActivate

快速啟動包含的控制項。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>傳回值

如果已啟用控制項網站, 則為非零, 否則為零。

### <a name="remarks"></a>備註

只有當使用者正在覆寫控制項的建立進程時, 才應該呼叫這個函式。

在快速`IPersist*::InitNew`啟動發生之後, 應該會呼叫和方法。`IPersist*::Load` 在快速啟用期間, 控制項應該會建立與容器接收器的連線。 不過, 在呼叫或`IPersist*::Load` `IPersist*::InitNew`之前, 這些連接都不會上線。

##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty

設定*dwDispID*所指定的控制項屬性。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要設定之控制項`IDispatch`介面上所找到之屬性或方法的分派識別碼。

*vtProp*<br/>
指定要設定的屬性類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
*VtProp*所指定之類型的單一參數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
>  與`SetProperty` 和`SetPropertyV`不同, 如果遇到錯誤 (例如嘗試設定不存在的屬性), 則不會擲回任何例外狀況。

##  <a name="setdefaultbutton"></a>  COleControlSite::SetDefaultButton

將控制項設定為預設按鈕。

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>參數

*bDefault*<br/>
如果控制項應該成為預設按鈕, 則為非零。否則為零。

### <a name="remarks"></a>備註

> [!NOTE]
>  控制項必須設定 OLEMISC_ACTSLIKEBUTTON 狀態位。

##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID

變更控制項的對話方塊專案識別碼的值。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
新的識別碼值。

### <a name="return-value"></a>傳回值

如果成功, 則為視窗的先前對話方塊專案識別碼;否則為0。

### <a name="remarks"></a>備註

##  <a name="setfocus"></a>  COleControlSite::SetFocus

將焦點設為控制項。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>參數

*lpmsg*<br/>
[MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)的指標。 這個結構包含的 Windows 訊息, 會`SetFocus`觸發目前控制網站中所含控制項的要求。

### <a name="return-value"></a>傳回值

先前具有焦點之視窗的指標。

##  <a name="setproperty"></a>  COleControlSite::SetProperty

設定*dwDispID*所指定的控制項屬性。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要設定之控制項`IDispatch`介面上所找到之屬性或方法的分派識別碼。

*vtProp*<br/>
指定要設定的屬性類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
*VtProp*所指定之類型的單一參數。

### <a name="remarks"></a>備註

如果`SetProperty`遇到錯誤, 則會擲回例外狀況。

例外狀況的類型取決於嘗試設定屬性或方法的傳回值。 如果傳回值為`DISP_E_EXCEPTION` `COleDispatchExcpetion` , `COleException`則會擲回, 否則為。

##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV

設定*dwDispID*所指定的控制項屬性。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
識別要設定之控制項`IDispatch`介面上所找到之屬性或方法的分派識別碼。

*vtProp*<br/>
指定要設定的屬性類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*argList*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

您可以使用*arg_list*參數來 passeed 所叫用之方法或屬性的額外參數。 如果`SetProperty`遇到錯誤, 則會擲回例外狀況。

例外狀況的類型取決於嘗試設定屬性或方法的傳回值。 如果傳回值為`DISP_E_EXCEPTION` `COleDispatchExcpetion` , `COleException`則會擲回, 否則為。

##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos

設定控制網站的大小、位置和迭置順序。

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

*pWndInsertAfter*<br/>
視窗的指標。

*x*<br/>
視窗左側的新位置。

*y*<br/>
視窗頂端的新位置。

*cx*<br/>
視窗的新寬度

*cy*<br/>
視窗的新高度。

*nFlags*<br/>
指定視窗調整大小和定位旗標。 如需可能的值, 請參閱 Windows SDK 中[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)的「備註」一節。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為零。

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

設定控制項網站的文字。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
要當做新標題或控制項文字使用之以 null 結束的字串指標。

### <a name="remarks"></a>備註

此函式會先嘗試設定標題庫存屬性。 如果不支援標題庫存屬性, 則會改為設定 Text 屬性。

##  <a name="showwindow"></a>COleControlSite:: ShowWindow

設定視窗的顯示狀態。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>參數

*nCmdShow*<br/>
指定控制項網站的顯示方式。 它必須是下列其中一個值:

- SW_HIDE 會隱藏此視窗, 並將啟用傳遞至另一個視窗。

- SW_MINIMIZE 會將視窗最小化, 並啟用系統清單中的最上層視窗。

- SW_RESTORE 會啟用並顯示視窗。 如果視窗最小化或最大化, Windows 就會將它還原成原始大小和位置。

- SW_SHOW 會啟動視窗, 並以其目前的大小和位置顯示。

- SW_SHOWMAXIMIZED 會啟用視窗, 並將它顯示為最大化的視窗。

- SW_SHOWMINIMIZED 會啟用視窗, 並將它顯示為圖示。

- SW_SHOWMINNOACTIVE 會將視窗顯示為圖示。 目前作用中的視窗仍為使用中狀態。

- SW_SHOWNA 會將視窗顯示為目前狀態。 目前作用中的視窗仍為使用中狀態。

- SW_SHOWNOACTI加值稅E 會將視窗顯示在其最新的大小和位置。 目前作用中的視窗仍為使用中狀態。

- SW_SHOWNORMAL 會啟用並顯示視窗。 如果視窗最小化或最大化, Windows 就會將它還原成原始大小和位置。

### <a name="return-value"></a>傳回值

如果視窗先前為可見, 則為非零;如果視窗先前已隱藏, 則為0。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
