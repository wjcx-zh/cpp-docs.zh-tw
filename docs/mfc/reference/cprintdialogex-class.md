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
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364034"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 類別

封裝 Windows 列印屬性表提供的服務。

## <a name="syntax"></a>語法

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPrint對話Ex:CPrintDialogEx](#cprintdialogex)|建構 `CPrintDialogEx` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPrint 對話Ex:建立印表機DC](#createprinterdc)|建立印表機裝置上下文而不顯示「列印」對話框。|
|[CPrintDialogEx::Do模態](#domodal)|顯示對話框,並允許用戶進行選擇。|
|[CPrint對話Ex:取得複本](#getcopies)|檢索請求的副本數。|
|[CPrint 對話Ex:取得預設](#getdefaults)|檢索設備預設值而不顯示對話方塊。|
|[CPrint 對話Ex:取得裝置名稱](#getdevicename)|檢索當前選擇的印表機裝置的名稱。|
|[CPrint對話前:取得DevMode](#getdevmode)|檢索`DEVMODE`結構。|
|[CPrint 對話Ex:取得驅動程式名稱](#getdrivername)|檢索系統定義的印表機設備驅動程式的名稱。|
|[CPrint 對話Ex:取得連接埠名稱](#getportname)|檢索當前選擇的印表機埠的名稱。|
|[CPrint 對話Ex:取得印表機DC](#getprinterdc)|檢索印表機設備上下文的句柄。|
|[CPrintDialogEx::PrintAll](#printall)|確定是否列印文件的所有頁面。|
|[CPrintDialogEx::Printcollate](#printcollate)|確定是否請求整理副本。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|確定是否列印文件的當前頁面。|
|[CPrintDialogEx::PrintRange](#printrange)|確定是否僅列印指定的頁面範圍。|
|[CPrintDialogEx::Print選擇](#printselection)|確定是否僅列印當前選定的專案。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPrint對話Ex::m_pdex](#m_pdex)|定義物件的結構`CPrintDialogEx`。|

## <a name="remarks"></a>備註

您可以依賴框架來處理應用程式的列印過程的許多方面。 有關使用框架處理列印任務的詳細資訊,請參閱文章[「列印](../../mfc/printing.md)」。

如果希望應用程式在沒有框架參與的情況下處理列印,則可以將`CPrintDialogEx`類"按照"與提供的構造函數一起使用,也可以從`CPrintDialogEx`派生自己的對話方塊類並編寫構造函數以滿足您的需要。 在這兩種情況下,這些對話框將類似於標準 MFC 對話框,因為它們派生`CCommonDialog`自類 。

要使用`CPrintDialogEx`物件,請首先`CPrintDialogEx`使用 建構函數創建物件。 建構對話框後,可以設置或修改[m_pdex](#m_pdex)結構中的任何值,以初始化對話方塊控制項的值。 結構`m_pdex`為[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)型。 有關此結構的詳細資訊,請參閱 Windows SDK。

如果不`m_pdex``hDevMode`為`hDevNames`和 成員提供自己的句柄,請確保在使用對話框後調用這些句柄的`GlobalFree`Windows 函數。

初始化對話方塊控制項後,呼`DoModal`叫成員函數以顯示對話方塊,並允許使用者選擇列印選項。 返回`DoModal`時,您可以確定使用者是否選擇了"確定"、"應用"或"取消"按鈕。

如果使用者按"確定",則可以使用`CPrintDialogEx`的成員函數檢索用戶輸入的資訊。

成員`CPrintDialogEx::GetDefaults`函數可用於檢索當前印表機預設值,而不顯示對話方塊。 此方法不需要使用者交互。

可以使用 Windows`CommDlgExtendedError`函數確定在對話方塊初始化期間是否發生了錯誤,並瞭解有關該錯誤的詳細資訊。 有關此功能的詳細資訊,請參閱 Windows SDK。

有關`CPrintDialogEx`使用的詳細資訊,請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrint對話Ex:CPrintDialogEx

構造 Windows 列印屬性表。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
可以使用一個或多個標誌自定義對話框的設置,使用位或運算符組合使用。 例如,PD_ALLPAGES標誌將預設列印範圍設置到文檔的所有頁面。 有關這些標誌的詳細資訊,請參閱 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)結構。

*pparentwnd*<br/>
指向對話框的父視窗或所有者視窗的指標。

### <a name="remarks"></a>備註

此成員函數僅構造物件。 使用`DoModal`成員函數顯示對話方塊。

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrint 對話Ex:建立印表機DC

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構創建印表機裝置上下文 (DC)。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>傳回值

處理新創建的印表機設備上下文。

### <a name="remarks"></a>備註

返回的 DC 也`hDC`存儲在[m_pdex](#m_pdex)的成員中。

此 DC 假定為當前印表機 DC,必須刪除以前獲得的任何其他印表機 DC。 可以調用此功能,並使用生成的 DC,而無需顯示「列印」對話方塊。

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::Do模態

呼叫此函數以顯示 Windows Print 屬性表,並允許使用者選擇各種列印選項,如副本數、頁面範圍以及是否應整理副本。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

INT_PTR返回值實際上是一個 HRESULT。 請參閱 Windows SDK 中的[PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\))中的「返回值」 部分。

### <a name="remarks"></a>備註

如果要通過設置`m_pdex`結構成員來初始化各種列印對話方塊選項,則應在`DoModal`調用 之前執行此操作,但在構造對話框物件之後。

調用`DoModal`後 ,可以調用其他成員函數來檢索使用者輸入到對話方塊中的設置或資訊。

如果在調用`DoModal`時使用PD_RETURNDC標誌,則印表機`hDC`DC 將在[m_pdex](#m_pdex)的成員中返回。 此 DC`CPrintDialogEx`必須透過調用的[DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)釋放。

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrint對話Ex:取得複本

調用`DoModal`後調用此函數以檢索請求的副本數。

```
int GetCopies() const;
```

### <a name="return-value"></a>傳回值

請求的副本數。

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrint 對話Ex:取得預設

呼叫此函數以檢索預設印表機的設備預設值,而不顯示對話方塊。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>傳回值

如果成功,則為 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

從[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構創建印表機裝置上下文 (DC)。

`GetDefaults`不顯示"列印"屬性表。 `hDevNames`相反,它將[m_pdex](#m_pdex)`hDevMode`和成員設置以處理為系統預設印表機初始化的[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)和[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)結構。 和`hDevNames``hDevMode`都必須為 NULL,`GetDefaults`否則。

如果`hDevNames`設置了PD_RETURNDC標誌,此函數不僅會返回和`hDevMode`(`m_pdex.hDevNames`位於`m_pdex.hDevMode`和) 到調用方,而且還`m_pdex.hDC`將在中返回印表機 DC。 呼叫者負責移除印表機 DC,`CPrintDialogEx`並在處理 完物件後調用句柄上的 Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)函數。

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrint 對話Ex:取得裝置名稱

在調用[DoModal](#domodal)以檢索目前所選印表機的名稱後,或調用[GetDefaults](#getdefaults)以檢索預設印表機的名稱後調用此函數。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>傳回值

當前選定的印表機的名稱。

### <a name="remarks"></a>備註

`CString`使用指向返回`GetDeviceName`的物件的指標作為 調用`lpszDeviceName`[CDC:::createDC](../../mfc/reference/cdc-class.md#createdc)中的值。

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrint對話前:取得DevMode

呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)後呼叫此功能以檢索有關列印裝置的資訊。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>傳回值

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)資料結構,其中包含有關列印驅動程序的設備初始化和環境的資訊。 您必須使用 Windows[全域解鎖](/windows/win32/api/winbase/nf-winbase-globalunlock)功能解鎖此結構佔用的記憶體,該功能在 Windows SDK 中進行了描述。

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrint 對話Ex:取得驅動程式名稱

呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)後呼叫此功能以檢索系統定義的印表機裝置驅動程式的名稱。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>傳回值

指定`CString`系統定義的驅動程式名稱。

### <a name="remarks"></a>備註

在調用[CDC:::createDC](../../mfc/reference/cdc-class.md#createdc)中,使用作為*lpszDriverName*的值傳回`CString``GetDriverName`的物件的指標。

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrint 對話Ex:取得連接埠名稱

呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)後呼叫此功能以檢索目前選取的印表機埠的名稱。

```
CString GetPortName() const;
```

### <a name="return-value"></a>傳回值

當前選定的印表機埠的名稱。

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrint 對話Ex:取得印表機DC

將句柄返回到印表機設備上下文。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>傳回值

印表機裝置上下文的句柄。

### <a name="remarks"></a>備註

使用完 Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)函數後,必須調用該函數以刪除設備上下文。

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrint對話Ex::m_pdex

一個 PRINTDLGEX 結構,其成員存儲對話框物件的特徵。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>備註

建構`CPrintDialogEx`物件後,可以`m_pdex`使用 在調用[DoModal](#domodal)成員函數之前設置對話框的各個方面。 有關`m_pdex`結構的詳細資訊,請參閱 Windows SDK 中的[PRINTDLGEX。](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)

如果直接修改`m_pdex`數據成員,將覆蓋任何默認行為。

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

呼叫`DoModal`後呼叫此功能以確定是否列印文件中的所有頁面。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>傳回值

如果要列印文檔中的所有頁面,則為 TRUE;否則 FALSE。

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::Printcollate

呼叫`DoModal`後呼叫此功能以確定印表機是否應整理文件的所有列印副本。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>傳回值

如果用戶在對話框中選擇「校對」複選框,則為 TRUE;否則 FALSE。

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

呼叫`DoModal`後呼叫此函數以確定是否在文件中列印當前頁面。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>傳回值

如果在列印對話框中選擇「列印目前頁面」,則為 TRUE;如果列印對話框中選擇了 **「列印當前頁面**」,則為 TRUE。否則 FALSE。

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

呼叫`DoModal`後呼叫此功能以確定是否僅列印文檔中的一系列頁面。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>傳回值

如果只列印文檔中的一系列頁面,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

指定的頁面範圍可以從[m_pdex(](#m_pdex)請`nPageRanges`參`nMaxPageRanges`閱`lpPageRanges`) 和 在 Windows SDK 中的[PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)結構中確定。

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::Print選擇

呼叫`DoModal`後呼叫此函數以確定是否僅列印當前選定的專案。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>傳回值

如果只列印所選專案,則為 TRUE;否則 FALSE。

## <a name="see-also"></a>另請參閱

[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
