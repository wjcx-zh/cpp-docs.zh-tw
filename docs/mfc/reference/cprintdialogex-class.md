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
ms.openlocfilehash: 79d696f89ca7474220559abbf5464f32b6e684c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543321"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 類別

封裝 Windows 列印屬性工作表所提供的服務。

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

|名稱|描述|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容，而不會顯示 [列印] 對話方塊。|
|[CPrintDialogEx::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選擇。|
|[CPrintDialogEx::GetCopies](#getcopies)|擷取要求的複本數目。|
|[CPrintDialogEx::GetDefaults](#getdefaults)|擷取裝置的預設值，而不會顯示對話方塊。|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|擷取目前選取的印表機裝置的名稱。|
|[CPrintDialogEx::GetDevMode](#getdevmode)|擷取`DEVMODE`結構。|
|[CPrintDialogEx::GetDriverName](#getdrivername)|擷取系統定莪印表機裝置驅動程式的名稱。|
|[CPrintDialogEx::GetPortName](#getportname)|擷取目前選取的印表機連接埠的名稱。|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|擷取印表機裝置內容控制代碼。|
|[CPrintDialogEx::PrintAll](#printall)|決定是否要列印的文件的所有頁面。|
|[CPrintDialogEx::PrintCollate](#printcollate)|決定是否自動分頁複製要求。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|決定是否要列印的文件目前的頁面。|
|[CPrintDialogEx::PrintRange](#printrange)|決定是否要列印指定的範圍的頁數。|
|[CPrintDialogEx::PrintSelection](#printselection)|決定是否要列印的目前選取項目。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|結構，用來自訂`CPrintDialogEx`物件。|

## <a name="remarks"></a>備註

您可以依賴的架構，來處理您的應用程式的列印程序的各個層面。 如需有關如何使用架構來處理列印工作的詳細資訊，請參閱[列印](../../mfc/printing.md)。

如果您希望應用程式來處理不需要架構的涉入的列印功能，您可以使用`CPrintDialogEx`「 現狀 」 類別的建構函式，也可以衍生自己的對話方塊類別從`CPrintDialogEx`和寫入的建構函式，以符合您的需求。 在任一情況下，這些對話方塊會表現標準的 MFC 對話方塊因為它們衍生自類別`CCommonDialog`。

若要使用`CPrintDialogEx`物件，請先建立物件使用`CPrintDialogEx`建構函式。 一旦建構的對話方塊中，您可以設定或修改中的任何值[m_pdex](#m_pdex)結構，以初始化對話方塊的控制項的值。 `m_pdex`結構的類型是[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa)。 如需有關此結構的詳細資訊，請參閱 Windows SDK。

如果您未提供您自己的控制代碼，在`m_pdex`for`hDevMode`和`hDevNames`成員，務必呼叫 Windows 函式`GlobalFree`完成對話方塊時，這些控制代碼。

在初始化對話方塊的控制項之後, 呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者選取列印選項。 當`DoModal`傳回時，您可以判斷使用者是否已選取 [確定]、 [套用] 或 [取消] 按鈕。

如果使用者按下 [確定]，您可以使用`CPrintDialogEx`的成員函式來擷取使用者所輸入的資訊。

`CPrintDialogEx::GetDefaults`成員函式可用於擷取目前的印表機預設值，而不會顯示對話方塊。 此方法需要任何使用者互動。

您可以使用 Windows`CommDlgExtendedError`函式來判斷是否在對話方塊的初始化期間發生錯誤，以及了解錯誤的詳細資訊。 如需有關這個函式的詳細資訊，請參閱 Windows SDK。

如需有關使用`CPrintDialogEx`，請參閱 <<c2> [ 通用對話方塊類別](../../mfc/common-dialog-classes.md)。

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

**標頭：** afxdlgs.h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

建構 Windows 列印屬性工作表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
您可以使用自訂設定的對話方塊中，使用位元的 OR 運算子結合的一或多個標幟。 比方說，PD_ALLPAGES 旗標會將預設的列印範圍設定至文件的所有頁面。 請參閱[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa)如需有關這些旗標的 Windows SDK 中的結構。

*pParentWnd*<br/>
對話方塊的父代或擁有者視窗的指標。

### <a name="remarks"></a>備註

此成員函式只會建構物件。 使用`DoModal`成員函式來顯示對話方塊。

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

從建立印表機裝置內容 (DC) [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)並[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

新建立的印表機裝置內容的控制代碼。

### <a name="remarks"></a>備註

傳回的 DC 也會儲存在`hDC`隸屬[m_pdex](#m_pdex)。

此 DC 會假設為目前的印表機 DC，和任何其他先前取得的網域控制站必須先刪除的印表機。 可以呼叫此函式，並使用產生的 DC，而不會不斷顯示 [列印] 對話方塊。

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

呼叫此函式，以顯示 Windows 列印屬性工作表，並允許使用者選取各種列印選項，例如 份數，頁面範圍，以及是否應該自動分頁副本。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

INT_PTR 傳回值是實際的 HRESULT。 請參閱中的傳回值 」 一節[PrintDlgEx](https://msdn.microsoft.com/library/windows/desktop/ms646942) Windows SDK 中。

### <a name="remarks"></a>備註

如果您想要設定的成員初始化的各種不同的列印對話方塊選項`m_pdex`結構中，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。

之後呼叫`DoModal`，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者的資訊輸入。

如果呼叫時使用 PD_RETURNDC 旗標，則`DoModal`，將會傳回是印表機 DC`hDC`的成員[m_pdex](#m_pdex)。 此 DC 必須藉由呼叫釋放[DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc)的呼叫端`CPrintDialogEx`。

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

呼叫此函式之後呼叫`DoModal`擷取要求的份數。

```
int GetCopies() const;
```

### <a name="return-value"></a>傳回值

要求的複本數目。

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

呼叫此函式可擷取預設印表機的裝置預設值，而不會顯示對話方塊。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>傳回值

如果成功，否則為 FALSE，則為 TRUE。

### <a name="remarks"></a>備註

從建立印表機裝置內容 (DC) [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)並[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。

`GetDefaults` 不會顯示列印屬性工作表。 相反地，它會設定`hDevNames`和`hDevMode`的成員[m_pdex](#m_pdex)來控制代碼[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)並[DEVNAMES](../../mfc/reference/devnames-structure.md)結構初始化進行系統預設的印表機。 兩者`hDevNames`並`hDevMode`必須是 NULL，或`GetDefaults`失敗。

如果設定 PD_RETURNDC 旗標，這個函式不只會傳回`hDevNames`和`hDevMode`(位於`m_pdex.hDevNames`並`m_pdex.hDevMode`) 呼叫者，但也會傳回在是印表機 DC `m_pdex.hDC`。 刪除印表機 DC 並呼叫 Windows 呼叫端負責[GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree)函式的控制代碼，當您完成`CPrintDialogEx`物件。

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

呼叫此函式之後呼叫[DoModal](#domodal)來擷取目前選取的印表機，或之後呼叫的名稱[GetDefaults](#getdefaults)擷取預設印表機的名稱。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

目前選取的印表機名稱。

### <a name="remarks"></a>備註

使用指標`CString`所傳回的物件`GetDeviceName`的值為`lpszDeviceName`呼叫中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

呼叫此函式之後呼叫[DoModal](#domodal)或是[GetDefaults](#getdefaults)擷取列印裝置的相關資訊。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea)資料結構，其中包含裝置的初始設定和環境的列印驅動程式的相關資訊。 您必須解除鎖定這個結構與 Windows 所取用的記憶體[GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock)函式，Windows SDK 中所述。

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

呼叫此函式之後呼叫[DoModal](#domodal)或是[GetDefaults](#getdefaults)來擷取系統定莪印表機裝置驅動程式的名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

A`CString`指定系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

使用指標`CString`所傳回的物件`GetDriverName`的值為*lpszDriverName*的呼叫中[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

呼叫此函式之後呼叫[DoModal](#domodal)或是[GetDefaults](#getdefaults)來擷取目前選取的印表機連接埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

目前選取的印表機連接埠的名稱。

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

傳回印表機裝置內容控制代碼。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>傳回值

印表機裝置內容控制代碼。

### <a name="remarks"></a>備註

您必須呼叫 Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc)函式，當您完成時刪除裝置內容使用它。

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

PRINTDLGEX 結構，其成員儲存對話方塊物件的特性。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>備註

在建構之後`CPrintDialogEx`物件，您可以使用`m_pdex`若要設定的對話方塊中，然後再呼叫的各個層面[DoModal](#domodal)成員函式。 如需詳細資訊`m_pdex`結構，請參閱[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) Windows SDK 中。

如果您修改`m_pdex`資料成員直接，您將會覆寫任何預設行為。

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

呼叫此函式之後呼叫`DoModal`來判斷是否要列印文件中的所有頁面。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>傳回值

如果文件中的所有頁面都的列印，則為 TRUE否則為 FALSE。

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

呼叫此函式之後呼叫`DoModal`判斷印表機是否應該自動分頁文件的所有列印的副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>傳回值

如果使用者在對話方塊中，選取 [自動分頁] 核取方塊，則為 TRUE。否則為 FALSE。

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

呼叫此函式之後呼叫`DoModal`來判斷是否要列印文件中目前的頁面。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>傳回值

則為 TRUE**列印目前頁**已選取 [列印] 對話方塊中，否則為 FALSE。

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

呼叫此函式之後呼叫`DoModal`來判斷是否要列印的文件中的頁面範圍。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>傳回值

如果只有文件中的頁面範圍，則為要列印;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

指定的頁面範圍可以從決定[m_pdex](#m_pdex) (請參閱`nPageRanges`， `nMaxPageRanges`，並`lpPageRanges`中[PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) Windows SDK 中的結構)。

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

呼叫此函式之後呼叫`DoModal`來判斷是否要列印的目前選取項目。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>傳回值

如果只有選取的項目，則為要列印;，則為 TRUE。否則為 FALSE。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
