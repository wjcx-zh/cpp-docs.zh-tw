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
ms.openlocfilehash: 57ea8f3a1dbbce4fcfa350bd99e4ee628e9675c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375690"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog 類別

用於建立使用 HTML 而不是對話方塊資源來實現其使用者介面的對話方塊。

## <a name="syntax"></a>語法

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDHtml對話::CDHtml對話](#cdhtmldialog)|建構 CDHtmlDialog 物件。|
|[CDHtml對話::_CDHtml對話](#_dtorcdhtmldialog)|銷毀 CDHtmlDialog 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDHtml對話::可以存取外部](#canaccessexternal)|可重寫,稱為訪問檢查,以查看載入頁上的腳本物件是否可以存取控制項網站的外部調度。 檢查以確保派單對腳本安全,或者當前區域允許對腳本不安全的物件。|
|[CDHtml對話:建立控制網站](#createcontrolsite)|用於創建控制項站台實例以在對話框上承載 WebBrowser 控制項的可重寫操作。|
|[CDHtml對話::DDX_DHtml_Ax控制](#ddx_dhtml_axcontrol)|在 HTML 頁上的成員變數和 ActiveX 控制件的屬性值之間交換數據。|
|[CDHtml對話::DDX_DHtml_複選框](#ddx_dhtml_checkbox)|在 HTML 頁上的成員變數和複選框之間交換數據。|
|[CDHtml對話::DDX_DHtml_元素文字](#ddx_dhtml_elementtext)|在成員變數和 HTML 頁上的任何 HTML 元素屬性之間交換數據。|
|[CDHtml對話::DDX_DHtml_收音機](#ddx_dhtml_radio)|在 HTML 頁上的成員變數和單選按鈕之間交換數據。|
|[CDHtml對話::DDX_DHtml_選擇索引](#ddx_dhtml_selectindex)|獲取或設定 HTML 頁上的清單框的索引。|
|[CDHtml對話::DDX_DHtml_選擇字串](#ddx_dhtml_selectstring)|獲取或設定 HTML 頁上列表框條目的顯示文字(基於當前索引)。|
|[CDHtml對話::DDX_DHtml_選擇值](#ddx_dhtml_selectvalue)|獲取或設定 HTML 頁上的清單方塊條目的值(基於當前索引)。|
|[CDHtmlDialog::D無摩模式](#destroymodeless)|銷毀無模式對話方塊。|
|[CDHtmlDialog:啟用無模式](#enablemodeless)|啟用無模式對話方塊。|
|[CDHtml對話::篩選資料物件](#filterdataobject)|允許對話框篩選託管瀏覽器創建的剪貼簿數據物件。|
|[CDHtmlDialog:取得控制排程](#getcontroldispatch)|檢索`IDispatch`HTML 文件中嵌入的 ActiveX 控制元件上的介面。|
|[CDHtml對話:取得控制屬性](#getcontrolproperty)|檢索指定的 ActiveX 控制件的請求屬性。|
|[CDHtml對話:取得目前網址](#getcurrenturl)|檢索與當前文件關聯的統一資源定位器 (URL)。|
|[CDHtml對話:取得 Html 文件](#getdhtmldocument)|檢索目前載入的 HTML 文件上的 IHTMLDocument2 介面。|
|[CDHtml對話::抓取刪除目標](#getdroptarget)|當包含的 WebBrowser 控制件用作放置目標以允許對話方塊提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)時,由它調用它。|
|[CDHtml對話:抓取元素](#getelement)|取得 HTML 元素上的介面。|
|[CDHtml對話:取得元素Html](#getelementhtml)|檢索`innerHTML`HTML 元素的屬性。|
|[CDHtml對話:抓取元素介面](#getelementinterface)|從 HTML 元素檢索請求的介面指標。|
|[CDHtml對話:抓取元素屬性](#getelementproperty)|檢索 HTML 元素屬性的值。|
|[CDHtml對話:抓取元素文字](#getelementtext)|檢索`innerText`HTML 元素的屬性。|
|[CDHtml對話:抓取事件](#getevent)|獲取指向`IHTMLEventObj`當前事件物件的指標。|
|[CDHtml對話:抓取外部](#getexternal)|獲取主機的`IDispatch`介面。|
|[CDHtmlDialog:取得Hostinfo](#gethostinfo)|檢索主機的 UI 功能。|
|[CDHtml對話:抓取選項關鍵路徑](#getoptionkeypath)|檢索存儲使用者首選項的註冊表項。|
|[CDHtml對話::隱藏UI](#hideui)|隱藏主機的 UI。|
|[CDHtmlDialog:是外部調度安全](#isexternaldispatchsafe)|指示主機的`IDispatch`介面是否安全編寫腳本。|
|[CDHtml對話::從資源載入](#loadfromresource)|將指定的資源載入 Web 瀏覽器控制項中。|
|[CDHtml對話:導覽](#navigate)|導航到指定的 URL。|
|[CDHtmlDialog::在瀏覽前開啟](#onbeforenavigate)|在觸發導航事件之前由框架調用。|
|[CDHtml對話::在文件完成](#ondocumentcomplete)|由框架呼叫,以便在文件達到READYSTATE_COMPLETE狀態時通知應用程式。|
|[CDHtml對話::在DocWindow啟動](#ondocwindowactivate)|當文檔視窗啟動或停用時,由框架調用。|
|[CDHtmlDialog:在框架視窗啟動](#onframewindowactivate)|當框架視窗啟動或停用時,框架調用。|
|[CDHtmlDialog:onInitDialog](#oninitdialog)|調用以回應WM_INITDIALOG消息。|
|[CDHtml對話::導航完成](#onnavigatecomplete)|導航事件完成後由框架調用。|
|[CDHtml對話:調整邊框大小](#resizeborder)|提醒需要調整邊框空間大小的物件。|
|[CDHtml對話::設定控制屬性](#setcontrolproperty)|將 ActiveX 控制件的屬性設置為新值。|
|[CDHtml對話::設定元素Html](#setelementhtml)|設定`innerHTML`HTML 元素的屬性。|
|[CDHtml對話::設定元素屬性](#setelementproperty)|設定 HTML 元素的屬性。|
|[CDHtml對話::設定元素文字](#setelementtext)|設定`innerText`HTML 元素的屬性。|
|[CDHtml對話::設定外部排程](#setexternaldispatch)|設置主機的`IDispatch`介面。|
|[CDHtml對話::設定主機標誌](#sethostflags)|設置主機的 UI 標誌。|
|[CDHtml對話::顯示內容選單](#showcontextmenu)|在顯示上下文菜單時調用。|
|[CDHtml對話::顯示UI](#showui)|顯示主機的 UI。|
|[CDHtml對話:翻譯加速器](#translateaccelerator)|調用 以處理功能表快捷鍵消息。|
|[CDHtml對話:翻譯網址](#translateurl)|呼叫以修改要載入的網址。|
|[CDHtml對話::更新UI](#updateui)|呼叫 以通知主機命令狀態已更改。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDHtml對話::m_bUseHtmlTitle](#m_busehtmltitle)|指示是否使用 HTML 文件的標題作為對話框標題。|
|[CDHtml對話:m_nHtmlResID](#m_nhtmlresid)|要顯示的 HTML 資源的資源識別碼。|
|[CDHtml對話::m_pBrowserApp](#m_pbrowserapp)|指向 Web 瀏覽器應用程式的指標。|
|[CDHtml對話::m_spHtmlDoc](#m_sphtmldoc)|指向 HTML 文件的指標。|
|[CDHtml對話::m_strCurrentUrl](#m_strcurrenturl)|當前 URL。|
|[CDHtml對話::m_szHtmlResID](#m_szhtmlresid)|HTML 資源 ID 的字串版本。|

## <a name="remarks"></a>備註

`CDHtmlDialog`可以載入要從 HTML 資源或網址顯示的 HTML。

`CDHtmlDialog`還可以使用 HTML 控制件進行資料交換,並處理 HTML 控制項中的事件,例如按鈕單擊。

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

## <a name="requirements"></a>需求

**標題:** afxdhtml.h

## <a name="ddx_dhtml-helper-macros"></a><a name="ddx_dhtml_helper_macros"></a>DDX_DHtml說明宏

DDX_DHtml幫助器巨集允許輕鬆存取 HTML 頁上控制項的常用屬性。

### <a name="data-exchange-macros"></a>資料交換巨集

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|從所選控制件設置或檢索 Value 屬性。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|設置或檢索當前元素的開始和結束標記之間的文本。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|在目前元素的開始和結束標記之間設置或檢索 HTML。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|設置或檢索目標 URL 或錨點。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|設置或檢索目標視窗或框架。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|設置或檢索文件中圖像或視頻剪輯的名稱。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|設置或檢索關聯幀的 URL。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|設置或檢索關聯幀的 URL。|

## <a name="cdhtmldialogcanaccessexternal"></a><a name="canaccessexternal"></a>CDHtml對話::可以存取外部

可重寫,稱為訪問檢查,以查看載入頁上的腳本物件是否可以存取控制項網站的外部調度。 檢查以確保派單對腳本安全,或者當前區域允許對腳本不安全的物件。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="cdhtmldialog"></a>CDHtml對話::CDHtml對話

建構基於資源的動態 HTML 對話方塊。

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

*lpszTemplate 名稱*<br/>
為對話框樣本資源名稱的 null 終止字串。

*什奇雷斯ID*<br/>
為 HTML 資源名稱的 null 終止字串。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件的指標[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

*nHtmlResID*<br/>
包含 HTML 資源的 ID 號。

### <a name="remarks"></a>備註

建構函數的第二種形式通過範本名稱提供對對話方塊資源的訪問。 建構函數的第三種形式通過資源範本的 ID 提供對對話方塊資源的訪問。 通常,ID 以**IDD_** 前綴開頭。

## <a name="cdhtmldialogcdhtmldialog"></a><a name="_dtorcdhtmldialog"></a>CDHtml對話::_CDHtml對話

銷毀 CDHtmlDialog 物件。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>備註

必須使用[CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)成員函數來銷毀由[CDialog:::create](../../mfc/reference/cdialog-class.md#create)創建的無模式對話方塊。

## <a name="cdhtmldialogcreatecontrolsite"></a><a name="createcontrolsite"></a>CDHtml對話:建立控制網站

用於創建控制項站台實例以在對話框上承載 WebBrowser 控制項的可重寫操作。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>參數

*pContainer*<br/>
指向[COleControl 容器](../../mfc/reference/colecontrolcontainer-class.md)物件的指標

*ppSite*<br/>
指向[指向 COleControlSite](../../mfc/reference/colecontrolsite-class.md)的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以重寫此成員函數以返回您自己的控制件網站類的實例。

## <a name="cdhtmldialogddx_dhtml_axcontrol"></a><a name="ddx_dhtml_axcontrol"></a>CDHtml對話::DDX_DHtml_Ax控制

在 HTML 頁上的成員變數和 ActiveX 控制件的屬性值之間交換數據。

```
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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
ActiveX 控制項的 HTML 原始物件標記的 ID 參數的值。

*dispId*<br/>
要與其交換數據的屬性的調度 ID。

*szProp名稱*<br/>
屬性的名稱。

*無 功*<br/>
類型[VARIANT 、 COlevariant](../../mfc/reference/colevariant-class.md)或[CComvariant](../../atl/reference/ccomvariant-class.md)的數據成員,用於保存與 ActiveX 控制件屬換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

## <a name="cdhtmldialogddx_dhtml_checkbox"></a><a name="ddx_dhtml_checkbox"></a>CDHtml對話::DDX_DHtml_複選框

在 HTML 頁上的成員變數和複選框之間交換數據。

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制項的 ID 參數指定的值。

*值*<br/>
要交換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

## <a name="cdhtmldialogddx_dhtml_elementtext"></a><a name="ddx_dhtml_elementtext"></a>CDHtml對話::DDX_DHtml_元素文字

在成員變數和 HTML 頁上的任何 HTML 元素屬性之間交換數據。

```
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
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制項的 ID 參數指定的值。

*dispId*<br/>
要與其交換資料的 HTML 元素的調度 ID。

*值*<br/>
要交換的值。

## <a name="cdhtmldialogddx_dhtml_radio"></a><a name="ddx_dhtml_radio"></a>CDHtml對話::DDX_DHtml_收音機

在 HTML 頁上的成員變數和單選按鈕之間交換數據。

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制項的 ID 參數指定的值。

*值*<br/>
要交換的值。

## <a name="cdhtmldialogddx_dhtml_selectindex"></a><a name="ddx_dhtml_selectindex"></a>CDHtml對話::DDX_DHtml_選擇索引

獲取或設定 HTML 頁上的清單框的索引。

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制`id`的參數指定的值。

*值*<br/>
要交換的值。

## <a name="cdhtmldialogddx_dhtml_selectstring"></a><a name="ddx_dhtml_selectstring"></a>CDHtml對話::DDX_DHtml_選擇字串

獲取或設定 HTML 頁上列表框條目的顯示文字(基於當前索引)。

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制項的 ID 參數指定的值。

*值*<br/>
要交換的值。

## <a name="cdhtmldialogddx_dhtml_selectvalue"></a><a name="ddx_dhtml_selectvalue"></a>CDHtml對話::DDX_DHtml_選擇值

獲取或設定 HTML 頁上的清單方塊條目的值(基於當前索引)。

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>參數

*pDX*<br/>
指向[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件的指標。

*szId*<br/>
為 HTML 控制項的 ID 參數指定的值。

*值*<br/>
要交換的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

## <a name="cdhtmldialogdestroymodeless"></a><a name="destroymodeless"></a>CDHtmlDialog::D無摩模式

從`CDHtmlDialog`物件分離無模式對話框並銷毀該物件。

```
void DestroyModeless();
```

## <a name="cdhtmldialogenablemodeless"></a><a name="enablemodeless"></a>CDHtmlDialog:啟用無模式

啟用無模式對話方塊。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>參數

*f 開啟*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))中的*fenable::* 在 Windows SDK 中啟用無模式。

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::啟用無模式](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)),如 Windows SDK 中所述。

## <a name="cdhtmldialogfilterdataobject"></a><a name="filterdataobject"></a>CDHtml對話::篩選資料物件

允許對話框篩選託管瀏覽器創建的剪貼簿數據物件。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>參數

*Pdo*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))中的*pDO::* 在 Windows SDK 中篩選數據物件。

*普多雷特*<br/>
請參閱 Windows SDK`IDocHostUIHandler::FilterDataObject`中的*ppDORet。*

### <a name="return-value"></a>傳回值

返回S_FALSE。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::篩選數據物件](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\)),如 Windows SDK 中所述。

## <a name="cdhtmldialoggetcontroldispatch"></a><a name="getcontroldispatch"></a>CDHtmlDialog:取得控制排程

檢索嵌入`IDispatch`[GetDHtmlDocument](#getdhtmldocument)傳回的 HTML 文件中的 ActiveX 控制項上的介面。

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>參數

*szId*<br/>
ActiveX 控制項的 HTML ID。

*普迪普*<br/>
如果在`IDispatch`網頁中找到控制項的介面。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

## <a name="cdhtmldialoggetcontrolproperty"></a><a name="getcontrolproperty"></a>CDHtml對話:取得控制屬性

檢索指定的 ActiveX 控制件的請求屬性。

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
ActiveX 控制項的 HTML ID。

*szProp名稱*<br/>
當前使用者預設區域設置中的屬性的名稱。

*pdisp 控制*<br/>
ActiveX 控制件`IDispatch`的指標。

*dispId*<br/>
屬性的調度識別碼。

### <a name="return-value"></a>傳回值

如果找不到控制項或屬性,則包含請求的屬性或空變體的變體。

### <a name="remarks"></a>備註

重載從頂部效率最低到底部效率最高列出。

## <a name="cdhtmldialoggetcurrenturl"></a><a name="getcurrenturl"></a>CDHtml對話:取得目前網址

檢索與當前文件關聯的統一資源定位器 (URL)。

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>參數

*szUrl*<br/>
包含要檢索的 URL 的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

## <a name="cdhtmldialoggetdhtmldocument"></a><a name="getdhtmldocument"></a>CDHtml對話:取得 Html 文件

檢索目前載入的 HTML 文件上的[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))介面。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>參數

* \* \* *指向指向 HTML 文件的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。 如果成功,則返回S_OK。

## <a name="cdhtmldialoggetdroptarget"></a><a name="getdroptarget"></a>CDHtml對話::抓取刪除目標

當包含的 WebBrowser 控制件用作放置目標以允許對話方塊提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)時,由它調用它。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>參數

*pDropTarget*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))中的*pDropTarget::* 在 Windows SDK 中獲取 DropTarget。

*ppDrop目標*<br/>
請參閱 Windows SDK`IDocHostUIHandler::GetDropTarget`中的*ppDropTarget。*

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::getDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="cdhtmldialoggetelement"></a><a name="getelement"></a>CDHtml對話:抓取元素

傳回*szElementId*指定的 HTML 元素上的介面。

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

*普迪普*<br/>
指向`IDispatch`請求的元素或元素集合的指標。

*pbCollection*<br/>
一種 BOOL,指示*ppdisp*表示的對像是單個元素還是元素的集合。

*pphtml元素*<br/>
指向`IHTMLElement`請求的元素的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

如果需要處理具有指定 ID 的多個元素的情況,請使用第一個重載。 可以使用最後一個參數來找出返回的介面指標是指向集合還是單個項。 如果介面指標位於集合上,則可以查詢`IHTMLElementCollection`,並使用其`item`屬性按單位位置引用元素。

如果頁面中有多個具有相同 ID 的元素,則第二個重載將失敗。

## <a name="cdhtmldialoggetelementhtml"></a><a name="getelementhtml"></a>CDHtml對話:取得元素Html

檢索`innerHTML`*szElementId*識別的 HTML 元素的屬性。

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

### <a name="return-value"></a>傳回值

找不到`innerHTML`此元素時,*由 szElementId*或 NULL 識別的 HTML 元素的屬性。

## <a name="cdhtmldialoggetelementinterface"></a><a name="getelementinterface"></a>CDHtml對話:抓取元素介面

從*szElementId*識別的 HTML 元素檢索請求的介面指標。

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

*普夫奧比*<br/>
如果找到元素並且查詢成功,則使用請求的介面指標填充的指標的位址。

*雷菲德*<br/>
請求介面的介面 ID (IID)。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

## <a name="cdhtmldialoggetelementproperty"></a><a name="getelementproperty"></a>CDHtml對話:抓取元素屬性

從*szElementId*識別的 HTML 元素中檢索由*dispId*識別的屬性的值。

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*dispId*<br/>
屬性的調度識別碼。

### <a name="return-value"></a>傳回值

如果找不到屬性或元素,則屬性或空變體的值。

## <a name="cdhtmldialoggetelementtext"></a><a name="getelementtext"></a>CDHtml對話:抓取元素文字

檢索`innerText`*szElementId*識別的 HTML 元素的屬性。

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

### <a name="return-value"></a>傳回值

找不到`innerText`屬性或元素時,由*szElementId*或 NULL 識別的 HTML 元素的屬性。

## <a name="cdhtmldialoggetevent"></a><a name="getevent"></a>CDHtml對話:抓取事件

返回指向`IHTMLEventObj`當前事件物件的指標。

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>參數

*ppEventObj*<br/>
將用介面指標填充的`IHTMLEventObj`指標的位址。

### <a name="return-value"></a>傳回值

標準 HRESULT 值。

### <a name="remarks"></a>備註

只能從 DHTML 事件處理程式中呼叫此函數。

## <a name="cdhtmldialoggetexternal"></a><a name="getexternal"></a>CDHtml對話:抓取外部

獲取主機的`IDispatch`介面。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>參數

*ppDispatch*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))中的*ppDispatch:* 在 Windows SDK 中獲取外部。

### <a name="return-value"></a>傳回值

返回S_OK成功或E_NOTIMPL失敗。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::get 外部](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\)),如 Windows SDK 中所述。

## <a name="cdhtmldialoggethostinfo"></a><a name="gethostinfo"></a>CDHtmlDialog:取得Hostinfo

檢索主機的 UI 功能。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>參數

*pInfo*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))中的*pInfo:* 在 Windows SDK 中獲取 Hostinfo。

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler 的實現::獲取 HostInfo,](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialoggetoptionkeypath"></a><a name="getoptionkeypath"></a>CDHtml對話:抓取選項關鍵路徑

檢索存儲使用者首選項的註冊表項。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>參數

*pchKey*<br/>
請參閱 IDocHostUIHandler 中的*pchKey:* 在 Windows SDK 中[獲取 Option KeyPath。](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))

*dw*<br/>
請參閱 Windows `IDocHostUIHandler::GetOptionKeyPath` SDK 中的*dw。*

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler 的實現::獲取選項KeyPath,](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialoghideui"></a><a name="hideui"></a>CDHtml對話::隱藏UI

隱藏主機的 UI。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::隱藏 UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="cdhtmldialogisexternaldispatchsafe"></a><a name="isexternaldispatchsafe"></a>CDHtmlDialog:是外部調度安全

指示主機的`IDispatch`介面是否安全編寫腳本。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>傳回值

返回 FALSE。

## <a name="cdhtmldialogloadfromresource"></a><a name="loadfromresource"></a>CDHtml對話::從資源載入

在 DHTML 對話方塊中將指定資源載入到 Web 瀏覽器控制元件中。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>參數

*lpsz資源*<br/>
指向包含要載入的資源名稱的字串的指標。

*nRes*<br/>
要載入的資源 ID。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

## <a name="cdhtmldialogm_busehtmltitle"></a><a name="m_busehtmltitle"></a>CDHtml對話::m_bUseHtmlTitle

指示是否使用 HTML 文件的標題作為對話框標題。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>備註

如果 m = bUseHtmlTitle 為 TRUE,則對話方塊標題設定為等於 HTML 文件的標題;如果**m**= **bUseHtmlTitle 為**TRUE,則對話方塊標題設定為等於 HTML 文件的標題。否則,將使用對話框資源中的標題。

## <a name="cdhtmldialogm_nhtmlresid"></a><a name="m_nhtmlresid"></a>CDHtml對話:m_nHtmlResID

要顯示的 HTML 資源的資源識別碼。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

## <a name="cdhtmldialogm_pbrowserapp"></a><a name="m_pbrowserapp"></a>CDHtml對話::m_pBrowserApp

指向 Web 瀏覽器應用程式的指標。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

## <a name="cdhtmldialogm_sphtmldoc"></a><a name="m_sphtmldoc"></a>CDHtml對話::m_spHtmlDoc

指向 HTML 文件的指標。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

## <a name="cdhtmldialogm_strcurrenturl"></a><a name="m_strcurrenturl"></a>CDHtml對話::m_strCurrentUrl

當前 URL。

```
CString m_strCurrentUrl;
```

## <a name="cdhtmldialogm_szhtmlresid"></a><a name="m_szhtmlresid"></a>CDHtml對話::m_szHtmlResID

HTML 資源 ID 的字串版本。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

## <a name="cdhtmldialognavigate"></a><a name="navigate"></a>CDHtml對話:導覽

導航到由*lpszURL*指定的 URL 標識的資源。

```
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
指向包含要定位的 URL 的字串的指標。

*dwFlags*<br/>
變數的標誌,用於指定是將資源添加到歷史記錄清單、是讀取到緩存還是從緩存寫入,以及是否在新視窗中顯示資源。 變數可以是[瀏覽器導航常點](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))枚舉定義的值的組合。

*lpsz目標的名稱*<br/>
指向字串的指標,其中包含要在其中顯示資源的框架的名稱。

*lpszHeaders*<br/>
指向指定要發送到伺服器的 HTTP 標頭的值的指標。 這些標頭將添加到預設的 Internet 資源管理器標頭中。 標頭可以指定伺服器所需的操作、傳遞給伺服器的數據類型或狀態代碼等資訊。 如果 URL 不是 HTTP URL,則忽略此參數。

*lpvPostData*<br/>
指向要隨 HTTP POST 事務發送的數據的指標。 例如,POST 事務用於發送 HTML 表單收集的數據。 如果此參數未指定任何發佈數據,則`Navigate`發出 HTTP GET 事務。 如果 URL 不是 HTTP URL,則忽略此參數。

*德沃斯特數據倫*<br/>
與 HTTP POST 事務一起發送的數據。 例如,POST 事務用於發送 HTML 表單收集的數據。 如果此參數未指定任何發佈數據,則`Navigate`發出 HTTP GET 事務。 如果 URL 不是 HTTP URL,則忽略此參數。

## <a name="cdhtmldialogonbeforenavigate"></a><a name="onbeforenavigate"></a>CDHtmlDialog::在瀏覽前開啟

框架調用,導致在導航發生之前觸發事件。

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
指向包含要導航到的 URL 的字串的指標。

## <a name="cdhtmldialogondocumentcomplete"></a><a name="ondocumentcomplete"></a>CDHtml對話::在文件完成

由框架呼叫,以便在文件達到READYSTATE_COMPLETE狀態時通知應用程式。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
指向包含導航到的 URL 的字串的指標。

## <a name="cdhtmldialogondocwindowactivate"></a><a name="ondocwindowactivate"></a>CDHtml對話::在DocWindow啟動

當文檔視窗啟動或停用時,由框架調用。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>參數

*f 啟動*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))中的*fActivate:* 在 Windows SDK 中啟動 OnDocWindow。

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler 的實現::OnDocWindowActivate,](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))如 Windows SDK 中所述。

## <a name="cdhtmldialogonframewindowactivate"></a><a name="onframewindowactivate"></a>CDHtmlDialog:在框架視窗啟動

當框架視窗啟動或停用時,框架調用。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>參數

*f 啟動*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))中的*fActivate:* 在 Windows SDK 中啟用 FrameWindow。

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler 的實現::在FrameWindow啟動上](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)),如 Windows SDK 中所述。

## <a name="cdhtmldialogoninitdialog"></a><a name="oninitdialog"></a>CDHtmlDialog:onInitDialog

調用以回應WM_INITDIALOG消息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

預設實現返回 TRUE。

### <a name="remarks"></a>備註

此訊息在`Create`期間發送到對話框`CreateIndirect`,`DoModal`或調用,該對話框在顯示對話框之前發生。

如果在初始化對話方塊時需要執行特殊處理,則重寫此成員函數。 在重寫版本中,首先調用基類`OnInitDialog`,但忽略其返回值。 您通常會從重寫的成員函數返回 TRUE。

Windows`OnInitDialog`透過 Microsoft 基礎類庫對話框共有的標準全域對話框過程(而不是透過消息映射)調用該函數,因此不需要此成員函數的消息映射條目。

## <a name="cdhtmldialogonnavigatecomplete"></a><a name="onnavigatecomplete"></a>CDHtml對話::導航完成

導航到指定 URL 後由框架呼叫。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>參數

*pDisp*<br/>
`IDispatch` 物件的指標。

*szUrl*<br/>
指向包含導航到的 URL 的字串的指標。

## <a name="cdhtmldialogresizeborder"></a><a name="resizeborder"></a>CDHtml對話:調整邊框大小

提醒需要調整邊框空間大小的物件。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>參數

*prc邊界*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))中的*prcBorder::* 在 Windows SDK 中調整邊框大小。

*pUI 視窗*<br/>
請參閱 Windows SDK`IDocHostUIHandler::ResizeBorder`中的*pUIWindow。*

*fFrame 視窗*<br/>
請參閱 Windows SDK`IDocHostUIHandler::ResizeBorder`中的*fFrame Window。*

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

## <a name="cdhtmldialogsetcontrolproperty"></a><a name="setcontrolproperty"></a>CDHtml對話::設定控制屬性

將 ActiveX 控制件的屬性設置為新值。

```
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
ActiveX 控制項的 HTML ID。

*dispId*<br/>
要設置的屬性的調度 ID。

*pVar*<br/>
指向包含新屬性值的 VARIANT 的變體的指標。

*pdisp 控制*<br/>
指向 ActiveX 控件`IDispatch`的介面 的指標。

*szProp名稱*<br/>
包含要設定的屬性的名稱的字串。

## <a name="cdhtmldialogsetelementhtml"></a><a name="setelementhtml"></a>CDHtml對話::設定元素Html

設定`innerHTML`HTML 元素的屬性。

```
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

*朋克埃萊姆*<br/>
HTML`IUnknown`元素的指標。

## <a name="cdhtmldialogsetelementproperty"></a><a name="setelementproperty"></a>CDHtml對話::設定元素屬性

設定 HTML 元素的屬性。

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>參數

*szElementId*<br/>
HTML 元素的識別碼。

*dispId*<br/>
要設置的屬性的調度 ID。

*pVar*<br/>
屬性的新值。

## <a name="cdhtmldialogsetelementtext"></a><a name="setelementtext"></a>CDHtml對話::設定元素文字

設定`innerText`HTML 元素的屬性。

```
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

*朋克埃萊姆*<br/>
HTML`IUnknown`元素的指標。

## <a name="cdhtmldialogsetexternaldispatch"></a><a name="setexternaldispatch"></a>CDHtml對話::設定外部排程

設置主機的`IDispatch`介面。

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>參數

*pdisp 外部*<br/>
新`IDispatch`介面。

## <a name="cdhtmldialogsethostflags"></a><a name="sethostflags"></a>CDHtml對話::設定主機標誌

設置主機 UI 標誌。

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
有關可能的值,請參閱 Windows SDK 中的[DOCHOSTUIFLAG。](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\))

## <a name="cdhtmldialogshowcontextmenu"></a><a name="showcontextmenu"></a>CDHtml對話::顯示內容選單

在顯示上下文菜單時調用。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>參數

*dwID*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))中的*dwID:* 在 Windows SDK 中顯示上下文選單。

*Ppt*<br/>
請參考 Windows `IDocHostUIHandler::ShowContextMenu` SDK 中的*分頁*。

*pcmdt 保留*<br/>
請參考 Windows SDK`IDocHostUIHandler::ShowContextMenu`中的*pcmdt 保留*。

*pdisp 保留*<br/>
請參考 Windows SDK`IDocHostUIHandler::ShowContextMenu`中的*pdisp 保留*。

### <a name="return-value"></a>傳回值

返回S_FALSE。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::顯示上下文選單](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)),如 Windows SDK 中所述。

## <a name="cdhtmldialogshowui"></a><a name="showui"></a>CDHtml對話::顯示UI

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
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))中的*dwID::* 在 Windows SDK 中顯示 UI。

*p 活動物件*<br/>
請參考 Windows SDK`IDocHostUIHandler::ShowUI`*中的 d 活動物件*。

*pCommand目標*<br/>
請參閱 Windows SDK`IDocHostUIHandler::ShowUI`中的*pCommandTarget。*

*pFrame*<br/>
請參閱 Windows `IDocHostUIHandler::ShowUI` SDK 中的*pFrame。*

*pDoc*<br/>
請參閱 Windows `IDocHostUIHandler::ShowUI` SDK 中的*pDoc。*

### <a name="return-value"></a>傳回值

返回S_FALSE。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler:::ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="cdhtmldialogtranslateaccelerator"></a><a name="translateaccelerator"></a>CDHtml對話:翻譯加速器

調用 以處理功能表快捷鍵消息。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))中的*lpMsg:Windows* SDK 中的翻譯加速器。

*普吉德集團*<br/>
請參考 Windows SDK`IDocHostUIHandler::TranslateAccelerator`中的*pguidCmd 群組*。

*nCmdID*<br/>
請參閱 Windows SDK`IDocHostUIHandler::TranslateAccelerator`中的*nCmdID。*

### <a name="return-value"></a>傳回值

返回S_FALSE。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::翻譯加速器](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="cdhtmldialogtranslateurl"></a><a name="translateurl"></a>CDHtml對話:翻譯網址

呼叫以修改要載入的網址。

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>參數

*dwTranslate*<br/>
請參閱[IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))中的*dwTranslate:Windows* SDK 中的翻譯 Url。

*普喬林*<br/>
請參閱 Windows SDK`IDocHostUIHandler::TranslateUrl`中的*pchURLIn。*

*ppchURLOut*<br/>
請參閱 Windows SDK`IDocHostUIHandler::TranslateUrl`中的*ppchURLOut。*

### <a name="return-value"></a>傳回值

返回S_FALSE。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::翻譯 Url](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="cdhtmldialogupdateui"></a><a name="updateui"></a>CDHtml對話::更新UI

呼叫 以通知主機命令狀態已更改。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>傳回值

返回E_NOTIMPL。

### <a name="remarks"></a>備註

此成員函數是 CDHtmlDialog 的[IDocHostUIHandler::updateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))的實現,如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 樣品 DHtml 探索](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml 協助程式巨集](#ddx_dhtml_helper_macros)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
