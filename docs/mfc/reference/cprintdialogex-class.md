---
title: CPrintDialogEx 類別
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 76c3968b20a66e9653fd769339e23ede2a756bbd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741334"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 類別

封裝 Windows Print 屬性工作表所提供的服務。

## <a name="syntax"></a>語法

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|建構 `CPrintDialogEx` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容，而不顯示 [列印] 對話方塊。|
|[CPrintDialogEx::DoModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|
|[CPrintDialogEx::GetCopies](#getcopies)|抓取要求的份數。|
|[CPrintDialogEx::GetDefaults](#getdefaults)|在不顯示對話方塊的情況下，抓取裝置預設值。|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|抓取目前選取之印表機裝置的名稱。|
|[CPrintDialogEx::GetDevMode](#getdevmode)|`DEVMODE`抓取結構。|
|[CPrintDialogEx::GetDriverName](#getdrivername)|抓取系統定義的印表機設備磁碟機的名稱。|
|[CPrintDialogEx::GetPortName](#getportname)|抓取目前選取之印表機埠的名稱。|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|抓取印表機裝置內容的控制碼。|
|[CPrintDialogEx::PrintAll](#printall)|決定是否要列印檔案的所有頁面。|
|[CPrintDialogEx::PrintCollate](#printcollate)|判斷是否要求自動分頁的複本。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|決定是否要列印檔案的目前頁面。|
|[CPrintDialogEx::PrintRange](#printrange)|決定是否只列印指定的頁面範圍。|
|[CPrintDialogEx::PrintSelection](#printselection)|決定是否只列印目前選取的專案。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|用來自訂`CPrintDialogEx`物件的結構。|

## <a name="remarks"></a>備註

您可以依賴架構來處理應用程式的列印流程的許多層面。 如需使用架構來處理列印工作的詳細資訊，請參閱[列印](../../mfc/printing.md)文章。

如果您想要讓應用程式在不需要架構介入的情況下處理列印， `CPrintDialogEx`您可以使用提供的函式來「依原樣」類別，也可以從`CPrintDialogEx`衍生您自己的對話方塊類別，並撰寫符合您需求的函式。 不論是哪一種情況，這些對話方塊的行為都像標準 MFC 對話方塊，因為它們是`CCommonDialog`從類別衍生而來。

若要使用`CPrintDialogEx`物件，請先使用此`CPrintDialogEx`函數建立物件。 建立對話方塊之後，您可以設定或修改[m_pdex](#m_pdex)結構中的任何值，以初始化對話方塊控制項的值。 結構的型別為[PRINTDLGEX。](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) `m_pdex` 如需此結構的詳細資訊，請參閱 Windows SDK。

如果`m_pdex`您未在中`hDevMode`為和`hDevNames`成員提供自己的控制碼`GlobalFree` ，請務必在完成對話方塊時，為這些控制碼呼叫 Windows 函式。

在初始化對話方塊控制項之後，呼叫`DoModal`成員函式以顯示對話方塊，並允許使用者選取列印選項。 當`DoModal`傳回時，您可以判斷使用者是否選取 [確定]、[套用] 或 [取消] 按鈕。

如果使用者按下 [確定]，您`CPrintDialogEx`可以使用的成員函式來抓取使用者輸入的資訊。

`CPrintDialogEx::GetDefaults`成員函式可用於在不顯示對話方塊的情況下，抓取目前的印表機預設值。 這個方法不需要使用者互動。

您可以使用 Windows `CommDlgExtendedError`函式來判斷對話方塊初始化期間是否發生錯誤，並深入瞭解錯誤。 如需此函數的詳細資訊，請參閱 Windows SDK。

如需使用`CPrintDialogEx`的詳細資訊，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

建立 Windows 列印屬性工作表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
一或多個旗標，可供您用來自訂對話方塊的設定，並使用位 OR 運算子進行結合。 例如，PD_ALLPAGES 旗標會將預設的列印範圍設定為檔的所有頁面。 如需這些旗標的詳細資訊，請參閱 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。

### <a name="remarks"></a>備註

這個成員函式只會建立物件。 `DoModal`使用成員函式來顯示對話方塊。

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構建立印表機裝置內容（DC）。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

新建立之印表機裝置內容的控制碼。

### <a name="remarks"></a>備註

傳回的 DC 也會儲存在`hDC` [m_pdex](#m_pdex)的成員中。

此 DC 會假設為目前的印表機 DC，而且任何其他先前取得的印表機 Dc 都必須刪除。 您可以呼叫此函式，並使用產生的 DC，而不需要顯示 [列印] 對話方塊。

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

呼叫此函式可顯示 Windows 列印屬性工作表，並允許使用者選取各種列印選項，例如份數、頁面範圍，以及是否應該將複本自動分頁。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

INT_PTR 傳回值實際上是 HRESULT。 請參閱 Windows SDK 中[PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\))的傳回值一節。

### <a name="remarks"></a>備註

如果您想要藉由設定`m_pdex`結構的成員來初始化各種 [列印對話方塊] 選項，您應該在呼叫`DoModal`之前執行此動作，但在構造對話方塊物件之後。

呼叫`DoModal`之後，您可以呼叫其他成員函式，以抓取使用者在對話方塊中輸入的設定或資訊。

如果在呼叫`DoModal`時使用 PD_RETURNDC 旗標，則會在[m_pdex](#m_pdex)的`hDC`成員中傳回印表機 DC。 此 DC 必須透過呼叫呼叫端的`CPrintDialogEx` [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)來釋放。

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

呼叫`DoModal`以取得要求的份數之後，請呼叫此函式。

```
int GetCopies() const;
```

### <a name="return-value"></a>傳回值

要求的份數。

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

呼叫此函式可取出預設印表機的裝置預設值，而不會顯示對話方塊。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構建立印表機裝置內容（DC）。

`GetDefaults`不會顯示 [列印] 屬性工作表。 相反地，它會`hDevNames`將`hDevMode` [m_pdex](#m_pdex)的和成員設定為處理為系統預設印表機初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構。 `GetDefaults`和`hDevNames` 都`hDevMode`必須是 Null 或失敗。

如果已設定 PD_RETURNDC 旗標，則此函式不只`hDevNames`會`hDevMode`將和（ `m_pdex.hDevNames`位於`m_pdex.hDevMode`和）傳回給呼叫者，而且也會傳回中`m_pdex.hDC`的印表機 DC。 當您完成`CPrintDialogEx`物件時，呼叫端會負責刪除印表機 DC，並在控制碼上呼叫 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)函數。

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

呼叫[DoModal](#domodal)以抓取目前選取之印表機的名稱，或在呼叫[GetDefaults](#getdefaults)來抓取預設印表機的名稱之後，呼叫此函式。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

目前選取之印表機的名稱。

### <a name="remarks"></a>備註

`CString`在[CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的呼叫中`GetDeviceName` ，使用所傳回`lpszDeviceName`之物件的指標做為的值。

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以抓取列印裝置的相關資訊。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)資料結構，其中包含有關列印驅動程式之裝置初始化和環境的資訊。 您必須使用 Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock)函數（如 Windows SDK 中所述），解除鎖定此結構所佔用的記憶體。

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以取出系統定義的印表機設備磁碟機名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

， `CString`指定系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

在`CString` [CDC：： CreateDC](../../mfc/reference/cdc-class.md#createdc)的呼叫中`GetDriverName` ，使用所傳回之物件的指標做為*lpszDriverName*的值。

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

在呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)之後呼叫此函式，以取得目前選取之印表機埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

目前選取之印表機埠的名稱。

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

傳回印表機裝置內容的控制碼。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>傳回值

印表機裝置內容的控制碼。

### <a name="remarks"></a>備註

當您使用完裝置內容時，您必須呼叫 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)函式來加以刪除。

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

PRINTDLGEX 結構，其成員會儲存對話方塊物件的特性。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>備註

在建立`CPrintDialogEx`物件之後，您可以使用`m_pdex`在呼叫[DoModal](#domodal)成員函式之前，設定對話方塊的各個層面。 如需`m_pdex`結構的詳細資訊，請參閱 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) 。

如果您直接修改`m_pdex`資料成員，將會覆寫任何預設行為。

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

在呼叫`DoModal`之後呼叫此函式，以判斷是否要列印檔案中的所有頁面。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>傳回值

如果要列印檔案中的所有頁面，則為 TRUE;否則為 FALSE。

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

在呼叫`DoModal`之後呼叫此函式，以判斷印表機是否應自動分頁所有列印的檔複本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>傳回值

如果使用者選取對話方塊中的 [自動分頁] 核取方塊，則為 TRUE;否則為 FALSE。

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

在呼叫`DoModal`之後呼叫此函式，以判斷是否要列印檔案中的目前頁面。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>傳回值

如果在列印對話方塊中選取了 [**列印目前的頁面**]，則為 TRUE;否則為 FALSE。

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

在呼叫`DoModal`之後呼叫此函式，以判斷是否只列印檔案中的一系列頁面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>傳回值

如果檔中只會列印一段範圍的頁面，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您可以從[m_pdex](#m_pdex)判斷指定的頁面範圍（請`nPageRanges`參閱`nMaxPageRanges`中的`lpPageRanges` [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)結構 Windows SDK 中的、和）。

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

在呼叫`DoModal`之後呼叫此函式，以判斷是否只列印目前選取的專案。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>傳回值

如果只列印選取的專案，則為 TRUE;否則為 FALSE。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
