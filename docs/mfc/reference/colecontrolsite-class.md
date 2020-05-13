---
title: COle 控制網站類別
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
ms.openlocfilehash: 90c41a1be1a66cdceebb3f045a98167e56b7cf4c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753953"
---
# <a name="colecontrolsite-class"></a>COle 控制網站類別

提供自訂用戶端控制項介面的支援。

## <a name="syntax"></a>語法

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COle 控制網站:COle 控制網站](#colecontrolsite)|建構 `COleControlSite` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COle 控制網站::結合預設屬性](#binddefaultproperty)|將托管控件的默認屬性綁定到數據源。|
|[COle 控制網站:結合屬性](#bindproperty)|將托管控件的屬性綁定到數據源。|
|[COle 控制網站:建立控制](#createcontrol)|創建託管的 ActiveX 控制件。|
|[COleControlSite::D控制](#destroycontrol)|銷毀托管控件。|
|[COleControlSite::DoVerb](#doverb)|執行託管控件的特定謂詞。|
|[COle 控制網站:啟用DSC](#enabledsc)|支援控制網站的數據源。|
|[COle 控制網站開啟視窗](#enablewindow)|啟用控制網站。|
|[COle 控制網站:凍結事件](#freezeevents)|指定控制項網站是否接受事件。|
|[COle 控制網站:取得DefBtn代碼](#getdefbtncode)|檢索托管控件的默認按鈕代碼。|
|[COle 控制網站:取得DlgCtrlID](#getdlgctrlid)|檢索控件的標識碼。|
|[COle 控制網站:取得事件Id](#geteventiid)|檢索托管控件的事件介面的 ID。|
|[COle 控制網站:取得樣式](#getexstyle)|檢索控件網站的擴展樣式。|
|[COle 控制網站:取得財產](#getproperty)|檢索托管控件的特定屬性。|
|[COle 控制網站:取得樣式](#getstyle)|檢索控件網站的樣式。|
|[COle 控制網站:抓取視窗文字](#getwindowtext)|檢索托管控件的文本。|
|[COle 控制網站::呼叫説明者](#invokehelper)|調用托管控件的特定方法。|
|[COle 控制網站::呼叫説明者V](#invokehelperv)|使用參數的變數清單調用托管控件的特定方法。|
|[COle 控制網站:預設按鈕](#isdefaultbutton)|確定控制項是否為視窗中的預設按鈕。|
|[COle 控制網站開啟視窗](#iswindowenabled)|檢查控制網站的可見狀態。|
|[COle 控制網站:修改樣式](#modifystyle)|修改控制項網站的當前擴展樣式。|
|[COle 控制網站:修改樣式](#modifystyleex)|修改控件網站的當前樣式。|
|[COle 控制網站:移動視窗](#movewindow)|更改控制網站的位置。|
|[COle 控制網站:快速啟動](#quickactivate)|快速啟動托管控件。|
|[COle 控制網站:安全設定屬性](#safesetproperty)|設置控件的屬性或方法,而不會引發異常。|
|[COle 控制網站:設定預設按鈕](#setdefaultbutton)|設置視窗中的預設按鈕。|
|[COle 控制網站:SetDlgCtrlID](#setdlgctrlid)|檢索控件的標識碼。|
|[COle 控制網站:設定焦點](#setfocus)|將焦點設置到控制網站。|
|[COle 控制網站:設定屬性](#setproperty)|設置托管控件的特定屬性。|
|[COle 控制網站:SetPropertyV](#setpropertyv)|使用參數的可變清單設置托管控件的特定屬性。|
|[COle 控制網站:設定視窗位置](#setwindowpos)|設置控制網站的位置。|
|[COle 控制網站:設定視窗文字](#setwindowtext)|設置托管控件的文本。|
|[COle 控制網站:顯示視窗](#showwindow)|顯示或隱藏控制網站。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[COle 控制網站:取得控制資訊](#getcontrolinfo)|檢索托管控件的鍵盤資訊和助記符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COle 控制網站:m_bIsWindowless](#m_biswindowless)|確定托管控件是否為無視窗控制項。|
|[COle 控制網站:m_ctlInfo](#m_ctlinfo)|包含有關控制項的鍵盤處理的資訊。|
|[COle 控制網站:m_dwEventSink](#m_dweventsink)|控件連接點的 Cookie。|
|[COle 控制網站:m_dwMiscStatus](#m_dwmiscstatus)|托管控件的雜項狀態。|
|[COle 控制網站:m_dwPropNotifySink](#m_dwpropnotifysink)|控件`IPropertyNotifySink`的 Cookie。|
|[COle 控制網站:m_dwStyle](#m_dwstyle)|托管控件的樣式。|
|[COle 控制網站:m_hWnd](#m_hwnd)|控制網站的句柄。|
|[COle 控制網站:m_iidEvents](#m_iidevents)|托管控件的事件介面的 ID。|
|[COle 控制網站:m_nID](#m_nid)|托管控件的 ID。|
|[COle 控制網站:m_pActiveObject](#m_pactiveobject)|指向托管控件`IOleInPlaceActiveObject`物件的指標。|
|[COle 控制網站:m_pCtrlCont](#m_pctrlcont)|托管控件的容器。|
|[COle 控制網站:m_pInPlaceObject](#m_pinplaceobject)|指向托管控件`IOleInPlaceObject`物件的指標。|
|[COle 控制網站:m_pObject](#m_pobject)|指向控件`IOleObjectInterface`介面的指標。|
|[COle 控制網站:m_pWindowlessObject](#m_pwindowlessobject)|指向控件`IOleInPlaceObjectWindowless`介面的指標。|
|[COle 控制網站:m_pWndCtrl](#m_pwndctrl)|指向托管控件的視窗物件的指標。|
|[COle控制網站::m_rect](#m_rect)|控制網站的尺寸。|

## <a name="remarks"></a>備註

此支援是嵌入式 ActiveX 控制項獲取有關其顯示網站的位置和範圍、其名字物件、使用者介面、其環境屬性及其容器提供的其他資源的主要方法。 `COleControlSite`全面實施[IOleControlSite,IOleInPlaceSite,IOleClientSite,IpropertynotifySink,、、IrowSetnotify](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite)[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)`IBoundObjectSite``INotifyDBEvents`[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)[介面](../../data/oledb/irowsetnotifyimpl-class.md)。 此外,還實現了 IDispatch 介面(支援環境屬性和事件接收器)。

要使用`COleControlSite`創建 ActiveX 控制件網站,`COleControlSite`請派生 類。 在容器`CWnd`的派生類中(例如,對話框)將覆蓋該`CWnd::CreateControlSite`函數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>需求

**標題:** afxocc.h

## <a name="colecontrolsitebinddefaultproperty"></a><a name="binddefaultproperty"></a>COle 控制網站::結合預設屬性

將調用物件的預設簡單綁定屬性(如類型庫中標記)綁定到數據源控制件的 DataSource、使用者名、密碼和 SQL 屬性定義的基礎游標。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
指定要綁定到資料來源控制件的資料綁定控制項上屬性的DISPID。

*vtProp*<br/>
指定要綁定的屬性的類型,例如,VT_BSTR、VT_VARIANT等。

*szfield名稱*<br/>
指定列的名稱,在數據源控制件提供的游標中,該屬性將綁定到該列。

*pDSCWnd*<br/>
指向`CWnd`承載將屬性綁定到的數據源控件的派生物件的指標。

### <a name="remarks"></a>備註

呼叫`CWnd`此函數的物件必須是數據綁定控制項。

## <a name="colecontrolsitebindproperty"></a><a name="bindproperty"></a>COle 控制網站:結合屬性

將調用物件的簡單綁定屬性(如類型庫中標記)綁定到數據源控制項的 DataSource、使用者名、密碼和 SQL 屬性定義的基礎游標。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>參數

*dwDispId*<br/>
指定要綁定到資料來源控制件的資料綁定控制項上屬性的DISPID。

*pWndDSC*<br/>
指向`CWnd`承載將屬性綁定到的數據源控件的派生物件的指標。

### <a name="remarks"></a>備註

呼叫`CWnd`此函數的物件必須是數據綁定控制項。

## <a name="colecontrolsitecolecontrolsite"></a><a name="colecontrolsite"></a>COle 控制網站:COle 控制網站

建構新的 `COleControlSite` 物件。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>參數

*pCtrlCont*<br/>
指向控制項容器的指標(表示承載 AtiveX 控制件的視窗)。

### <a name="remarks"></a>備註

此函數由[COccManager:創建容器](../../mfc/reference/coccmanager-class.md#createcontainer)函數調用。 有關自訂容器創建的詳細資訊,請參閱[COccManager:::createSite](../../mfc/reference/coccmanager-class.md#createsite)。

## <a name="colecontrolsitecreatecontrol"></a><a name="createcontrol"></a>COle 控制網站:建立控制

創建由物件託管的`COleControlSite`ActiveX 控制件。

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
指向表示控制項的視窗物件的指標。

*Clsid*<br/>
控制項的唯一類別 ID。

*lpsz 視窗名稱*<br/>
指向要在控制項中顯示的文本的指標。 設定 winodw 的標題或文本屬性(如果有)的值。

*dwStyle*<br/>
視窗樣式。 可用樣式列在 **「備註」** 部分下。

*矩形*<br/>
指定控制項的大小和位置。 它可以是`CRect`對`RECT`象或結構。

*nID*<br/>
指定控制項的子視窗 ID。

*p 堅持*<br/>
指向`CFile`包含控制的持久狀態的指標。 默認值為 NULL,指示控制項在不從任何持久儲存還原其狀態的情況下初始化自身。 如果不是 NULL,它應該是指向包含控制項持久資料`CFile`的 派生物件的指標,其形式是流或存儲。 此數據可能已保存在用戶端的上次啟動中。 `CFile`可以包含其他數據,但必須將其讀寫指標設置為調用`CreateControl`時持久性數據的第一個字節。

*b 儲存*<br/>
指示是否應將*pPersist*中的數據`IStorage`解釋`IStream`為 或數據。 如果*pPersist*中的數據是儲存,*則 b 儲存*應為 TRUE。 如果*pPersist*中的數據是流,*則 b 儲存*應為 FALSE。 預設值為 FALSE。

*bstrLicKey*<br/>
可選的許可證金鑰資料。 僅創建需要運行時許可證密鑰的控制項才需要此資料。 如果控制項支援許可,則必須提供許可證金鑰才能成功建立控制項。 預設值是 NULL。

*Ppt*<br/>
指向包含控制項左`POINT`上角的結構的指標。 控制項大小由*size*的值決定。 *ppt*和*size 值*是指定控制項的大小和位置的選擇方法。

*psize*<br/>
指向包含控制大小的`SIZE`結構的指標。 左上角由*ppt*的值決定。 *ppt*和*size 值*是指定控制項的大小和位置的選擇方法。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

只有 Windows *dwStyle*標誌的`CreateControl`子集受 支援:

- WS_VISIBLE 創建最初可見的視窗。 如果希望控件立即可見(如普通視窗),則需要。

- WS_DISABLED 創建最初禁用的視窗。 禁用的視窗無法接收使用者輸入。 如果控件具有"已啟用"屬性,則可以進行設置。

- WS_BORDER 創建具有細線邊框的視窗。 如果控件具有 BorderStyle 屬性,則可以進行設置。

- WS_GROUP 指定一組控制件的第一個控制項。 用戶可以使用方向鍵將鍵盤焦點從組中的一個控制項更改為下一個控制項。 在第一個控制項之後使用WS_GROUP樣式定義的所有控制項都屬於同一組。 具有WS_GROUP樣式的下一個控制項將結束組並啟動下一個組。

- WS_TABSTOP 指定可在使用者按下 TAB 鍵時接收鍵盤焦點的控制項。 按下 TAB 鍵會將鍵盤焦點更改為WS_TABSTOP樣式的下一個控制項。

使用第二個重載創建預設大小的控制項。

## <a name="colecontrolsitedestroycontrol"></a><a name="destroycontrol"></a>COleControlSite::D控制

銷毀`COleControlSite`物件。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

完成後,對象將從記憶體中釋放,並且指向該物件的任何指標都不再有效。

## <a name="colecontrolsitedoverb"></a><a name="doverb"></a>COleControlSite::DoVerb

執行指定的謂詞。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>參數

*nVerb*<br/>
指定要執行的謂詞。 它可以包括以下之一:

|值|意義|符號|
|-----------|-------------|------------|
|0|主動詞命令|OLEIVERB_PRIMARY|
|-1|次要動詞|(無)|
|1|顯示要編輯的物件。|OLEIVERB_SHOW|
|-2|在單獨的視窗中編輯專案。|OLEIVERB_OPEN|
|-3|隱藏物件。|OLEIVERB_HIDE|
|-4|就地啟動控制件。|OLEIVERB_UIACTIVATE|
|-5|就地啟動控制件,而無需其他用戶介面元素。|OLEIVERB_INPLACEACTIVATE|
|-7|顯示控件的屬性。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
指向導致專案被啟動的消息的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

此函數直接通過控件的`IOleObject`介面調用以執行指定的謂詞。 如果由於此函數調用而引發異常,則返回 HRESULT 錯誤代碼。

有關詳細資訊,請參閱 Windows SDK 中的[IOleObject::DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

## <a name="colecontrolsiteenabledsc"></a><a name="enabledsc"></a>COle 控制網站:啟用DSC

支援控制網站的數據源。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>備註

由框架調用,以啟用和初始化控制網站的數據來源。 重寫此函數以提供自定義行為。

## <a name="colecontrolsiteenablewindow"></a><a name="enablewindow"></a>COle 控制網站開啟視窗

啟用或禁用滑鼠和鍵盤輸入到控制網站。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
指定是啟用還是禁用視窗:如果要啟用視窗輸入,則為 TRUE,否則為 FALSE。

### <a name="return-value"></a>傳回值

如果視窗以前已禁用,則非零,否則為 0。

## <a name="colecontrolsitefreezeevents"></a><a name="freezeevents"></a>COle 控制網站:凍結事件

指定控制站點是處理還是忽略從控制項觸發的事件。

```cpp
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>參數

*bFreeze*<br/>
指定控制項站台是否想要停止接受事件。 如果控件不接受事件,則非零;否則為零。

### <a name="remarks"></a>備註

如果*bFreeze*為 TRUE,則控制網站請求控制項停止 fring 事件。 如果*bFreeze*為 FALSE,則控制網站請求控制件繼續觸發事件。

> [!NOTE]
> 如果控制網站請求,則不需要該控件停止觸發事件。 它可以繼續觸發,但控制網站將忽略所有後續事件。

## <a name="colecontrolsitegetcontrolinfo"></a><a name="getcontrolinfo"></a>COle 控制網站:取得控制資訊

檢索有關控件的鍵盤助記符和鍵盤行為的資訊。

```cpp
void GetControlInfo();
```

### <a name="remarks"></a>備註

資訊儲存在[COleControlSite::m_ctlInfo](#m_ctlinfo)。

## <a name="colecontrolsitegetdefbtncode"></a><a name="getdefbtncode"></a>COle 控制網站:取得DefBtn代碼

確定控制項是否為預設按鈕。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>傳回值

可以是下列其中一個值：

- DLGC_DEFPUSHBUTTON控制項是對話框中的預設按鈕。

- DLGC_UNDEFPUSHBUTTON控制項不是對話框中的預設按鈕。

- **0**控制項不是按鈕。

## <a name="colecontrolsitegetdlgctrlid"></a><a name="getdlgctrlid"></a>COle 控制網站:取得DlgCtrlID

檢索控件的標識碼。

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>傳回值

控制項的對話方塊項識別碼。

## <a name="colecontrolsitegeteventiid"></a><a name="geteventiid"></a>COle 控制網站:取得事件Id

檢索指向控制項的預設事件介面的指標。

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>參數

*皮伊德*<br/>
指向介面 ID 的指標。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。 如果成功 *,piid*包含控制項的預設事件介面的介面 ID。

## <a name="colecontrolsitegetexstyle"></a><a name="getexstyle"></a>COle 控制網站:取得樣式

檢索窗口的擴展樣式。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>傳回值

控制項視窗的擴充樣式。

### <a name="remarks"></a>備註

要檢查一般樣式,請致電[COleControlSite::getStyle](#getstyle)。

## <a name="colecontrolsitegetproperty"></a><a name="getproperty"></a>COle 控制網站:取得財產

獲取*dwDispID*指定的控制項屬性。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
標識要檢索的控制項預設`IDispatch`介面上找到的屬性的調度 ID。

*vtProp*<br/>
指定要檢索的屬性的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvProp*<br/>
將接收屬性值的變數的位址。 它必須匹配*vtProp*指定的類型。

### <a name="remarks"></a>備註

該值通過*pvProp*返回。

## <a name="colecontrolsitegetstyle"></a><a name="getstyle"></a>COle 控制網站:取得樣式

檢索控件網站的樣式。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>傳回值

視窗的樣式。

### <a name="remarks"></a>備註

有關可能值的清單,請參閱[Windows 樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 要檢索控制元件站台的擴充樣式,請致電[COleControlSite::GetExStyle](#getexstyle)。

## <a name="colecontrolsitegetwindowtext"></a><a name="getwindowtext"></a>COle 控制網站:抓取視窗文字

檢索控件的當前文本。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>參數

*Str*<br/>
對包含控制項當前`CString`文字的物件的引用。

### <a name="remarks"></a>備註

如果控件支援標題股票屬性,則返回此值。 如果不支援"標題"股票屬性,則返回 Text 屬性的值。

## <a name="colecontrolsiteinvokehelper"></a><a name="invokehelper"></a>COle 控制網站::呼叫説明者

在*wFlags*指定的上下文中呼叫*dwDispID*指定的方法或屬性。

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
標識要調用的屬性或方法的`IDispatch`調度 ID。

*wFlags*<br/>
描述要呼叫 IDispatch::Invoke 時之內容的旗標。 有關可能的*wFlags*值`IDispatch::Invoke`,請參閱 Windows SDK。

*弗特雷特*<br/>
指定傳回值的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須與*vtRet*指定的類型匹配。

*pbParamInfo*<br/>
指向 null 連接端的位元串的指標,指定*pbParamInfo*之後的參數類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
參數的變數清單,在*pbParamInfo*中指定的類型。

### <a name="remarks"></a>備註

*pbParamInfo*參數指定傳遞給方法或屬性的參數的類型。 引數的變數清單會以 ... 語法宣告代表。

此函數將參數轉換為 VARIANTARG 值,然後在控制項`IDispatch::Invoke`上調用 方法。 若呼叫 `IDispatch::Invoke` 失敗，此函式會擲回例外狀況。 `IDispatch::Invoke`行程代碼為`DISP_E_EXCEPTION`,則此函數`COleDispatchException`會引發一個物件,`COleException`否則將引發 。

## <a name="colecontrolsiteinvokehelperv"></a><a name="invokehelperv"></a>COle 控制網站::呼叫説明者V

在*wFlags*指定的上下文中呼叫*dwDispID*指定的方法或屬性。

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
標識要調用的屬性或方法的`IDispatch`調度 ID。

*wFlags*<br/>
描述要呼叫 IDispatch::Invoke 時之內容的旗標。

*弗特雷特*<br/>
指定傳回值的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*pvRet*<br/>
要接收屬性值或傳回值之變數的位址。 它必須與*vtRet*指定的類型匹配。

*pbParamInfo*<br/>
指向 null 連接端的位元串的指標,指定*pbParamInfo*之後的參數類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*阿格列斯*<br/>
指向變數參數清單的指標。

### <a name="remarks"></a>備註

*pbParamInfo*參數指定傳遞給方法或屬性的參數的類型。 可以使用*va_list*參數傳遞所調用的方法或屬性的額外參數。

通常,此函數由 呼`COleControlSite::InvokeHelper`叫 。

## <a name="colecontrolsiteisdefaultbutton"></a><a name="isdefaultbutton"></a>COle 控制網站:預設按鈕

確定控制項是否為預設按鈕。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>傳回值

如果控件是視窗上的預設按鈕,則為非零,否則為零。

## <a name="colecontrolsiteiswindowenabled"></a><a name="iswindowenabled"></a>COle 控制網站開啟視窗

確定控制網站是否啟用。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>傳回值

如果啟用了控件,則為非零,否則為零。

### <a name="remarks"></a>備註

該值將從控制項的「已啟用」股票屬性中檢索。

## <a name="colecontrolsitem_biswindowless"></a><a name="m_biswindowless"></a>COle 控制網站:m_bIsWindowless

確定物件是否為無視窗控制項。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>備註

如果控件沒有視窗,則非零,否則為零。

## <a name="colecontrolsitem_ctlinfo"></a><a name="m_ctlinfo"></a>COle 控制網站:m_ctlInfo

有關控件如何處理鍵盤輸入的資訊。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>備註

此資訊存儲在[CONTROLINFO](/windows/win32/api/ocidl/ns-ocidl-controlinfo)結構中。

## <a name="colecontrolsitem_dweventsink"></a><a name="m_dweventsink"></a>COle 控制網站:m_dwEventSink

包含來自控制項事件接收器的連接點的 Cookie。

```
DWORD m_dwEventSink;
```

## <a name="colecontrolsitem_dwmiscstatus"></a><a name="m_dwmiscstatus"></a>COle 控制網站:m_dwMiscStatus

包含有關控制項的雜項資訊。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[OLEMISC。](/windows/win32/api/oleidl/ne-oleidl-olemisc)

## <a name="colecontrolsitem_dwpropnotifysink"></a><a name="m_dwpropnotifysink"></a>COle 控制網站:m_dwPropNotifySink

包含[IProperty Notify Sink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) Cookie。

```
DWORD m_dwPropNotifySink;
```

## <a name="colecontrolsitem_dwstyle"></a><a name="m_dwstyle"></a>COle 控制網站:m_dwStyle

包含控制項的視窗樣式。

```
DWORD m_dwStyle;
```

## <a name="colecontrolsitem_hwnd"></a><a name="m_hwnd"></a>COle 控制網站:m_hWnd

包含控制項的 HWND,如果控制項沒有視窗,則包含 NULL。

```
HWND m_hWnd;
```

## <a name="colecontrolsitem_iidevents"></a><a name="m_iidevents"></a>COle 控制網站:m_iidEvents

包含控制項的預設事件接收器介面的介面 ID。

```
IID m_iidEvents;
```

## <a name="colecontrolsitem_nid"></a><a name="m_nid"></a>COle 控制網站:m_nID

包含控制項的對話方塊項 ID。

```
UINT m_nID;
```

## <a name="colecontrolsitem_pactiveobject"></a><a name="m_pactiveobject"></a>COle 控制網站:m_pActiveObject

包含控制項的[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)介面。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

## <a name="colecontrolsitem_pctrlcont"></a><a name="m_pctrlcont"></a>COle 控制網站:m_pCtrlCont

包含控制的容器(表示表單)。

```
COleControlContainer* m_pCtrlCont;
```

## <a name="colecontrolsitem_pinplaceobject"></a><a name="m_pinplaceobject"></a>COle 控制網站:m_pInPlaceObject

包含控制項的`IOleInPlaceObject` [IOleInPlace 物件](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)介面。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

## <a name="colecontrolsitem_pobject"></a><a name="m_pobject"></a>COle 控制網站:m_pObject

包含控制`IOleObjectInterface`的介面。

```
LPOLEOBJECT m_pObject;
```

## <a name="colecontrolsitem_pwindowlessobject"></a><a name="m_pwindowlessobject"></a>COle 控制網站:m_pWindowlessObject

包含控制項的`IOleInPlaceObjectWindowless` [IOleInPlace 無視窗](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)介面。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

## <a name="colecontrolsitem_pwndctrl"></a><a name="m_pwndctrl"></a>COle 控制網站:m_pWndCtrl

包含指向表示控件本身`CWnd`的對象的指標。

```
CWnd* m_pWndCtrl;
```

## <a name="colecontrolsitem_rect"></a><a name="m_rect"></a>COle控制網站::m_rect

包含控制件相對於容器視窗的邊界。

```
CRect m_rect;
```

## <a name="colecontrolsitemodifystyle"></a><a name="modifystyle"></a>COle 控制網站:修改樣式

修改控件的樣式。

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*dwRemove*<br/>
要從當前視窗樣式中刪除的樣式。

*dwAdd*<br/>
要從當前視窗樣式添加的樣式。

*nFlags*<br/>
視窗定位標誌。 有關可能值的清單,請參閱 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函數。

### <a name="return-value"></a>傳回值

如果樣式已更改,則非零,否則為零。

### <a name="remarks"></a>備註

控制件的「已啟用」屬性將修改以匹配WS_DISABLED設定。 控制件的庫存邊框樣式屬性將修改以匹配 WS_BORDER請求的設置。 所有其他樣式將直接應用於控制項的視窗句柄(如果存在)。

修改控制項的視窗樣式。 要添加或刪除的樣式可以使用位或 ( &#124; ) 運算子進行組合。 有關可用視窗樣式的資訊,請參閱 Windows SDK 中的[「創建視窗](/windows/win32/api/winuser/nf-winuser-createwindoww)」功能。

如果*nFlags*是`ModifyStyle`非零 ,請呼叫 Win32 函數`SetWindowPos`,並透過*nFlags*與以下四個標誌組合來重繪視窗:

- SWP_NOSIZE 保留當前大小。

- SWP_NOMOVE 保留當前位置。

- SWP_NOZORDER保留當前 Z 訂單。

- SWP_NOACTIVATE不激活視窗。

要修改視窗的延伸樣式,請呼叫[ModifyStyleEx](#modifystyleex)。

## <a name="colecontrolsitemodifystyleex"></a><a name="modifystyleex"></a>COle 控制網站:修改樣式

修改控件的擴展樣式。

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>參數

*dwRemove*<br/>
要從當前視窗樣式中刪除的擴展樣式。

*dwAdd*<br/>
要從當前視窗樣式添加的擴展樣式。

*nFlags*<br/>
視窗定位標誌。 有關可能值的清單,請參閱 Windows SDK 中的[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)函數。

### <a name="return-value"></a>傳回值

如果樣式已更改,則非零,否則為零。

### <a name="remarks"></a>備註

控制項「外觀」屬性將修改以匹配WS_EX_CLIENTEDGE設定。 所有其他擴展視窗樣式將直接應用於控制項的視窗句柄(如果存在)。

修改控制項點物件的視窗擴展樣式。 要添加或刪除的樣式可以使用位或 ( &#124; ) 運算子進行組合。 有關可用視窗樣式的資訊,請參閱 Windows SDK 中的[「創建視窗Ex」](/windows/win32/api/winuser/nf-winuser-createwindowexw)功能。

如果*nFlags*是`ModifyStyleEx`非零 ,請呼叫 Win32 函數`SetWindowPos`,並透過*nFlags*與以下四個標誌組合來重繪視窗:

- SWP_NOSIZE 保留當前大小。

- SWP_NOMOVE 保留當前位置。

- SWP_NOZORDER保留當前 Z 訂單。

- SWP_NOACTIVATE不激活視窗。

要修改視窗的擴展樣式,請調用["修改樣式](#modifystyle)"。

## <a name="colecontrolsitemovewindow"></a><a name="movewindow"></a>COle 控制網站:移動視窗

更改控制項的位置。

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

*Y*<br/>
視窗頂部的新位置。

*n 寬度*<br/>
視窗的新寬度

*nHeight*<br/>
視窗的新高度。

## <a name="colecontrolsitequickactivate"></a><a name="quickactivate"></a>COle 控制網站:快速啟動

快速啟動包含的控制件。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>傳回值

如果控制網站已啟動,則非零,否則為零。

### <a name="remarks"></a>備註

僅當使用者重寫控件的創建過程時,才應調用此函數。

發生`IPersist*::Load``IPersist*::InitNew`快速 啟動后應調用 和 方法。 在快速啟動期間,控件應建立與容器接收器的連接。 但是,這些連接在調用或`IPersist*::Load``IPersist*::InitNew`被調用之前不會活。

## <a name="colecontrolsitesafesetproperty"></a><a name="safesetproperty"></a>COle 控制網站:安全設定屬性

設置*dwDispID*指定的控制項屬性。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
標識要設置的屬性或方法的調度 ID,該 ID`IDispatch`位於控制項的介面上。

*vtProp*<br/>
指定要設置的屬性的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
*vtProp*指定的類型的單個參數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果`SetProperty``SetPropertyV`遇到錯誤(例如嘗試設定不存在的屬性),則與 和不同,則不引發異常。

## <a name="colecontrolsitesetdefaultbutton"></a><a name="setdefaultbutton"></a>COle 控制網站:設定預設按鈕

將控制項設定為預設按鈕。

```cpp
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>參數

*b預設*<br/>
如果控件應成為默認按鈕,則非零;否則為零。

### <a name="remarks"></a>備註

> [!NOTE]
> 控件必須設置OLEMISC_ACTSLIKEBUTTON狀態位。

## <a name="colecontrolsitesetdlgctrlid"></a><a name="setdlgctrlid"></a>COle 控制網站:SetDlgCtrlID

更改控制項的對話方塊項識別碼的值。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
新的標識碼。

### <a name="return-value"></a>傳回值

如果成功,視窗的上一個對話框項標識符;如果成功,則視窗的上一個對話框項標識符。否則 0。

### <a name="remarks"></a>備註

## <a name="colecontrolsitesetfocus"></a><a name="setfocus"></a>COle 控制網站:設定焦點

將焦點設置到控制項。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>參數

*lpmsg*<br/>
指向[MSG 結構](/windows/win32/api/winuser/ns-winuser-msg)的指標。 此結構包含觸發目前控制件站點中包含的控制項`SetFocus`請求的 Windows 訊息。

### <a name="return-value"></a>傳回值

指向以前具有焦點的視窗的指標。

## <a name="colecontrolsitesetproperty"></a><a name="setproperty"></a>COle 控制網站:設定屬性

設置*dwDispID*指定的控制項屬性。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
標識要設置的屬性或方法的調度 ID,該 ID`IDispatch`位於控制項的介面上。

*vtProp*<br/>
指定要設置的屬性的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*...*<br/>
*vtProp*指定的類型的單個參數。

### <a name="remarks"></a>備註

如果`SetProperty`遇到錯誤,將引發異常。

異常的類型由嘗試設置屬性或方法的返回值確定。 如果傳回值`DISP_E_EXCEPTION`為`COleDispatchExcpetion`, 則引發否則為`COleException`。

## <a name="colecontrolsitesetpropertyv"></a><a name="setpropertyv"></a>COle 控制網站:SetPropertyV

設置*dwDispID*指定的控制項屬性。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>參數

*dwDispID*<br/>
標識要設置的屬性或方法的調度 ID,該 ID`IDispatch`位於控制項的介面上。

*vtProp*<br/>
指定要設置的屬性的類型。 如需可能的值，請參閱 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)的＜備註＞一節。

*阿格列斯*<br/>
引數清單的指標。

### <a name="remarks"></a>備註

可以使用*arg_list*參數傳遞所調用的方法或屬性的額外參數。 如果`SetProperty`遇到錯誤,將引發異常。

異常的類型由嘗試設置屬性或方法的返回值確定。 如果傳回值`DISP_E_EXCEPTION`為`COleDispatchExcpetion`, 則引發否則為`COleException`。

## <a name="colecontrolsitesetwindowpos"></a><a name="setwindowpos"></a>COle 控制網站:設定視窗位置

設置控制站點的大小、位置和 Z 順序。

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

*pWndInsert 後*<br/>
指向視窗的指標。

*x*<br/>
視窗左側的新位置。

*Y*<br/>
視窗頂部的新位置。

*殘雪*<br/>
視窗的新寬度

*cy*<br/>
視窗的新高度。

*nFlags*<br/>
指定視窗大小調整和定位標誌。 有關可能的值,請參閱 Windows SDK 中[「設定視窗Pos」](/windows/win32/api/winuser/nf-winuser-setwindowpos)的備註部分。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為零。

## <a name="colecontrolsitesetwindowtext"></a><a name="setwindowtext"></a>COle 控制網站:設定視窗文字

設定控制站點的文字。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
指向要用作新標題或控制項文字的 null 終止字串的指標。

### <a name="remarks"></a>備註

此函數首先嘗試設置標題股票屬性。 如果不支援"標題"股票屬性,則改為設置 Text 屬性。

## <a name="colecontrolsiteshowwindow"></a><a name="showwindow"></a>COle 控制網站:顯示視窗

設置視窗的顯示狀態。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>參數

*nCmdShow*<br/>
指定如何顯示控制件網站。 它必須是以下值之一:

- SW_HIDE隱藏此視窗並將啟動傳遞到另一個視窗。

- SW_MINIMIZE最小化視窗並啟動系統清單中的頂級視窗。

- SW_RESTORE啟動並顯示視窗。 如果視窗最小化或最大化,Windows 會將其還原到其原始大小和位置。

- SW_SHOW啟動視窗,並將其以當前大小和位置顯示。

- SW_SHOWMAXIMIZED啟動視窗並將其顯示為最大化視窗。

- SW_SHOWMINIMIZED啟動視窗並將其顯示為圖示。

- SW_SHOWMINNOACTIVE將窗口顯示為圖示。 當前處於活動狀態的視窗保持活動狀態。

- SW_SHOWNA 顯示視窗當前狀態。 當前處於活動狀態的視窗保持活動狀態。

- SW_SHOWNOACTIVATE 以最新的大小和位置顯示視窗。 當前處於活動狀態的視窗保持活動狀態。

- SW_SHOWNORMAL 啟動並顯示視窗。 如果視窗最小化或最大化,Windows 會將其還原到其原始大小和位置。

### <a name="return-value"></a>傳回值

如果視窗以前可見,則非零;如果視窗以前已隱藏,則為 0。

## <a name="see-also"></a>另請參閱

[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer 類別](../../mfc/reference/colecontrolcontainer-class.md)
