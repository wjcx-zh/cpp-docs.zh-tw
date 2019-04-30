---
title: CPageSetupDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 01a320fbcd9760bab484f3c75553613852ca9aed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373163"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 類別

封裝 Windows 通用 OLE 版面設定對話方塊所提供的服務，以及設定和修改列印邊界的額外支援。

## <a name="syntax"></a>語法

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|建構 `CPageSetupDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|建立列印裝置內容。|
|[CPageSetupDialog::DoModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|傳回印表機裝置名稱。|
|[CPageSetupDialog::GetDevMode](#getdevmode)|傳回目前的 DEVMODE 的印表機。|
|[CPageSetupDialog::GetDriverName](#getdrivername)|傳回由印表機驅動程式。|
|[CPageSetupDialog::GetMargins](#getmargins)|傳回目前的邊界設定的印表機。|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|傳回印表機的紙張大小。|
|[CPageSetupDialog::GetPortName](#getportname)|傳回的輸出連接埠名稱。|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|由架構呼叫以呈現列印頁面的畫面影像。|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|呈現列印頁面的畫面影像前，由架構呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|結構，用來自訂`CPageSetupDialog`物件。|

## <a name="remarks"></a>備註

此類別被設計來取代 [設定列印格式] 對話方塊。

若要使用`CPageSetupDialog`物件，請先建立物件使用`CPageSetupDialog`建構函式。 一旦建構的對話方塊中，您可以設定或修改中的任何值`m_psd`來初始化對話方塊的控制項值的資料成員。 [M_psd](#m_psd)結構屬於 PAGESETUPDLG 的型別。

在初始化對話方塊的控制項之後, 呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者選取列印選項。 `DoModal` 傳回使用者是否已選取 確定 (IDOK) 或 取消 (IDCANCEL) 按鈕。

如果`DoModal`傳回 IDOK，您可以使用數個`CPageSetupDialog`的成員函式或存取`m_psd`資料成員，來擷取使用者的資訊輸入。

> [!NOTE]
>  通用 OLE 版面設定對話方塊關閉之後，使用者所做的任何變更將不會儲存由架構。 這是由應用程式本身儲存至永久的位置，例如應用程式的文件或應用程式類別的成員的這個對話方塊中任何值。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

呼叫此函式來建構`CPageSetupDialog`物件。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
您可以使用自訂的對話方塊中設定的一或多個標幟。 值，可以使用位元 OR 運算子加以結合。 這些值具有下列意義：

- PSD_DEFAULTMINMARGINS 設定允許，使印表機的最小值與相同的頁面邊界寬度下限。 如果也指定 PSD_MARGINS 和 PSD_MINMARGINS 旗標，則會忽略此旗標。

- PSD_INWININIINTLMEASURE 未實作。

- PSD_MINMARGINS 會導致系統使用中指定的值`rtMinMargin`作為允許的最小寬度，左側、 頂端、 右側，和下方邊界的成員。 系統會防止使用者輸入小於指定的最小寬度。 如果未指定 PSD_MINMARGINS，系統就會設定允許的寬度下限所允許的印表機。

- PSD_MARGINS 啟動邊界控制項區域。

- PSD_INTHOUSANDTHSOFINCHES 會導致單位 對話方塊中的度量單位是英吋的 1/1000 之間。

- PSD_INHUNDREDTHSOFMILLIMETERS 會導致單位 對話方塊中的度量單位是 1/100 公釐。

- PSD_DISABLEMARGINS 停用邊界對話方塊的控制項。

- PSD_DISABLEPRINTER 停用 [印表機] 按鈕。

- PSD_NOWARNING 避免預設的印表機時顯示警告訊息。

- PSD_DISABLEORIENTATION 停用頁面方向對話方塊控制項。

- PSD_RETURNDEFAULT 會導致`CPageSetupDialog`返回[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)並[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)會初始化為系統預設的印表機，而不會顯示一個對話方塊中的結構。 它假設這兩個`hDevNames`和`hDevMode`都為 NULL; 否則函數會傳回錯誤。 如果系統預設的印表機支援舊的印表機驅動程式 （早於 Windows 3.0 版） 只能`hDevNames`傳回;`hDevMode`為 NULL。

- PSD_DISABLEPAPER 停用文件選取範圍控制項。

- PSD_SHOWHELP 會導致對話方塊中，以顯示 [說明] 按鈕。 `hwndOwner`成員不得為 NULL，如果指定此旗標。

- PSD_ENABLEPAGESETUPHOOK 啟用攔截函式中指定`lpfnSetupHook`。

- PSD_ENABLEPAGESETUPTEMPLATE 會造成要建立對話方塊中，使用範本 對話方塊所識別的作業系統`hInstance`和`lpSetupTemplateName`。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE 表示`hInstance`識別包含預先載入的對話方塊範本的資料區塊。 系統會忽略`lpSetupTemplateName`如果指定此旗標。

- PSD_ENABLEPAGEPAINTHOOK 啟用攔截函式中指定`lpfnPagePaintHook`。

- PSD_DISABLEPAGEPAINTING 停用對話方塊中的 [繪製] 的區域。

*pParentWnd*<br/>
至對話方塊的父成員或擁有者的指標。

### <a name="remarks"></a>備註

使用[DoModal](../../mfc/reference/cdialog-class.md#domodal)函式來顯示對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

建立從印表機裝置內容[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)並[DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames)結構。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

新建立的印表機裝置內容 (DC) 的控制代碼。

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

呼叫此函式可顯示 [Windows 通用 OLE 版面設定] 對話方塊中，而且允許使用者選取各種列印設定選項，例如列印邊界、 大小和方向的紙張，以及目的地印表機。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，呼叫 Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror)函式來判斷是否發生錯誤。

IDOK 及 IDCANCEL 是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

此外，使用者可以存取印表機安裝選項，例如網路位置和所選印表機的特定屬性。

如果您想要初始化的各種版面設定對話方塊選項所設定的成員`m_psd`結構，您應該先呼叫如此做`DoModal`，前後建構對話方塊物件。 之後呼叫`DoModal`，呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者的資訊輸入。

如果您想要傳播目前使用者所輸入的設定，請呼叫[CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函式會將資訊從`CPageSetupDialog`物件初始化，並選取適當的屬性的新印表機 DC。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>範例

  範例，請參閱[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

呼叫此函式之後`DoModal`來擷取目前所選印表機的名稱。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

所使用的裝置名稱`CPageSetupDialog`物件。

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

呼叫此函式之後呼叫`DoModal`擷取印表機裝置內容的相關資訊`CPageSetupDialog`物件。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)資料結構，其中包含裝置的初始設定和環境的列印驅動程式的相關資訊。 您必須解除鎖定這個結構與 Windows 所取用的記憶體[GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock)函式，Windows SDK 中所述。

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

呼叫此函式之後呼叫[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)來擷取系統定莪印表機裝置驅動程式的名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

A`CString`指定系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

使用指標`CString`所傳回的物件`GetDriverName`的值為`lpszDriverName`呼叫中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

呼叫此函式在呼叫之後`DoModal`擷取印表機裝置驅動程式的邊界。

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>參數

*lpRectMargins*<br/>
指標[RECT](/windows/desktop/api/windef/ns-windef-tagrect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)告訴您目前所選印表機的列印邊界 （以 1/1000年英吋或 1/100 公釐） 的物件。 如果您不想要這個矩形，這個參數，傳遞 NULL。

*lpRectMinMargins*<br/>
指標`RECT`結構或`CRect`告訴您目前所選印表機的最小列印邊界 （以 1/1000年英吋或 1/100 公釐） 的物件。 如果您不想要這個矩形，這個參數，傳遞 NULL。

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

呼叫此函式以擷取列印選取的紙張大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，包含選取列印在紙張 （在 1/1000年英吋或 1/100 公釐） 的大小。

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

呼叫此函式之後呼叫`DoModal`來擷取目前選取的印表機連接埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

目前選取的印表機連接埠的名稱。

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

類型 PAGESETUPDLG，其成員儲存對話方塊物件的特性結構。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>備註

在建構之後`CPageSetupDialog`物件，您可以使用`m_psd`若要設定的對話方塊中，然後再呼叫的各個層面`DoModal`成員函式。

如果您修改`m_psd`資料成員直接，您將會覆寫任何預設行為。

如需詳細資訊[PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda)結構，請參閱 Windows SDK。

範例，請參閱[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

由架構呼叫以繪製於列印頁面的畫面影像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
印表機裝置內容指標。

*nMessage*<br/>
指定的訊息，指出頁面目前所繪製的區域。 可以是下列其中一項：

- WM_PSD_FULLPAGERECT 整個頁面區域。

- WM_PSD_MINMARGINRECT 目前的最小邊界。

- 目前 WM_PSD_MARGINRECT 邊界。

- WM_PSD_GREEKTEXTRECT 頁面內容。

- 保留給使用郵票表示 WM_PSD_ENVSTAMPRECT 區域。

- 用於代表寄件地址的 WM_PSD_YAFULLPAGERECT 區域。 這個區域會延伸到範例的頁面區域的邊緣。

*lpRect*<br/>
指標[CRect](../../atl-mfc-shared/reference/crect-class.md)或是[RECT](/windows/desktop/api/windef/ns-windef-tagrect)物件，含有在繪圖區域的座標。

### <a name="return-value"></a>傳回值

非零值，如果處理;否則為 0。

### <a name="remarks"></a>備註

此映像，然後會顯示通用 OLE 版面設定對話方塊的一部分。 預設實作會繪製的文字頁面的影像。

覆寫此函式以自訂繪製的映像或整個映像的特定區域。 您可以使用**切換**陳述式搭配**案例**檢查值的陳述式*n 訊息*。 例如，若要自訂內容的頁面影像轉譯，您可以使用下列的範例程式碼：

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

請注意，您不需要處理的每個案例*n 訊息*。 您可以選擇處理映像的映像或整個區域的數個元件的一個元件。

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

繪製畫面的影像列印的頁面之前由架構呼叫。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>參數

*wPaper*<br/>
指定值，指出的紙張大小。 這個值可以是其中一個**DMPAPER_** 值的描述中所列出[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)結構。

*wFlags*<br/>
表示紙張或信封的方向和印表機是點陣印表機或 HPPCL （Hewlett Packard 印表機控制語言） 裝置。 這個參數的值可以是下列其中一個：

- 0x001 紙張以橫向模式 （點陣式）

- 0x003 紙張以橫向模式 (HPPCL)

- 0x005 紙張以直向模式 （點陣式）

- 0x007 紙張以直向模式 (HPPCL)

- 0x00b 信封以橫向模式 (HPPCL)

- 0x00d 信封以直向模式 （點陣式）

- 0x019 信封以橫向模式 （點陣式）

- 0x01f 信封以直向模式 （點陣式）

*pPSD*<br/>
`PAGESETUPDLG` 結構的指標。 如需詳細資訊[PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda)，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

非零值，如果處理;否則為 0。

### <a name="remarks"></a>備註

覆寫此函式以自訂繪製影像。 如果您覆寫這個函式，並傳回 TRUE，則必須繪製整個映像。 如果您覆寫這個函式，並傳回 FALSE，由架構繪製整個預設影像。

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
