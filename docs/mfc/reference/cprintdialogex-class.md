---
title: CPrintDialogEx 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f511eb1414a5cd5e22b9a3e05f81caef15b908e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376642"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx 類別
封裝 Windows 列印屬性工作表提供的服務。  
  
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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容而不會顯示 [列印] 對話方塊。|  
|[CPrintDialogEx::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選擇。|  
|[CPrintDialogEx::GetCopies](#getcopies)|擷取要求的份數。|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|擷取裝置的預設值，而不顯示對話方塊。|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|擷取目前選取的印表機裝置名稱。|  
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
 您可以依賴架構，以處理您的應用程式的列印程序的許多層面。 如需使用架構來處理列印工作的詳細資訊，請參閱文章[列印](../../mfc/printing.md)。  
  
 如果您希望應用程式來處理不需要的 framework 涉入列印，您可以使用`CPrintDialogEx`類別 「 現況 」 提供，建構函式，或您可以衍生您自己的對話方塊類別從`CPrintDialogEx`和寫入以符合您需求的建構函式。 在任一情況下，這些對話方塊的行為類似標準 MFC 對話方塊因為它們都衍生自類別`CCommonDialog`。  
  
 若要使用`CPrintDialogEx`物件，請先建立物件使用`CPrintDialogEx`建構函式。 一旦建構的對話方塊中，您可以設定或修改中的任何值[m_pdex](#m_pdex)結構，以初始化對話方塊的控制項的值。 `m_pdex`結構的類型是[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)。 如需有關此結構的詳細資訊，請參閱 Windows SDK。  
  
 如果您未提供您自己的控制代碼中`m_pdex`如**hDevMode**和**hDevNames**成員，請務必呼叫 Windows 函式**GlobalFree**適用於這些控制代碼當您完成對話方塊。  
  
 初始化對話方塊控制項之後呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者選取列印選項。 當`DoModal`傳回時，您可以判斷使用者是否選取 確定，套用 或 取消 按鈕。  
  
 如果使用者按下 [確定]，您可以使用`CPrintDialogEx`的成員函式來擷取使用者輸入的資訊。  
  
 `CPrintDialogEx::GetDefaults`成員函式可用於擷取目前的印表機預設值，而不顯示對話方塊。 這個方法不需要使用者互動。  
  
 您可以使用 Windows **CommDlgExtendedError**函式判斷是否在對話方塊的初始化期間發生錯誤，並深入了解錯誤。 如需有關此函式的詳細資訊，請參閱 Windows SDK。  
  
 如需有關使用`CPrintDialogEx`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
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
 `dwFlags`  
 一或多個旗標可用於自訂的對話方塊中，使用位元 OR 運算子結合在一起設定。 例如， **PD_ALLPAGES**旗標設定的預設列印範圍到文件的所有頁面。 請參閱[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844)如需有關這些旗標的 Windows SDK 中的結構。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者視窗的指標。  
  
### <a name="remarks"></a>備註  
 此成員函式只會建構物件。 使用`DoModal`成員函式來顯示對話方塊。  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 建立印表機裝置內容 (DC) 從[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>傳回值  
 新建立的印表機裝置內容的控制代碼。  
  
### <a name="remarks"></a>備註  
 傳回的 DC 也會儲存在**hDC**隸屬[m_pdex](#m_pdex)。  
  
 此 DC 會假設為目前的印表機 DC，和任何其他之前取得網域控制站，必須先刪除的印表機。 可以呼叫此函式，並使用產生的 DC，而不會永遠顯示 [列印] 對話方塊。  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 呼叫此函式，以顯示 Windows 列印屬性工作表，並允許使用者選取各種列印選項，例如複製，頁面範圍的數目以及是否應該自動分頁副本。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 INT_PTR 傳回值是實際的 HRESULT。 請參閱中的傳回值 」 一節[PrintDlgEx](http://msdn.microsoft.com/library/windows/desktop/ms646942) Windows SDK 中。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種列印對話方塊選項`m_pdex`結構，您應該這麼做會在呼叫之前`DoModal`，但在建構對話方塊物件之後。  
  
 在呼叫`DoModal`，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者資訊輸入。  
  
 如果**PD_RETURNDC**呼叫時，會使用旗標`DoModal`，是印表機 DC 將會傳回**hDC**隸屬[m_pdex](#m_pdex)。 此 DC 必須釋放呼叫[DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)的呼叫端所`CPrintDialogEx`。  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 呼叫此函式之後呼叫`DoModal`擷取要求的份數。  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>傳回值  
 複製要求數目。  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 呼叫此函式可擷取預設印表機的裝置預設值，而不顯示對話方塊。  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果成功，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 建立印表機裝置內容 (DC) 從[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。  
  
 `GetDefaults` 不會顯示列印屬性工作表。 相反地，它會設定**hDevNames**和**hDevMode**成員[m_pdex](#m_pdex)的控制代碼[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)會初始化為系統預設的印表機的結構。 同時**hDevNames**和**hDevMode**必須是 NULL，或`GetDefaults`失敗。  
  
 如果**PD_RETURNDC**設定旗標，此函式不會只傳回**hDevNames**和**hDevMode** (位於**m_pdex.hDevNames**和**m_pdex.hDevMode**) 給呼叫者，但也會傳回的印表機 DC **m_pdex.hDC**。 刪除印表機 DC 並呼叫 Windows 呼叫端負責[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)函式上的控制代碼，當您完成`CPrintDialogEx`物件。  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 呼叫此函式之後呼叫[DoModal](#domodal)擷取名稱目前選取的印表機，或之後呼叫[GetDefaults](#getdefaults)擷取預設印表機的名稱。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的印表機名稱。  
  
### <a name="remarks"></a>備註  
 使用指標`CString`所傳回物件`GetDeviceName`做為值`lpszDeviceName`呼叫[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取列印裝置的相關資訊。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)資料結構，其中包含裝置初始化和環境的列印驅動程式的相關資訊。 您必須解除鎖定這個 Windows 結構的記憶體[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函式，Windows SDK 中所述。  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取系統定莪印表機裝置驅動程式的名稱。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`指定系統定莪驅動程式名稱。  
  
### <a name="remarks"></a>備註  
 使用指標`CString`所傳回物件`GetDriverName`做為值`lpszDriverName`呼叫[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取目前選取的印表機連接埠的名稱。  
  
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
 您必須呼叫 Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)函式來刪除的裝置內容，當您在使用它。  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 PRINTDLGEX 結構，其成員儲存對話方塊物件的特性。  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>備註  
 之後建構`CPrintDialogEx`物件，您可以使用`m_pdex`設定對話方塊中，會在呼叫之前的各個層面[DoModal](#domodal)成員函式。 如需有關`m_pdex`結構，請參閱[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) Windows SDK 中。  
  
 如果您修改`m_pdex`資料成員直接管理，您將會覆寫任何預設行為。  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印文件中的所有頁面。  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**文件中的所有頁面都的列印，否則如果**FALSE**。  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 呼叫此函式之後呼叫`DoModal`判斷印表機是否應該自動分頁文件的所有列印的副本。  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果使用者選取 自動分頁 核取方塊 對話方塊中; 否則**FALSE**。  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印文件中目前的頁面。  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果**列印本頁**已選取 [列印] 對話方塊中，否則**FALSE**。  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印的文件中的頁面範圍。  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果只有一個範圍的文件中的頁列印，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 指定的頁面範圍可由[m_pdex](#m_pdex) (請參閱**nPageRanges**， **nMaxPageRanges**，和**lpPageRanges** 中[PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) Windows SDK 中的結構)。  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印的目前選取項目。  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果只有選取的項目列印，否則**FALSE**。  
  
## <a name="see-also"></a>另請參閱  
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
