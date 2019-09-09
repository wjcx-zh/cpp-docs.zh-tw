---
title: CPrintDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741354"
---
# <a name="cprintdialog-class"></a>CPrintDialog 類別

封裝 Windows 通用列印對話方塊提供的服務。

## <a name="syntax"></a>語法

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|建構 `CPrintDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容，而不顯示 [列印] 對話方塊。|
|[CPrintDialog::DoModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|
|[CPrintDialog::GetCopies](#getcopies)|抓取要求的份數。|
|[CPrintDialog::GetDefaults](#getdefaults)|在不顯示對話方塊的情況下，抓取裝置預設值。|
|[CPrintDialog::GetDeviceName](#getdevicename)|抓取目前選取之印表機裝置的名稱。|
|[CPrintDialog::GetDevMode](#getdevmode)|`DEVMODE`抓取結構。|
|[CPrintDialog::GetDriverName](#getdrivername)|抓取目前選取的印表機驅動程式名稱。|
|[CPrintDialog::GetFromPage](#getfrompage)|抓取列印範圍的起始頁。|
|[CPrintDialog::GetPortName](#getportname)|抓取目前選取之印表機埠的名稱。|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|抓取印表機裝置內容的控制碼。|
|[CPrintDialog::GetToPage](#gettopage)|抓取列印範圍的結束頁。|
|[CPrintDialog::PrintAll](#printall)|決定是否要列印檔案的所有頁面。|
|[CPrintDialog::PrintCollate](#printcollate)|判斷是否要求自動分頁的複本。|
|[CPrintDialog::PrintRange](#printrange)|決定是否只列印指定的頁面範圍。|
|[CPrintDialog::PrintSelection](#printselection)|決定是否只列印目前選取的專案。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|用來自訂`CPrintDialog`物件的結構。|

## <a name="remarks"></a>備註

一般 [列印] 對話方塊提供簡單的方式，讓您以與 Windows 標準一致的方式來執行 [列印和列印設定] 對話方塊。

> [!NOTE]
>  `CPrintDialogEx`類別會封裝 Windows Print 屬性工作表所提供的服務。 如需詳細資訊，請參閱[CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)總覽。

`CPrintDialog`的功能是由[CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)所取代，其設計目的是為您提供列印設定和版面設定的通用對話方塊。

您可以依賴架構來處理應用程式的列印流程的許多層面。 在此情況下，架構會自動顯示要列印的 Windows 通用對話方塊。 您也可以讓架構處理應用程式的列印，但使用您自己的 [列印] 對話方塊來覆寫 [一般列印] 對話方塊。 如需使用架構來處理列印工作的詳細資訊，請參閱[列印](../../mfc/printing.md)文章。

如果您想要讓應用程式在不需要架構介入的情況下處理列印， `CPrintDialog`您可以使用提供的函式來「依原樣」類別，也可以從`CPrintDialog`衍生您自己的對話方塊類別，並撰寫符合您需求的函式。 不論是哪一種情況，這些對話方塊的行為都像標準 MFC 對話方塊，因為它們是`CCommonDialog`從類別衍生而來。

若要使用`CPrintDialog`物件，請先使用此`CPrintDialog`函數建立物件。 建立對話方塊之後，您可以設定或修改[m_pd](#m_pd)結構中的任何值，以初始化對話方塊控制項的值。 結構的型別為[PRINTDLG。](/windows/win32/api/commdlg/ns-commdlg-printdlga) `m_pd` 如需此結構的詳細資訊，請參閱 Windows SDK。

如果`m_pd`您未在中`hDevMode`為和`hDevNames`成員提供自己的控制碼`GlobalFree` ，請務必在完成對話方塊時，為這些控制碼呼叫 Windows 函式。 使用所提供`CWinApp::OnFilePrintSetup`的架構列印安裝程式時，您不需要釋放這些控制碼。 控制碼是由`CWinApp`維護，並在的析構函式中`CWinApp`釋放。 只有在使用`CPrintDialog`獨立時，才需要釋放這些控制碼。

在初始化對話方塊控制項之後，呼叫`DoModal`成員函式以顯示對話方塊，並允許使用者選取列印選項。 `DoModal`傳回使用者是否選取 [確定] （IDOK）或 [取消] （IDCANCEL）按鈕。

如果`DoModal`傳回 IDOK，您可以使用`CPrintDialog`的其中一個成員函式來取出使用者輸入的資訊。

`CPrintDialog::GetDefaults`成員函式可用於在不顯示對話方塊的情況下，抓取目前的印表機預設值。 此成員函式不需要使用者互動。

您可以使用 Windows `CommDlgExtendedError`函式來判斷對話方塊初始化期間是否發生錯誤，並深入瞭解錯誤。 如需此函數的詳細資訊，請參閱 Windows SDK。

`CPrintDialog`依賴 COMMDLG。Windows 3.1 和更新版本隨附的 DLL 檔案。

若要自訂對話方塊、從`CPrintDialog`衍生類別，請提供自訂對話方塊範本，並加入訊息對應以處理來自擴充控制項的通知訊息。 任何未處理的訊息都應該傳遞至基類。 不需要自訂攔截函數。

若要以不同的方式處理相同的訊息，視對話方塊是列印或列印設定而定，您必須為每個對話方塊衍生一個類別。 您也必須覆寫 Windows `AttachOnSetup`函式，此函式會在 [列印] 對話方塊中選取 [列印設定] 按鈕時，處理建立新對話方塊的功能。

如需使用`CPrintDialog`的詳細資訊，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

建立 [Windows 列印] 或 [列印設定] 對話方塊物件。

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*bPrintSetupOnly*<br/>
指定是否要顯示標準的 Windows [列印] 對話方塊或 [列印設定] 對話方塊。 將此參數設定為 [TRUE]，以顯示 [標準 Windows 列印安裝程式] 對話方塊。 將它設定為 FALSE 以顯示 [Windows 列印] 對話方塊。 如果*bPrintSetupOnly*為 FALSE，則 [列印] 對話方塊中仍會顯示 [列印設定] 選項按鈕。

*dwFlags*<br/>
一或多個旗標，可供您用來自訂對話方塊的設定，並使用位 OR 運算子進行結合。 例如，PD_ALLPAGES 旗標會將預設的列印範圍設定為檔的所有頁面。 如需這些旗標的詳細資訊，請參閱 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。

### <a name="remarks"></a>備註

這個成員函式只會建立物件。 `DoModal`使用成員函式來顯示對話方塊。

請注意，當您呼叫*bPrintSetupOnly*設定為 FALSE 的函式時，會自動使用 PD_RETURNDC 旗標。 呼叫`DoModal`、 `GetDefaults`或`m_pd.hDC`之後，將會在中傳回印表機 DC。 `GetPrinterDC` 此 DC 必須透過呼叫呼叫端的`CPrintDialog` [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)來釋放。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構建立印表機裝置內容（DC）。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

新建立之印表機裝置內容的控制碼。

### <a name="remarks"></a>備註

此 DC 會假設為目前的印表機 DC，而且任何其他先前取得的印表機 Dc 都必須由使用者刪除。 您可以呼叫此函式，並使用產生的 DC，而不需要顯示 [列印] 對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

顯示 [Windows 通用列印] 對話方塊，並允許使用者選取各種列印選項，例如份數、頁面範圍，以及是否應該將複本分頁。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL。 如果傳回 IDCANCEL，請呼叫 Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)函數來判斷是否發生錯誤。

IDOK 和 IDCANCEL 是常數，指出使用者是否選取 [確定] 或 [取消] 按鈕。

### <a name="remarks"></a>備註

如果您想要藉由設定`m_pd`結構的成員來初始化各種 [列印對話方塊] 選項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

呼叫`DoModal`之後，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

請注意，當您呼叫*bPrintSetupOnly*設定為 FALSE 的函式時，會自動使用 PD_RETURNDC 旗標。 呼叫`DoModal`、 `GetDefaults`或`m_pd.hDC`之後，將會在中傳回印表機 DC。 `GetPrinterDC` 此 DC 必須透過呼叫呼叫端的`CPrintDialog` [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)來釋放。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： CreatePrinterDC](#createprinterdc)的範例。

##  <a name="getcopies"></a>CPrintDialog::GetCopies

抓取要求的份數。

```
int GetCopies() const;
```

### <a name="return-value"></a>傳回值

要求的份數。

### <a name="remarks"></a>備註

呼叫`DoModal`以取得要求的份數之後，請呼叫此函式。

### <a name="example"></a>範例

  請參閱[CPrintDialog：:P rintcollate](#printcollate)的範例。

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

在不顯示對話方塊的情況下，抓取預設印表機的裝置預設值。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則為0。

### <a name="remarks"></a>備註

抓取的值會放在`m_pd`結構中。

在某些情況下，呼叫此函式將會呼叫 `CPrintDialog` 的 [constructor](#cprintdialog)，並將 *bPrintSetupOnly* 設定為 FALSE。 在這些情況下，系統會自動`hDevNames`配置`hDevMode`印表機 DC 和和（位於`m_pd`資料成員中的兩個控制碼）。

如果呼叫的的`CPrintDialog`函式，*且 bPrintSetupOnly*設定為 FALSE，則此`hDevNames`函式`hDevMode`不只會將和`m_pd.hDevMode`中`m_pd.hDevNames`的傳回到呼叫端，而且也會傳回中的印表機 DC`m_pd.hDC`。 當您完成`CPrintDialog`物件時，呼叫端會負責刪除印表機 DC，並在控制碼上呼叫 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)函數。

### <a name="example"></a>範例

此程式碼片段會取得預設印表機的裝置內容，並向使用者報告印表機的解析度（以每英寸點為單位）。 （印表機功能的這個屬性通常稱為 DPI）。

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

抓取目前選取之印表機裝置的名稱。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

目前選取之印表機的名稱。

### <a name="remarks"></a>備註

呼叫[DoModal](#domodal)以抓取目前選取之印表機的名稱，或在呼叫[GetDefaults](#getdefaults)以抓取預設印表機的目前裝置預設值之後，呼叫此函式。 `CString`在[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的呼叫中`GetDeviceName` ，使用所傳回`lpszDeviceName`之物件的指標做為的值。

### <a name="example"></a>範例

此程式碼片段會顯示使用者的預設印表機名稱及其連線的埠，以及印表機使用的多工緩衝處理器名稱。 這段程式碼可能會顯示一個訊息方塊，指出「您的預設印表機是使用\\winspool.drv 的 \server\share 上的 HP LaserJet IIIP。」，例如。

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

`DEVMODE`抓取結構。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)資料結構，其中包含有關列印驅動程式之裝置初始化和環境的資訊。 您必須使用 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock)函數（如 Windows SDK 中所述），解除鎖定此結構所佔用的記憶體。

### <a name="remarks"></a>備註

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以抓取列印裝置的相關資訊。

### <a name="example"></a>範例

  請參閱[CPrintDialog：:P rintcollate](#printcollate)的範例。

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

抓取目前選取的印表機驅動程式名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

， `CString`指定系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以取出系統定義的印表機設備磁碟機名稱。 `CString`在[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的呼叫中`GetDriverName` ，使用所傳回`lpszDriverName`之物件的指標做為的值。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： GetDeviceName](#getdevicename)的範例。

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

抓取列印範圍的起始頁。

```
int GetFromPage() const;
```

### <a name="return-value"></a>傳回值

要列印的頁面範圍中的起始頁碼。

### <a name="remarks"></a>備註

呼叫`DoModal`以在要列印的頁面範圍中抓取起始頁碼後，呼叫這個函式。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： m_pd](#m_pd)的範例。

##  <a name="getportname"></a>  CPrintDialog::GetPortName

抓取目前選取之印表機埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

目前選取之印表機埠的名稱。

### <a name="remarks"></a>備註

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以取得目前選取之印表機埠的名稱。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： GetDeviceName](#getdevicename)的範例。

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

抓取印表機裝置內容的控制碼。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為印表機裝置內容的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如果此 `CPrintDialog`函式的 bPrintSetupOnly 參數為 FALSE （表示顯示 [列印] 對話方塊），則`GetPrinterDC`會傳回印表機裝置內容的控制碼。 當您使用完裝置內容時，您必須呼叫 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)函式來加以刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

抓取列印範圍的結束頁。

```
int GetToPage() const;
```

### <a name="return-value"></a>傳回值

要列印的頁面範圍中的結束頁碼。

### <a name="remarks"></a>備註

呼叫`DoModal`以取得要列印之頁面範圍中的結束頁碼後，請呼叫此函式。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： m_pd](#m_pd)的範例。

##  <a name="m_pd"></a>  CPrintDialog::m_pd

結構，其成員會儲存對話方塊物件的特性。

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>備註

在建立`CPrintDialog`物件之後，您可以使用`m_pd`在呼叫[DoModal](#domodal)成員函式之前，設定對話方塊的各個層面。 如需`m_pd`結構的詳細資訊，請參閱 Windows SDK 中的[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) 。

如果您直接修改`m_pd`資料成員，將會覆寫任何預設行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

決定是否要列印檔案的所有頁面。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>傳回值

如果要列印檔案中的所有頁面，則為非零值;否則為0。

### <a name="remarks"></a>備註

在呼叫`DoModal`之後呼叫此函式，以判斷是否要列印檔案中的所有頁面。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： m_pd](#m_pd)的範例。

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

判斷是否要求自動分頁的複本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>傳回值

如果使用者選取對話方塊中的 [自動分頁] 核取方塊，則為非零。否則為0。

### <a name="remarks"></a>備註

在呼叫`DoModal`之後呼叫此函式，以判斷印表機是否應自動分頁所有列印的檔複本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

決定是否只列印指定的頁面範圍。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>傳回值

如果只列印檔案中的一系列頁面，則為非零值。否則為0。

### <a name="remarks"></a>備註

在呼叫`DoModal`之後呼叫此函式，以判斷是否只列印檔案中的一系列頁面。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： m_pd](#m_pd)的範例。

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

決定是否只列印目前選取的專案。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>傳回值

如果只列印選取的專案，則為非零;否則為0。

### <a name="remarks"></a>備註

在呼叫`DoModal`之後呼叫此函式，以判斷是否只列印目前選取的專案。

### <a name="example"></a>範例

  請參閱[CPrintDialog：： m_pd](#m_pd)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
