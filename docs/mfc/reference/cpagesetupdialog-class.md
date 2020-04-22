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
ms.openlocfilehash: 3664149ef0d7476b460ef06cddaf2b8145ade701
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753696"
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
|[CPagesetup對話::CPage安裝程式對話](#cpagesetupdialog)|建構 `CPageSetupDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPageSetup::建立印表機DC](#createprinterdc)|建立用於列印的裝置上下文。|
|[CPagesetup對話::Do模態](#domodal)|顯示對話框,並允許用戶進行選擇。|
|[CPagesetup對話:抓取裝置名稱](#getdevicename)|返回印表機的設備名稱。|
|[CPagesetup對話::取得開發模式](#getdevmode)|返回印表機的當前 DEVMODE。|
|[CPagesetup對話::取得驅動程式名稱](#getdrivername)|返回印表機使用的驅動程式。|
|[CPagesetup對話:取得邊緣](#getmargins)|返回印表機的當前邊距設置。|
|[CPagesetup對話::取得紙張大小](#getpapersize)|返回印表機的紙張大小。|
|[CPagesetup對話::取得連接埠名稱](#getportname)|返回輸出埠名稱。|
|[CPagesetup對話::在畫頁](#ondrawpage)|由框架調用以呈現列印頁的螢幕圖像。|
|[CPagesetup對話::P重新繪製頁面](#predrawpage)|在渲染列印頁的螢幕圖像之前,由框架調用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPagesetup對話::m_psd](#m_psd)|定義物件的結構`CPageSetupDialog`。|

## <a name="remarks"></a>備註

此類旨在取代「列印設置」對話框。

要使用`CPageSetupDialog`物件,請首先`CPageSetupDialog`使用 建構函數創建物件。 建構對話框後,可以設置或修改`m_psd`資料成員中的任何值,以初始化對話方塊控制項的值。 [m_psd](#m_psd)結構為PAGESETUPDLG型。

初始化對話方塊控制項後,呼`DoModal`叫成員函數以顯示對話方塊,並允許使用者選擇列印選項。 `DoModal`返回使用者是否選擇了"確定 (IDOK)"還是"取消"(IDCANCEL)按鈕。

如果`DoModal`返回 IDOK,則可以使用`CPageSetupDialog`多個成員函數或`m_psd`訪問 數據成員來檢索使用者輸入的資訊。

> [!NOTE]
> 取消通用 OLE 頁面設定對話方塊後,框架將不會保存使用者所做的任何更改。 由應用程式本身將此對話方塊中的任何值保存到永久位置,例如應用程式的文件或應用程式類的成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPagesetup對話::CPage安裝程式對話

呼叫此函式以建構物件`CPageSetupDialog`。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
可用於自定義對話方塊設置的一個或多個標誌。 可以使用位-OR 運算符組合這些值。 這些值具有以下意義：

- PSD_DEFAULTMINMARGINS 將頁邊距的最小允許寬度設置為與印表機最小值相同的最小寬度。 如果還指定了PSD_MARGINS和PSD_MINMARGINS標誌,則忽略此標誌。

- PSD_INWININIINTLMEASURE未實現。

- PSD_MINMARGINS 使系統`rtMinMargin`使用 成員中指定的值作為左側、頂部、右側和底部邊距的最小允許寬度。 系統可防止使用者輸入小於指定最小值的寬度。 如果未指定PSD_MINMARGINS,系統將允許的最小寬度設置為印表機允許的最小寬度。

- PSD_MARGINS激活邊距控制區域。

- PSD_INTHOUSANDTHSOFINCHES 使對話框的單位以 1/1000 英寸為單位進行測量。

- PSD_INHUNDREDTHSOFMILLIMETERS 使對話框的單位以 1/100 毫米為單位進行測量。

- PSD_DISABLEMARGINS禁用邊距對話框控制件。

- PSD_DISABLEPRINTER禁用印表機按鈕。

- PSD_NOWARNING防止在沒有預設印表機時顯示警告消息。

- PSD_DISABLEORIENTATION 禁用頁面方向對話方塊控制項。

- PSD_RETURNDEFAULT`CPageSetupDialog`導致返回為系統預設印表機初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構而不顯示對話方塊。 假定兩者`hDevNames``hDevMode`均為 NULL;否則,函數將返回一個錯誤。 如果舊印表機驅動程式支援系統預設印表機(早於 Windows 版本 3.0),則僅返回`hDevNames`系統預設印表機;如果舊印表機驅動程式支援系統預設印表機(早於 Windows 版本 3.0),則僅返回系統預設印表機。`hDevMode`為 NULL。

- PSD_DISABLEPAPER禁用紙張選擇控制項。

- PSD_SHOWHELP 使對話框顯示"説明"按鈕。 如果`hwndOwner`指定此標誌,則成員不能為 NULL。

- PSD_ENABLEPAGESETUPHOOK 啟用`lpfnSetupHook`中 指定的掛鉤函數。

- PSD_ENABLEPAGESETUPTEMPLATE 使作業系統使用`hInstance``lpSetupTemplateName`和標識的對話框範本框創建對話方塊。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE指示`hInstance`標識包含預載入對話框範本的數據塊。 如果指定了此`lpSetupTemplateName`標誌,系統將忽略。

- PSD_ENABLEPAGEPAINTHOOK 啟用`lpfnPagePaintHook`中 指定的掛鉤函數。

- PSD_DISABLEPAGEPAINTING禁用對話框的繪製區域。

*pparentwnd*<br/>
指向對話框的父或所有者的指標。

### <a name="remarks"></a>備註

使用["DoModal"](../../mfc/reference/cdialog-class.md#domodal)功能顯示對話框。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetup::建立印表機DC

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構創建印表機裝置上下文。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

處理新創建的印表機設備上下文 (DC)。

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPagesetup對話::Do模態

呼叫此函數以顯示 Windows 通用 OLE 頁面設定對話方塊,並允許使用者選擇各種列印設定選項,如列印邊距、紙張的大小和方向以及目標印表機。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果返回 IDCANCEL,請呼叫 Windows [CommDlg 擴充錯誤](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)功能以確定是否發生了錯誤。

IDOK 和 IDCANCEL 是指示使用者選擇"確定"還是"取消"按鈕的常量。

### <a name="remarks"></a>備註

此外,用戶可以存取印表機設置選項,如網路位置和特定於所選印表機的屬性。

如果要通過設置`m_psd`結構成員來初始化各種頁面設置對話框選項,則應在調`DoModal`用 之前和構造對話框物件之後執行此操作。 調用`DoModal`後 調用 其他成員函數以檢索使用者輸入到對話方塊中的設置或資訊。

如果要傳播使用者輸入的當前設定,請呼叫[CWinApp::選擇印表機](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函數從`CPageSetupDialog`物件獲取資訊並初始化,並選擇具有正確屬性的新印表機 DC。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>範例

  請參考[CPageSetup 對話框的範例:cPagesetupDialog](#cpagesetupdialog)。

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPagesetup對話:抓取裝置名稱

在此之後`DoModal`調用此功能以檢索當前選取印表機的名稱。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

`CPageSetupDialog`對象使用的設備名稱。

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPagesetup對話::取得開發模式

調用後調用`DoModal`此功能以檢索`CPageSetupDialog`有關 物件的印表機設備上下文的資訊。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)資料結構,其中包含有關列印驅動程序的設備初始化和環境的資訊。 您必須使用 Windows[全域解鎖](/windows/win32/api/winbase/nf-winbase-globalunlock)功能解鎖此結構佔用的記憶體,該功能在 Windows SDK 中進行了描述。

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPagesetup對話::取得驅動程式名稱

呼叫[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)後呼叫此功能以檢索系統定義的印表機裝置驅動程式的名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

指定`CString`系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

`CString`使用指向返回`GetDriverName`的物件的指標作為 調用`lpszDriverName`[CDC:::createDC](../../mfc/reference/cdc-class.md#createdc)中的值。

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPagesetup對話:取得邊緣

呼叫後呼叫此功能以`DoModal`檢索印表機裝置驅動程式的邊距。

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>參數

*lprect 邊緣*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件,該物件描述當前所選印表機的列印邊距(以 1/1000 英吋或 1/100 mm 為單位)。 如果對此矩形不感興趣,則通過 NULL。

*lpRectMin 邊緣*<br/>
指向結構或`RECT`物件`CRect`, 該結構或物件描述目前所選印表機的最小列印邊距(1/1000 英吋或 1/100 mm)。 如果對此矩形不感興趣,則通過 NULL。

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPagesetup對話::取得紙張大小

呼叫此函數以檢索選擇要列印的紙張的大小。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>傳回值

選擇用於列印的包含紙張大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件(以 1/1000 英吋或 1/100 毫米為單位)。

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPagesetup對話::取得連接埠名稱

呼叫後呼叫`DoModal`此功能以檢索當前選定的印表機埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

當前選定的印表機埠的名稱。

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPagesetup對話::m_psd

PAGESETUPDLG 類型的結構,其成員存儲對話框物件的特徵。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>備註

建構`CPageSetupDialog`物件后,可以`m_psd`使用 在`DoModal`調用 成員函數之前設置對話框的各個方面。

如果直接修改`m_psd`數據成員,將覆蓋任何默認行為。

有關[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)結構的詳細資訊,請參閱 Windows SDK。

請參考[CPageSetup 對話框的範例:cPagesetupDialog](#cpagesetupdialog)。

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPagesetup對話::在畫頁

由框架調用以繪製列印頁的螢幕圖像。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向印表機設備上下文的指標。

*n訊息*<br/>
指定一條消息,指示當前正在繪製的頁面的區域。 可以是下列其中一項：

- WM_PSD_FULLPAGERECT整個頁面區域。

- WM_PSD_MINMARGINRECT 當前最小邊距。

- WM_PSD_MARGINRECT 當前邊距。

- WM_PSD_GREEKTEXTRECT頁面的內容。

- WM_PSD_ENVSTAMPRECT為郵票表示而保留的區域。

- WM_PSD_YAFULLPAGERECT返回位址表示的區域。 此區域延伸到示例頁面區域的邊緣。

*lpRect*<br/>
指向包含繪圖區域座標的[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](/windows/win32/api/windef/ns-windef-rect)物件的指標。

### <a name="return-value"></a>傳回值

處理時非零值;否則 0。

### <a name="remarks"></a>備註

然後,此圖像將作為通用 OLE 頁面設置對話框的一部分顯示。 預設實現繪製文本頁面的圖像。

重寫此函數以自定義圖像的特定區域或整個圖像的圖形。 可以通過對**大小寫**語句使用**switch**語句來檢查*nMessage*的值來執行此操作。 例如,要自訂頁面圖像內容的呈現,可以使用以下範例碼:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

請注意,您不需要處理每種情況下的*nMessage*。 您可以選擇處理圖像的一個元件、圖像的幾個元件或整個區域。

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPagesetup對話::P重新繪製頁面

在繪製列印頁的螢幕圖像之前,由框架調用。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>參數

*wPaper*<br/>
指定指示紙張大小的值。 此值可以是[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)結構描述中列出的**DMPAPER_** 值之一。

*wFlags*<br/>
指示紙張或信封的方向,以及印表機是點陣還是 HPPCL(惠普印表機控制語言)設備。 這個參數的值可以是下列其中一個：

- 0x001 橫向模式下的紙張(點矩陣)

- 0x003 橫向模式下的紙張 (HPPCL)

- 0x005 縱向模式下的紙張(點矩陣)

- 0x007 縱向模式下的紙張 (HPPCL)

- 0x00b 橫向模式下的信封 (HPPCL)

- 0x00d 縱向模式下的信封(點矩陣)

- 0x019 橫向模式下的信封(點矩陣)

- 0x01f 縱向模式下的信封(點矩陣)

*pPSD*<br/>
`PAGESETUPDLG` 結構的指標。 有關[PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)的詳細資訊,請參閱 Windows SDK。

### <a name="return-value"></a>傳回值

處理時非零值;否則 0。

### <a name="remarks"></a>備註

重寫此函數以自定義圖像的圖形。 如果重寫此函數並返回 TRUE,則必須繪製整個圖像。 如果重寫此函數並返回 FALSE,則整個預設圖像由框架繪製。

## <a name="see-also"></a>另請參閱

[MFC 樣品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
