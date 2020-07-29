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
ms.openlocfilehash: 280d75c3bcacd673107fd32ecaa39953b06a77c8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214070"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 類別

封裝 Windows 通用 OLE 版面設定對話方塊所提供的服務，以及設定和修改列印邊界的額外支援。

## <a name="syntax"></a>語法

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|建構 `CPageSetupDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|建立列印的裝置內容。|
|[CPageSetupDialog：:D oModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|傳回印表機的裝置名稱。|
|[CPageSetupDialog::GetDevMode](#getdevmode)|傳回印表機目前的 DEVMODE。|
|[CPageSetupDialog：： GetDriverName](#getdrivername)|傳回印表機所使用的驅動程式。|
|[CPageSetupDialog::GetMargins](#getmargins)|傳回印表機的目前邊界設定。|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|傳回印表機的紙張大小。|
|[CPageSetupDialog::GetPortName](#getportname)|傳回輸出埠名稱。|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|由架構呼叫以呈現列印頁面的螢幕影像。|
|[CPageSetupDialog：:P reDrawPage](#predrawpage)|在呈現列印頁面的螢幕影像之前，由架構呼叫。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CPageSetupDialog：： m_psd](#m_psd)|用來自訂物件的結構 `CPageSetupDialog` 。|

## <a name="remarks"></a>備註

這個類別是設計用來取代 [列印設定] 對話方塊。

若要使用 `CPageSetupDialog` 物件，請先使用此函數建立物件 `CPageSetupDialog` 。 建立對話方塊之後，您可以設定或修改資料成員中的任何值， `m_psd` 以初始化對話方塊控制項的值。 [M_psd](#m_psd)結構的類型是 PAGESETUPDLG。

在初始化對話方塊控制項之後，呼叫成員函式 `DoModal` 以顯示對話方塊，並允許使用者選取列印選項。 `DoModal`傳回使用者是否選取 [確定] （IDOK）或 [取消] （IDCANCEL）按鈕。

如果傳回 `DoModal` IDOK，您可以使用數個的成員函式 `CPageSetupDialog` 或存取 `m_psd` 資料成員，以取出使用者的資訊輸入。

> [!NOTE]
> 在 [一般 OLE 版面設定] 對話方塊關閉之後，架構將不會儲存使用者所做的任何變更。 應用程式本身會負責將此對話方塊中的任何值儲存到永久位置，例如應用程式的檔或應用程式類別的成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

呼叫此函式以建立 `CPageSetupDialog` 物件。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
一或多個旗標，可供您用來自訂對話方塊的設定。 這些值可以使用位 OR 運算子結合。 這些值具有以下意義：

- PSD_DEFAULTMINMARGINS 會將頁面邊界的最小允許寬度設定為與印表機的最低值相同。 如果同時指定了 PSD_MARGINS 和 PSD_MINMARGINS 旗標，則會忽略此旗標。

- PSD_INWININIINTLMEASURE 未執行。

- PSD_MINMARGINS 會導致系統使用成員中指定的值 `rtMinMargin` ，做為左邊、上、右和下邊界的最小允許寬度。 系統會防止使用者輸入小於指定之最小值的寬度。 如果未指定 PSD_MINMARGINS，系統會將允許的最小寬度設定為印表機允許的寬度。

- PSD_MARGINS 啟動邊界控制項區域。

- PSD_INTHOUSANDTHSOFINCHES 會導致對話方塊的單位以一英寸的1/1000 測量。

- PSD_INHUNDREDTHSOFMILLIMETERS 會導致對話方塊的單位以一毫米的1/100 測量。

- PSD_DISABLEMARGINS 停用邊界對話方塊控制項。

- PSD_DISABLEPRINTER 停用 [印表機] 按鈕。

- PSD_NOWARNING 防止在沒有預設印表機時顯示警告訊息。

- PSD_DISABLEORIENTATION 停用 [頁面方向] 對話方塊控制項。

- PSD_RETURNDEFAULT 會導致傳回 `CPageSetupDialog` [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構，為系統預設印表機初始化，而不會顯示對話方塊。 假設 `hDevNames` 和 `hDevMode` 都是 Null，否則函數會傳回錯誤。 如果舊的印表機驅動程式（早于 Windows 3.0 版）支援系統預設印表機，則只 `hDevNames` 會傳回; `hDevMode` 是 Null。

- PSD_DISABLEPAPER 停用紙張選取控制項。

- PSD_SHOWHELP 會導致對話方塊顯示 [說明] 按鈕。 `hwndOwner`如果指定此旗標，成員不得為 Null。

- PSD_ENABLEPAGESETUPHOOK 啟用中指定的攔截函式 `lpfnSetupHook` 。

- PSD_ENABLEPAGESETUPTEMPLATE 會導致作業系統使用和所識別的對話方塊範本方塊來建立對話方塊 `hInstance` `lpSetupTemplateName` 。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE 表示 `hInstance` 識別包含預先載入之對話方塊範本的資料區塊。 `lpSetupTemplateName`如果指定此旗標，系統就會忽略。

- PSD_ENABLEPAGEPAINTHOOK 啟用中指定的攔截函式 `lpfnPagePaintHook` 。

- PSD_DISABLEPAGEPAINTING 停用對話方塊的繪製區域。

*pParentWnd*<br/>
對話方塊的父系或擁有者的指標。

### <a name="remarks"></a>備註

使用[DoModal](../../mfc/reference/cdialog-class.md#domodal)函數來顯示對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構建立印表機裝置內容。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

新建立之印表機裝置內容（DC）的控制碼。

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog：:D oModal

呼叫此函式以顯示 [Windows 通用 OLE 版面設定] 對話方塊，並允許使用者選取各種列印設定選項，例如列印邊界、紙張大小和方向，以及目的地印表機。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，請呼叫 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函數來判斷是否發生錯誤。

IDOK 和 IDCANCEL 是常數，指出使用者是否選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

此外，使用者也可以存取印表機安裝選項，例如所選印表機特定的網路位置和內容。

如果您想要藉由設定結構的成員來初始化各種 [版面設定] 對話方塊選項 `m_psd` ，您應該在呼叫之前 `DoModal` ，以及在建立對話方塊物件之後，執行此動作。 呼叫之後 `DoModal` ，呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

如果您想要傳播使用者所輸入的目前設定，請呼叫[CWinApp：： SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函式會從物件取得資訊 `CPageSetupDialog` ，並使用適當的屬性來初始化並選取新的印表機 DC。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>範例

  請參閱[CPageSetupDialog：： CPageSetupDialog](#cpagesetupdialog)的範例。

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

請在之後呼叫此函式 `DoModal` ，以取得目前選取之印表機的名稱。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

物件所使用的裝置名稱 `CPageSetupDialog` 。

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

呼叫以抓取物件之 `DoModal` 印表機裝置內容的相關資訊之後，呼叫此函式 `CPageSetupDialog` 。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)資料結構，其中包含有關列印驅動程式之裝置初始化和環境的資訊。 您必須使用 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock)函數（如 Windows SDK 中所述），解除鎖定此結構所佔用的記憶體。

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog：： GetDriverName

呼叫[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)來取得系統定義的印表機設備磁碟機名稱之後，請呼叫此函式。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

， `CString` 指定系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

`CString` `GetDriverName` `lpszDriverName` 在[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的呼叫中，使用所傳回之物件的指標做為的值。

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

呼叫以 `DoModal` 取得印表機設備磁碟機的邊界之後，呼叫此函式。

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>參數

*lpRectMargins*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件的指標，描述目前所選印表機的列印邊界（1/1000 英寸或 1/100 mm）。 如果您對此矩形不感興趣，請傳遞 Null 給此參數。

*lpRectMinMargins*<br/>
`RECT`結構或 `CRect` 物件的指標，描述目前所選印表機的最小列印邊界（1/1000 英寸或 1/100 mm）。 如果您對此矩形不感興趣，請傳遞 Null 給此參數。

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

呼叫此函式可抓取選取要列印的紙張大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含選取要列印的紙張大小（1/1000 英寸或 1/100 mm）。

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

呼叫 `DoModal` 以抓取目前選取的印表機埠名稱之後，呼叫此函式。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

目前選取之印表機埠的名稱。

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog：： m_psd

PAGESETUPDLG 類型的結構，其成員會儲存對話方塊物件的特性。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>備註

在建立 `CPageSetupDialog` 物件之後，您可以在 `m_psd` 呼叫成員函式之前，使用來設定對話方塊的各個層面 `DoModal` 。

如果您直接修改 `m_psd` 資料成員，將會覆寫任何預設行為。

如需有關[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)結構的詳細資訊，請參閱 Windows SDK。

請參閱[CPageSetupDialog：： CPageSetupDialog](#cpagesetupdialog)的範例。

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

由架構呼叫以繪製列印頁面的螢幕影像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
印表機裝置內容的指標。

*N 訊息*<br/>
指定訊息，指出目前正在繪製的頁面區域。 可以是下列其中一項：

- WM_PSD_FULLPAGERECT 整個頁面區域。

- WM_PSD_MINMARGINRECT 目前的最小邊界。

- WM_PSD_MARGINRECT 目前的邊界。

- WM_PSD_GREEKTEXTRECT 頁面的內容。

- 保留給郵資戳記的 WM_PSD_ENVSTAMPRECT 區域。

- 傳回位址標記法的 WM_PSD_YAFULLPAGERECT 區域。 這個區域會延伸至範例頁面區域的邊緣。

*lpRect*<br/>
[CRect](../../atl-mfc-shared/reference/crect-class.md)或[矩形](/windows/win32/api/windef/ns-windef-rect)物件的指標，其中包含繪圖區的座標。

### <a name="return-value"></a>傳回值

如果已處理，則為非零值;否則為0。

### <a name="remarks"></a>備註

然後，此影像會顯示為 [一般 OLE 版面設定] 對話方塊的一部分。 預設的執行會繪製一頁文字的影像。

覆寫此函式，以自訂影像特定區域的繪圖或整個影像。 若要這麼做，您可以使用 **`switch`** 語句，並 **`case`** 檢查*n 訊息*值的語句。 例如，若要自訂頁面影像內容的呈現方式，您可以使用下列範例程式碼：

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

請注意，您不需要處理*n 訊息*的每個案例。 您可以選擇處理影像的一個元件、影像的數個元件或整個區域。

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog：:P reDrawPage

在繪製列印頁面的螢幕影像之前，由架構呼叫。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>參數

*wPaper*<br/>
指定表示紙張大小的值。 這個值可以是[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)結構描述中所列的其中一個**DMPAPER_** 值。

*wFlags*<br/>
指出紙張或信封的方向，以及印表機是否為單點矩陣或 HPPCL （Hewlett Packard 印表機控制語言）裝置。 這個參數的值可以是下列其中一個：

- 橫向模式的0x001 紙張（點矩陣）

- 橫向模式的0x003 紙張（HPPCL）

- 以直向模式0x005 紙張（點矩陣）

- 以直向模式0x007 紙張（HPPCL）

- 橫向模式的0x00b 信封（HPPCL）

- 直向模式中的0x00d 信封（點矩陣）

- 橫向模式的0x019 信封（點矩陣）

- 直向模式中的0x01f 信封（點矩陣）

*pPSD*<br/>
`PAGESETUPDLG` 結構的指標。 如需[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)的詳細資訊，請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

如果已處理，則為非零值;否則為0。

### <a name="remarks"></a>備註

覆寫此函式以自訂影像的繪圖。 如果您覆寫此函式並傳回 TRUE，則必須繪製整個影像。 如果您覆寫此函式並傳回 FALSE，則架構會繪製整個預設影像。

## <a name="see-also"></a>另請參閱

[MFC 範例 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
