---
title: CDHtmlDialog 類別
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: 9cc01c94357d7aac7fa6fa98127628a60746e1e8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842880"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog 類別

用來建立使用 HTML 而非對話方塊資源的對話方塊，以執行其使用者介面。

## <a name="syntax"></a>語法

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDHtmlDialog：： CDHtmlDialog](#cdhtmldialog)|結構 CDHtmlDialog 物件。|
|[CDHtmlDialog：： ~ CDHtmlDialog](#_dtorcdhtmldialog)|終結 CDHtmlDialog 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDHtmlDialog：： CanAccessExternal](#canaccessexternal)|可覆寫的，稱為存取檢查，以查看載入的頁面上的腳本物件是否可以存取控制網站的外部分派。 檢查以確定分派可以安全地進行腳本處理，或目前的區域允許不安全的物件進行腳本處理。|
|[CDHtmlDialog：： CreateControlSite](#createcontrolsite)|可覆寫，用來建立控制網站實例，以在對話方塊上裝載 WebBrowser 控制項。|
|[CDHtmlDialog：:D DX_DHtml_AxControl](#ddx_dhtml_axcontrol)|在成員變數與 HTML 網頁上 ActiveX 控制項的屬性值之間交換資料。|
|[CDHtmlDialog：:D DX_DHtml_CheckBox](#ddx_dhtml_checkbox)|在成員變數與 HTML 網頁上的核取方塊之間交換資料。|
|[CDHtmlDialog：:D DX_DHtml_ElementText](#ddx_dhtml_elementtext)|在成員變數與 HTML 網頁上的任何 HTML 元素屬性之間交換資料。|
|[CDHtmlDialog：:D DX_DHtml_Radio](#ddx_dhtml_radio)|在成員變數與 HTML 網頁上的選項按鈕之間交換資料。|
|[CDHtmlDialog：:D DX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|取得或設定 HTML 網頁上清單方塊的索引。|
|[CDHtmlDialog：:D DX_DHtml_SelectString](#ddx_dhtml_selectstring)|根據 HTML 網頁上目前的索引) ，取得或設定清單方塊專案 (的顯示文字。|
|[CDHtmlDialog：:D DX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|根據 HTML 網頁上目前的索引) ，取得或設定清單方塊專案 (的值。|
|[CDHtmlDialog：:D estroyModeless](#destroymodeless)|終結非強制回應對話方塊。|
|[CDHtmlDialog：： EnableModeless](#enablemodeless)|啟用非強制回應對話方塊。|
|[CDHtmlDialog：： FilterDataObject](#filterdataobject)|允許對話方塊篩選由託管瀏覽器所建立的剪貼簿資料物件。|
|[CDHtmlDialog：： GetControlDispatch](#getcontroldispatch)|抓取 `IDispatch` HTML 檔案中內嵌的 ActiveX 控制項上的介面。|
|[CDHtmlDialog：： GetControlProperty](#getcontrolproperty)|抓取所指定 ActiveX 控制項的要求屬性。|
|[CDHtmlDialog：： GetCurrentUrl](#getcurrenturl)|抓取與目前檔相關聯 (URL) 的統一資源定位器。|
|[CDHtmlDialog：： GetDHtmlDocument](#getdhtmldocument)|抓取目前載入之 HTML 檔案上的 IHTMLDocument2 介面。|
|[CDHtmlDialog：： GetDropTarget](#getdroptarget)|由包含的 WebBrowser 控制項在當做放置目標使用時呼叫，以允許對話方塊提供替代 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)。|
|[CDHtmlDialog：： GetElement](#getelement)|取得 HTML 元素上的介面。|
|[CDHtmlDialog：： GetElementHtml](#getelementhtml)|抓取 HTML 專案的 `innerHTML` 屬性。|
|[CDHtmlDialog：： GetElementInterface](#getelementinterface)|從 HTML 元素抓取要求的介面指標。|
|[CDHtmlDialog：： GetElementProperty](#getelementproperty)|抓取 HTML 元素之屬性的值。|
|[CDHtmlDialog：： GetElementText](#getelementtext)|抓取 HTML 專案的 `innerText` 屬性。|
|[CDHtmlDialog：： GetEvent](#getevent)|取得 `IHTMLEventObj` 目前事件物件的指標。|
|[CDHtmlDialog：： GetExternal](#getexternal)|取得主機的 `IDispatch` 介面。|
|[CDHtmlDialog：： GetHostInfo](#gethostinfo)|捕獲主機的 UI 功能。|
|[CDHtmlDialog：： GetOptionKeyPath](#getoptionkeypath)|抓取用來儲存使用者喜好設定的登錄機碼。|
|[CDHtmlDialog：： HideUI](#hideui)|隱藏主機的 UI。|
|[CDHtmlDialog：： IsExternalDispatchSafe](#isexternaldispatchsafe)|指出主機的介面是否 `IDispatch` 可以安全地進行腳本處理。|
|[CDHtmlDialog：： LoadFromResource](#loadfromresource)|將指定的資源載入至 WebBrowser 控制項。|
|[CDHtmlDialog：：導覽](#navigate)|流覽至指定的 URL。|
|[CDHtmlDialog：： OnBeforeNavigate](#onbeforenavigate)|在引發導覽事件之前，由架構呼叫。|
|[CDHtmlDialog：： OnDocumentComplete](#ondocumentcomplete)|由架構呼叫，以在檔達到 READYSTATE_COMPLETE 狀態時通知應用程式。|
|[CDHtmlDialog：： OnDocWindowActivate](#ondocwindowactivate)|當文件視窗啟用或停用時，由架構呼叫。|
|[CDHtmlDialog：： OnFrameWindowActivate](#onframewindowactivate)|當框架視窗啟用或停用時，由架構呼叫。|
|[CDHtmlDialog：： OnInitDialog](#oninitdialog)|在回應 WM_INITDIALOG 訊息時呼叫。|
|[CDHtmlDialog：： OnNavigateComplete](#onnavigatecomplete)|在導覽事件完成之後，由架構呼叫。|
|[CDHtmlDialog：： ResizeBorder](#resizeborder)|警示物件，它需要調整框線空間的大小。|
|[CDHtmlDialog：： SetControlProperty](#setcontrolproperty)|將 ActiveX 控制項的屬性設定為新的值。|
|[CDHtmlDialog：： SetElementHtml](#setelementhtml)|設定 HTML 專案的 `innerHTML` 屬性。|
|[CDHtmlDialog：： SetElementProperty](#setelementproperty)|設定 HTML 專案的屬性。|
|[CDHtmlDialog：： SetElementText](#setelementtext)|設定 HTML 專案的 `innerText` 屬性。|
|[CDHtmlDialog：： SetExternalDispatch](#setexternaldispatch)|設定主機的 `IDispatch` 介面。|
|[CDHtmlDialog：： SetHostFlags](#sethostflags)|設定主機的 UI 旗標。|
|[CDHtmlDialog：： ShowCoNtextMenu](#showcontextmenu)|當內容功能表即將顯示時呼叫。|
|[CDHtmlDialog：： >showui 或](#showui)|顯示主機的 UI。|
|[CDHtmlDialog：： TranslateAccelerator](#translateaccelerator)|呼叫以處理功能表快速鍵訊息。|
|[CDHtmlDialog：： TranslateUrl](#translateurl)|呼叫以修改要載入的 URL。|
|[CDHtmlDialog：： UpdateUI](#updateui)|呼叫以通知主機命令狀態已變更。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDHtmlDialog：： m_bUseHtmlTitle](#m_busehtmltitle)|指出是否要使用 HTML 檔案的標題作為對話方塊標題。|
|[CDHtmlDialog：： m_nHtmlResID](#m_nhtmlresid)|要顯示之 HTML 資源的資源識別碼。|
|[CDHtmlDialog：： m_pBrowserApp](#m_pbrowserapp)|Web 瀏覽器應用程式的指標。|
|[CDHtmlDialog：： m_spHtmlDoc](#m_sphtmldoc)|HTML 檔案的指標。|
|[CDHtmlDialog：： m_strCurrentUrl](#m_strcurrenturl)|目前的 URL。|
|[CDHtmlDialog：： m_szHtmlResID](#m_szhtmlresid)|HTML 資源識別碼的字串版本。|

## <a name="remarks"></a>備註

`CDHtmlDialog` 可以載入 HTML 資源或 URL 所顯示的 HTML。

`CDHtmlDialog` 也可以使用 HTML 控制項進行資料交換，以及處理來自 HTML 控制項的事件，例如按一下按鈕。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>規格需求

**標頭：** afxdhtml。h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a> DDX_DHtml Helper 宏

DDX_DHtml helper 宏可讓您輕鬆存取 HTML 網頁上常用的控制項屬性。

### <a name="data-exchange-macros"></a>資料交換宏

|名稱|描述|
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|從選取的控制項設定或抓取 Value 屬性。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|設定或抓取目前專案的開始和結束標記之間的文字。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|設定或抓取目前專案的開始和結束標記之間的 HTML。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|設定或抓取目的地 URL 或錨點。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|設定或抓取目標視窗或框架。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|設定或抓取檔中影像或影片剪輯的名稱。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|設定或抓取相關聯框架的 URL。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|設定或抓取相關聯框架的 URL。|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a> CDHtmlDialog：： CanAccessExternal

可覆寫的，稱為存取檢查，以查看載入的頁面上的腳本物件是否可以存取控制網站的外部分派。 檢查以確定分派可以安全地進行腳本處理，或目前的區域允許不安全的物件進行腳本處理。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a> CDHtmlDialog：： CDHtmlDialog

結構化以資源為基礎的動態 HTML 對話方塊。

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
以 null 終止的字串，這是對話方塊範本資源的名稱。

*szHtmlResID*<br/>
以 null 終止的字串，這是 HTML 資源的名稱。

*pParentWnd*<br/>
指向對話方塊物件所屬之 [CWnd](../../mfc/reference/cwnd-class.md)) 類型的父系或擁有者視窗物件 (指標。 如果是 Null，對話方塊物件的父視窗就會設定為主應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊範本資源的 ID 號碼。

*nHtmlResID*<br/>
包含 HTML 資源的 ID 號碼。

### <a name="remarks"></a>備註

第二種形式的函式可透過範本名稱提供對話資源的存取權。 第三種形式的函式可讓您透過資源範本的識別碼存取對話方塊資源。 通常，識別碼的開頭會是 **IDD_** 前置詞。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a> CDHtmlDialog：： ~ CDHtmlDialog

終結 CDHtmlDialog 物件。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>備註

[CWnd：:D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)成員函數必須用來終結[CDialog：： Create](../../mfc/reference/cdialog-class.md#create)所建立的非強制回應對話方塊。

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a> CDHtmlDialog：： CreateControlSite

可覆寫，用來建立控制網站實例，以在對話方塊上裝載 WebBrowser 控制項。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>參數

*pContainer*<br/>
[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)物件的指標

*ppSite*<br/>
指向 [COleControlSite](../../mfc/reference/colecontrolsite-class.md)指標的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以覆寫這個成員函式，以傳回您自己的控制網站類別的實例。

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a> CDHtmlDialog：:D DX_DHtml_AxControl

在成員變數與 HTML 網頁上 ActiveX 控制項的屬性值之間交換資料。

```cpp
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
ActiveX 控制項 HTML 來源中物件標記識別項參數的值。

*dispId*<br/>
您要用來交換資料之屬性的分派識別碼。

*szPropName*<br/>
屬性的名稱。

*無 功*<br/>
VARIANT、 [COleVariant](../../mfc/reference/colevariant-class.md)或 [CComVariant](../../atl/reference/ccomvariant-class.md)類型的資料成員，其保存與 ActiveX 控制項屬性交換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a> CDHtmlDialog：:D DX_DHtml_CheckBox

在成員變數與 HTML 網頁上的核取方塊之間交換資料。

```cpp
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的 ID 參數所指定的值。

*value*<br/>
正在交換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a> CDHtmlDialog：:D DX_DHtml_ElementText

在成員變數與 HTML 網頁上的任何 HTML 元素屬性之間交換資料。

```cpp
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的 ID 參數所指定的值。

*dispId*<br/>
您要用來交換資料之 HTML 元素的分派識別碼。

*value*<br/>
正在交換的值。

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a> CDHtmlDialog：:D DX_DHtml_Radio

在成員變數與 HTML 網頁上的選項按鈕之間交換資料。

```cpp
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的 ID 參數所指定的值。

*value*<br/>
正在交換的值。

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a> CDHtmlDialog：:D DX_DHtml_SelectIndex

取得或設定 HTML 網頁上清單方塊的索引。

```cpp
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的參數所指定的值 `id` 。

*value*<br/>
正在交換的值。

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a> CDHtmlDialog：:D DX_DHtml_SelectString

根據 HTML 網頁上目前的索引) ，取得或設定清單方塊專案 (的顯示文字。

```cpp
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的 ID 參數所指定的值。

*value*<br/>
正在交換的值。

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a> CDHtmlDialog：:D DX_DHtml_SelectValue

根據 HTML 網頁上目前的索引) ，取得或設定清單方塊專案 (的值。

```cpp
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
您針對 HTML 控制項的 ID 參數所指定的值。

*value*<br/>
正在交換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a> CDHtmlDialog：:D estroyModeless

從物件卸離非強制回應對話方塊 `CDHtmlDialog` ，並終結物件。

```cpp
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a> CDHtmlDialog：： EnableModeless

啟用非強制回應對話方塊。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>參數

*fEnable*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))的*fEnable* 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a> CDHtmlDialog：： FilterDataObject

允許對話方塊篩選由託管瀏覽器所建立的剪貼簿資料物件。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>參數

*Pdo*<br/>
請參閱 Windows SDK 中的 *pDO* in [IDocHostUIHandler：： FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)) 。

*ppDORet*<br/>
請參閱 Windows SDK 中的 *ppDORet* `IDocHostUIHandler::FilterDataObject` 。

### <a name="return-value"></a>傳回值

傳回 S_FALSE。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a> CDHtmlDialog：： GetControlDispatch

`IDispatch`在[GetDHtmlDocument](#getdhtmldocument)所傳回的 HTML 檔案中內嵌的 ActiveX 控制項上，捕獲介面。

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>參數

*szId*<br/>
ActiveX 控制項的 HTML 識別碼。

*ppdisp*<br/>
`IDispatch`如果在網頁中找到，則為控制項的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a> CDHtmlDialog：： GetControlProperty

抓取所指定 ActiveX 控制項的要求屬性。

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>參數

*szId*<br/>
ActiveX 控制項的 HTML 識別碼。

*szPropName*<br/>
目前使用者的預設地區設定中屬性的名稱。

*pdispControl*<br/>
`IDispatch`ActiveX 控制項的指標。

*dispId*<br/>
屬性的分派識別碼。

### <a name="return-value"></a>傳回值

如果找不到控制項或屬性，則為包含所要求屬性的 variant 或空的 variant。

### <a name="remarks"></a>備註

從最高效率到最低的最高效率，會列出多載。

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a> CDHtmlDialog：： GetCurrentUrl

抓取與目前檔相關聯 (URL) 的統一資源定位器。

```cpp
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>參數

*szUrl*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要取出的 URL。

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a> CDHtmlDialog：： GetDHtmlDocument

抓取目前載入之 HTML 檔案上的 [IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) 介面。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>參數

* \* \* pphtmlDoc*指向 HTML 檔案指標的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。 如果成功，則傳回 S_OK。

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a> CDHtmlDialog：： GetDropTarget

由包含的 WebBrowser 控制項在當做放置目標使用時呼叫，以允許對話方塊提供替代 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>參數

*pDropTarget*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))的*pDropTarget* 。

*ppDropTarget*<br/>
請參閱 Windows SDK 中的 *ppDropTarget* `IDocHostUIHandler::GetDropTarget` 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a> CDHtmlDialog：： GetElement

傳回 *szElementId*所指定之 HTML 元素的介面。

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*ppdisp*<br/>
`IDispatch`要求的元素或專案集合的指標。

*pbCollection*<br/>
布林值，指出 *ppdisp* 所代表的物件是單一元素或元素的集合。

*pphtmlElement*<br/>
所 `IHTMLElement` 要求之專案的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果您需要處理可能有一個以上具有指定識別碼之元素的條件，請使用第一個多載。 您可以使用最後一個參數，找出傳回的介面指標是否為集合或單一專案。 如果介面指標位於集合上，您可以查詢， `IHTMLElementCollection` 並使用其 `item` 屬性來依序數位置參考元素。

如果頁面中有一個以上的專案具有相同的識別碼，則第二個多載會失敗。

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a> CDHtmlDialog：： GetElementHtml

抓取 `innerHTML` *szElementId*所識別之 HTML 元素的屬性。

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

### <a name="return-value"></a>傳回值

`innerHTML` *SzElementId*所識別之 HTML 元素的屬性，如果找不到該元素，則為 Null。

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a> CDHtmlDialog：： GetElementInterface

從 *szElementId*所識別的 HTML 元素抓取要求的介面指標。

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*ppvObj*<br/>
如果找到元素且查詢成功，將會填入所要求介面指標的指標位址。

*refiid*<br/>
要求的介面 (IID) 的介面識別碼。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a> CDHtmlDialog：： GetElementProperty

從*szElementId*所識別的 HTML 元素抓取*dispId*所識別之屬性的值。

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*dispId*<br/>
屬性的分派識別碼。

### <a name="return-value"></a>傳回值

如果找不到屬性或專案，則為屬性的值或空的 variant。

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a> CDHtmlDialog：： GetElementText

抓取 `innerText` *szElementId*所識別之 HTML 元素的屬性。

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

### <a name="return-value"></a>傳回值

`innerText` *SzElementId*所識別之 HTML 專案的屬性，如果找不到屬性或元素，則為 Null。

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a> CDHtmlDialog：： GetEvent

傳回 `IHTMLEventObj` 目前事件物件的指標。

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>參數

*ppEventObj*<br/>
將會填入介面指標的指標位址 `IHTMLEventObj` 。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

這個函式應該只在 DHTML 事件處理常式內呼叫。

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a> CDHtmlDialog：： GetExternal

取得主機的 `IDispatch` 介面。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>參數

*ppDispatch*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))的*ppDispatch* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a> CDHtmlDialog：： GetHostInfo

捕獲主機的 UI 功能。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))的*pInfo* 。

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a> CDHtmlDialog：： GetOptionKeyPath

抓取用來儲存使用者喜好設定的登錄機碼。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pchKey*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))的*pchKey* 。

*dw*<br/>
請*dw*參閱 `IDocHostUIHandler::GetOptionKeyPath` Windows SDK 中的 dw。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a> CDHtmlDialog：： HideUI

隱藏主機的 UI。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a> CDHtmlDialog：： IsExternalDispatchSafe

指出主機的介面是否 `IDispatch` 可以安全地進行腳本處理。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>傳回值

傳回 FALSE。

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a> CDHtmlDialog：： LoadFromResource

將指定的資源載入至 DHTML 對話方塊中的 WebBrowser 控制項。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>參數

*lpszResource*<br/>
包含要載入之資源名稱的字串指標。

*nRes*<br/>
要載入的資源 ID。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a> CDHtmlDialog：： m_bUseHtmlTitle

指出是否要使用 HTML 檔案的標題作為對話方塊標題。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>備註

如果 **m**_ **bUseHtmlTitle** 為 TRUE，則會將對話標題設定為等於 HTML 檔案的標題;否則，會使用對話方塊資源中的標題。

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a> CDHtmlDialog：： m_nHtmlResID

要顯示之 HTML 資源的資源識別碼。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a> CDHtmlDialog：： m_pBrowserApp

Web 瀏覽器應用程式的指標。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a> CDHtmlDialog：： m_spHtmlDoc

HTML 檔案的指標。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a> CDHtmlDialog：： m_strCurrentUrl

目前的 URL。

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a> CDHtmlDialog：： m_szHtmlResID

HTML 資源識別碼的字串版本。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a> CDHtmlDialog：：導覽

流覽至 *lpszURL*所指定之 URL 所識別的資源。

```cpp
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
字串的指標，其中包含要設為目標的 URL。

*dwFlags*<br/>
變數的旗標，這個變數會指定是否要將資源加入至歷程記錄清單、是否要讀取快取或從快取寫入，以及是否要在新視窗中顯示資源。 變數可以是 [BrowserNavConstants](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\)) 列舉所定義的值組合。

*lpszTargetFrameName*<br/>
字串的指標，其中包含要在其中顯示資源的框架名稱。

*lpszHeaders*<br/>
值的指標，此值會指定要傳送至伺服器的 HTTP 標頭。 這些標頭會新增至預設的 Internet Explorer 標頭。 標頭可以指定伺服器所需的動作、傳遞至伺服器的資料類型，或狀態碼等資訊。 如果 URL 不是 HTTP URL，則會忽略此參數。

*lpvPostData*<br/>
要與 HTTP POST 交易一起傳送之資料的指標。 例如，POST 交易會用來傳送 HTML 表單所收集的資料。 如果此參數未指定任何 post 資料，則會 `Navigate` 發出 HTTP GET 交易。 如果 URL 不是 HTTP URL，則會忽略此參數。

*dwPostDataLen*<br/>
要與 HTTP POST 交易一起傳送的資料。 例如，POST 交易會用來傳送 HTML 表單所收集的資料。 如果此參數未指定任何 post 資料，則會 `Navigate` 發出 HTTP GET 交易。 如果 URL 不是 HTTP URL，則會忽略此參數。

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a> CDHtmlDialog：： OnBeforeNavigate

由架構呼叫，以在進行導覽之前引發事件。

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
字串的指標，其中包含要流覽的 URL。

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a> CDHtmlDialog：： OnDocumentComplete

由架構呼叫，以在檔達到 READYSTATE_COMPLETE 狀態時通知應用程式。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
字串的指標，其中包含導覽至的 URL。

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a> CDHtmlDialog：： OnDocWindowActivate

當文件視窗啟用或停用時，由架構呼叫。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>參數

*fActivate*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))的*fActivate* 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a> CDHtmlDialog：： OnFrameWindowActivate

當框架視窗啟用或停用時，由架構呼叫。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>參數

*fActivate*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))的*fActivate* 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a> CDHtmlDialog：： OnInitDialog

在回應 WM_INITDIALOG 訊息時呼叫。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

預設的實值會傳回 TRUE。

### <a name="remarks"></a>備註

這則訊息會在、或呼叫期間傳送至對話方塊，此對話方塊會在 `Create` `CreateIndirect` `DoModal` 對話方塊顯示之前出現。

如果您需要在初始化對話方塊時執行特殊處理，請覆寫這個成員函式。 在覆寫的版本中，先呼叫基類， `OnInitDialog` 但忽略其傳回值。 您通常會從覆寫的成員函式傳回 TRUE。

Windows `OnInitDialog` 會透過所有 MFC 程式庫對話方塊通用的標準全域對話方塊程式來呼叫函式，而不是透過訊息對應，因此，您不需要這個成員函式的訊息對應專案。

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a> CDHtmlDialog：： OnNavigateComplete

在流覽至指定的 URL 之後，由架構呼叫。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
字串的指標，其中包含導覽至的 URL。

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a> CDHtmlDialog：： ResizeBorder

警示物件，它需要調整框線空間的大小。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>參數

*prcBorder*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))的*prcBorder* 。

*pUIWindow*<br/>
請參閱 Windows SDK 中的 *pUIWindow* `IDocHostUIHandler::ResizeBorder` 。

*fFrameWindow*<br/>
請參閱 Windows SDK 中的 *fFrameWindow* `IDocHostUIHandler::ResizeBorder` 。

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a> CDHtmlDialog：： SetControlProperty

將 ActiveX 控制項的屬性設定為新的值。

```cpp
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
ActiveX 控制項的 HTML 識別碼。

*dispId*<br/>
要設定之屬性的分派識別碼。

*pVar*<br/>
變數的指標，其中包含新的屬性值。

*pdispControl*<br/>
ActiveX 控制項介面的指標 `IDispatch` 。

*szPropName*<br/>
包含要設定之屬性名稱的字串。

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a> CDHtmlDialog：： SetElementHtml

設定 HTML 專案的 `innerHTML` 屬性。

```cpp
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*bstrText*<br/>
`innerHTML` 屬性的新值。

*punkElem*<br/>
`IUnknown`HTML 元素的指標。

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a> CDHtmlDialog：： SetElementProperty

設定 HTML 專案的屬性。

```cpp
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*dispId*<br/>
要設定之屬性的分派識別碼。

*pVar*<br/>
屬性的新值。

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a> CDHtmlDialog：： SetElementText

設定 HTML 專案的 `innerText` 屬性。

```cpp
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*bstrText*<br/>
`innerText` 屬性的新值。

*punkElem*<br/>
`IUnknown`HTML 元素的指標。

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a> CDHtmlDialog：： SetExternalDispatch

設定主機的 `IDispatch` 介面。

```cpp
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>參數

*pdispExternal*<br/>
新的 `IDispatch` 介面。

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a> CDHtmlDialog：： SetHostFlags

設定主機 UI 旗標。

```cpp
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
如需可能的值，請參閱 Windows SDK 中的 [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) 。

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a> CDHtmlDialog：： ShowCoNtextMenu

當內容功能表即將顯示時呼叫。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>參數

*dwID*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： ShowCoNtextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))的*dwID* 。

*Ppt*<br/>
請*ppt*參閱 `IDocHostUIHandler::ShowContextMenu` Windows SDK 中的 ppt。

*pcmdtReserved*<br/>
請參閱 Windows SDK 中的 *pcmdtReserved* `IDocHostUIHandler::ShowContextMenu` 。

*pdispReserved*<br/>
請參閱 Windows SDK 中的 *pdispReserved* `IDocHostUIHandler::ShowContextMenu` 。

### <a name="return-value"></a>傳回值

傳回 S_FALSE。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： ShowCoNtextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogshowui"></a><a name="showui"></a> CDHtmlDialog：： >showui 或

顯示主機的 UI。

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>參數

*dwID*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： >showui 或](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))的*dwID* 。

*pActiveObject*<br/>
請參閱 Windows SDK 中的 *d pActiveObject* `IDocHostUIHandler::ShowUI` 。

*pCommandTarget*<br/>
請參閱 Windows SDK 中的 *pCommandTarget* `IDocHostUIHandler::ShowUI` 。

*pFrame*<br/>
請參閱 Windows SDK 中的 *pFrame* `IDocHostUIHandler::ShowUI` 。

*Pdoc->*<br/>
請參閱 Windows SDK 中的 *pdoc->* `IDocHostUIHandler::ShowUI` 。

### <a name="return-value"></a>傳回值

傳回 S_FALSE。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： >showui 或](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a> CDHtmlDialog：： TranslateAccelerator

呼叫以處理功能表快速鍵訊息。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))的*lpMsg* 。

*pguidCmdGroup*<br/>
請參閱 Windows SDK 中的 *pguidCmdGroup* `IDocHostUIHandler::TranslateAccelerator` 。

*nCmdID*<br/>
請參閱 Windows SDK 中的 *nCmdID* `IDocHostUIHandler::TranslateAccelerator` 。

### <a name="return-value"></a>傳回值

傳回 S_FALSE。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a> CDHtmlDialog：： TranslateUrl

呼叫以修改要載入的 URL。

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>參數

*dwTranslate*<br/>
請參閱 Windows SDK 中[IDocHostUIHandler：： TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))的*dwTranslate* 。

*pchURLIn*<br/>
請參閱 Windows SDK 中的 *pchURLIn* `IDocHostUIHandler::TranslateUrl` 。

*ppchURLOut*<br/>
請參閱 Windows SDK 中的 *ppchURLOut* `IDocHostUIHandler::TranslateUrl` 。

### <a name="return-value"></a>傳回值

傳回 S_FALSE。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a> CDHtmlDialog：： UpdateUI

呼叫以通知主機命令狀態已變更。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函式是 CDHtmlDialog 的 [IDocHostUIHandler：： UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))的實，如 Windows SDK 所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml Helper 宏](#ddx_dhtml_helper_macros)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
