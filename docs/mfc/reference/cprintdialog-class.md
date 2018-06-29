---
title: CPrintDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d72b96e0be786aab18903e95f346eccd5364dd4b
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079644"
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
  
|名稱|描述|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|建立印表機裝置內容而不會顯示 [列印] 對話方塊。|  
|[CPrintDialog::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選取。|  
|[CPrintDialog::GetCopies](#getcopies)|擷取要求的份數。|  
|[CPrintDialog::GetDefaults](#getdefaults)|擷取裝置的預設值，而不顯示對話方塊。|  
|[CPrintDialog::GetDeviceName](#getdevicename)|擷取目前選取的印表機裝置名稱。|  
|[CPrintDialog::GetDevMode](#getdevmode)|擷取`DEVMODE`結構。|  
|[CPrintDialog::GetDriverName](#getdrivername)|擷取目前選取的印表機驅動程式的名稱。|  
|[CPrintDialog::GetFromPage](#getfrompage)|擷取列印範圍的起始頁面。|  
|[CPrintDialog::GetPortName](#getportname)|擷取目前選取的印表機連接埠的名稱。|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|擷取印表機裝置內容控制代碼。|  
|[CPrintDialog::GetToPage](#gettopage)|擷取列印範圍的結束頁面。|  
|[CPrintDialog::PrintAll](#printall)|決定是否要列印的文件的所有頁面。|  
|[CPrintDialog::PrintCollate](#printcollate)|決定是否自動分頁複製要求。|  
|[CPrintDialog::PrintRange](#printrange)|決定是否要列印指定的範圍的頁數。|  
|[CPrintDialog::PrintSelection](#printselection)|決定是否要列印的目前選取項目。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|結構，用來自訂`CPrintDialog`物件。|  
  
## <a name="remarks"></a>備註  
 通用列印對話方塊提供簡單的方式與 Windows 標準一致的方式實作列印和列印 對話方塊。  
  
> [!NOTE]
>  `CPrintDialogEx`類別會封裝 Windows 列印屬性工作表中所提供的服務。 如需詳細資訊，請參閱[CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)概觀。  
  
 `CPrintDialog`功能程式的取代[CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)，它設計為您提供的通用對話方塊中，針對同時列印設定和 版面設定。  
  
 您可以依賴架構，以處理您的應用程式的列印程序的許多層面。 在此情況下，架構會自動顯示列印的 Windows 通用對話方塊。 您也可以有列印您的應用程式的架構控制代碼，而覆寫通用列印對話方塊中，使用您自己的列印對話方塊。 如需使用架構來處理列印工作的詳細資訊，請參閱文章[列印](../../mfc/printing.md)。  
  
 如果您希望應用程式來處理不需要的 framework 涉入列印，您可以使用`CPrintDialog`類別 「 現況 」 提供，建構函式，或您可以衍生您自己的對話方塊類別從`CPrintDialog`和寫入以符合您需求的建構函式。 在任一情況下，這些對話方塊的行為類似標準 MFC 對話方塊因為它們都衍生自類別`CCommonDialog`。  
  
 若要使用`CPrintDialog`物件，請先建立物件使用`CPrintDialog`建構函式。 一旦建構的對話方塊中，您可以設定或修改中的任何值[m_pd](#m_pd)結構，以初始化對話方塊的控制項的值。 `m_pd`結構的類型是[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)。 如需有關此結構的詳細資訊，請參閱 Windows SDK。  
  
 如果您未提供您自己的控制代碼中`m_pd`如**hDevMode**和**hDevNames**成員，請務必呼叫 Windows 函式**GlobalFree**適用於這些控制代碼當您完成對話方塊。 當使用所提供的架構的列印設定實作`CWinApp::OnFilePrintSetup`，您沒有釋放這些控制代碼。 控點由維護`CWinApp`會釋出和`CWinApp`的解構函式。 時才需要使用時釋放這些控制代碼`CPrintDialog`獨立。  
  
 初始化對話方塊控制項之後呼叫`DoModal`成員函式，以顯示對話方塊，並允許使用者選取列印選項。 `DoModal` 傳回使用者是否選取 [確定] \( **IDOK**) 或 [取消] \( **IDCANCEL**) 按鈕。  
  
 如果`DoModal`傳回**IDOK**，您可以使用其中一個`CPrintDialog`的成員函式來擷取使用者輸入的資訊。  
  
 `CPrintDialog::GetDefaults`成員函式可用於擷取目前的印表機預設值，而不顯示對話方塊。 此成員函式不需要使用者互動。  
  
 您可以使用 Windows **CommDlgExtendedError**函式判斷是否在對話方塊的初始化期間發生錯誤，並深入了解錯誤。 如需有關此函式的詳細資訊，請參閱 Windows SDK。  
  
 `CPrintDialog` 依賴 COMMDLG。隨附於 Windows 版本 3.1 和更新版本的 DLL 檔案。  
  
 若要自訂對話方塊中，衍生自`CPrintDialog`，提供自訂對話方塊範本中，加入處理從擴充的控制項通知訊息的訊息對應。 任何未處理的訊息應該傳遞給基底類別。 自訂攔截函式不需要。  
  
 若要處理相同的訊息，以不同的方式根據對話方塊是列印] 或 [列印設定，您必須衍生每個對話方塊中的類別。 您也必須覆寫 Windows **AttachOnSetup**函式，用來處理新的對話方塊建立列印 對話方塊內選取 設定列印格式 按鈕時。  
  
 如需有關使用`CPrintDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdlgs.h  
  
##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog  
 建構的 Windows 列印 」 或 「 列印設定對話方塊物件。  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *bPrintSetupOnly*  
 指定是否顯示標準的 Windows 列印對話方塊或 [設定列印格式] 對話方塊。 這個參數設定為**TRUE**顯示標準的 [Windows 設定列印格式] 對話方塊。 將它設定為**FALSE**顯示 Windows 列印 對話方塊。 如果*bPrintSetupOnly*是**FALSE**，設定列印格式 選項按鈕仍會顯示在 列印 對話方塊。  
  
 *dwFlags*  
 一或多個旗標可用於自訂的對話方塊中，使用位元 OR 運算子結合在一起設定。 例如， **PD_ALLPAGES**旗標設定的預設列印範圍到文件的所有頁面。 請參閱[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)如需有關這些旗標的 Windows SDK 中的結構。  
  
 *pParentWnd*  
 對話方塊的父系或擁有者視窗的指標。  
  
### <a name="remarks"></a>備註  
 此成員函式只會建構物件。 使用`DoModal`成員函式來顯示對話方塊。  
  
 請注意，當您呼叫具有建構函式`bPrintSetupOnly`設**FALSE**、 **PD_RETURNDC**旗標會自動使用。 在呼叫`DoModal`， `GetDefaults`，或`GetPrinterDC`，是印表機 DC 將會傳回`m_pd.hDC`。 此 DC 必須釋放呼叫[DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)的呼叫端所`CPrintDialog`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC  
 建立印表機裝置內容 (DC) 從[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>傳回值  
 新建立的印表機裝置內容的控制代碼。  
  
### <a name="remarks"></a>備註  
 此 DC 會假設為目前的印表機 DC，和任何其他之前取得網域控制站必須先刪除使用者的印表機。 可以呼叫此函式，並使用產生的 DC，而不會永遠顯示 [列印] 對話方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>  CPrintDialog::DoModal  
 顯示 Windows 通用列印對話方塊，並允許使用者選取各種列印選項，例如 份數，頁面範圍，以及是否應該自動分頁副本。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**是傳回，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 **IDOK**和**IDCANCEL**是常數，以指出使用者是否選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種列印對話方塊選項`m_pd`結構，您應該這麼做會在呼叫之前`DoModal`，但在建構對話方塊物件之後。  
  
 在呼叫`DoModal`，您可以呼叫其他成員函式來擷取在對話方塊中的 設定 或 使用者資訊輸入。  
  
 請注意，當您呼叫具有建構函式*bPrintSetupOnly*設**FALSE**、 **PD_RETURNDC**旗標會自動使用。 在呼叫`DoModal`， `GetDefaults`，或`GetPrinterDC`，是印表機 DC 將會傳回`m_pd.hDC`。 此 DC 必須釋放呼叫[DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)的呼叫端所`CPrintDialog`。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::CreatePrinterDC](#createprinterdc)。  
  
##  <a name="getcopies"></a>  CPrintDialog::GetCopies  
 擷取要求的份數。  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>傳回值  
 複製要求數目。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`擷取要求的份數。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults  
 擷取裝置的預設值的預設印表機，而不顯示對話方塊。  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 擷取的值會放在`m_pd`結構。  
  
 在某些情況下，會呼叫此函式的呼叫[建構函式](#cprintdialog)如`CPrintDialog`與*bPrintSetupOnly*設**FALSE**。 在這些情況下，是印表機 DC 和**hDevNames**和**hDevMode** (兩個控點位於`m_pd`資料成員) 會自動配置。  
  
 如果建構函式`CPrintDialog`呼叫`bPrintSetupOnly`設**FALSE**，此函式不只會傳回**hDevNames**和**hDevMode** （位於**m_pd.hDevNames**和**m_pd.hDevMode**) 給呼叫者，但也會傳回的印表機 DC **m_pd.hDC**。 刪除印表機 DC 並呼叫 Windows 呼叫端負責[GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)函式上的控制代碼，當您完成`CPrintDialog`物件。  
  
### <a name="example"></a>範例  
 此程式碼片段會取得預設的印表機裝置內容，並向使用者回報每英吋印表機解析度。 （此屬性的印表機的功能通常稱為 DPI。）  
  
 [!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName  
 擷取目前選取的印表機裝置名稱。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的印表機名稱。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫[DoModal](#domodal)擷取名稱目前選取的印表機，或之後呼叫[GetDefaults](#getdefaults)擷取目前的預設印表機的裝置預設值。 使用指標`CString`所傳回物件`GetDeviceName`做為值`lpszDeviceName`呼叫[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>範例  
 此程式碼片段會顯示使用者的預設印表機名稱和連線，以及多工緩衝處理器名稱印表機要使用的連接埠。 程式碼可能會顯示訊息方塊，指出 「 預設印表機位於 HP LaserJet IIIP \\\server\share 使用 winspool。 」，例如。  
  
 [!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode  
 擷取`DEVMODE`結構。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)資料結構，其中包含裝置初始化和環境的列印驅動程式的相關資訊。 您必須解除鎖定這個 Windows 結構的記憶體[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函式，Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取列印裝置的相關資訊。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::PrintCollate](#printcollate)。  
  
##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName  
 擷取目前選取的印表機驅動程式的名稱。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`指定系統定莪驅動程式名稱。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取系統定莪印表機裝置驅動程式的名稱。 使用指標`CString`所傳回物件`GetDriverName`做為值`lpszDriverName`呼叫[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage  
 擷取列印範圍的起始頁面。  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 起始頁碼範圍中要列印的頁面。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`來擷取要列印的頁面範圍中，起始頁碼。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="getportname"></a>  CPrintDialog::GetPortName  
 擷取目前選取的印表機連接埠的名稱。  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的印表機連接埠的名稱。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫[DoModal](#domodal)或[GetDefaults](#getdefaults)擷取目前選取的印表機連接埠的名稱。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::GetDeviceName](#getdevicename)。  
  
##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC  
 擷取印表機裝置內容控制代碼。  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>傳回值  
 成功; 如果印表機裝置內容控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果*bPrintSetupOnly*參數`CPrintDialog`建構函式已**FALSE** （表示會顯示 [列印] 對話方塊），然後`GetPrinterDC`印表機裝置傳回的控制代碼內容。 您必須呼叫 Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533)函式來刪除的裝置內容，當您在使用它。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>  CPrintDialog::GetToPage  
 擷取列印範圍的結束頁面。  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 結束頁碼範圍中要列印的頁面。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`來擷取要列印的頁面範圍，結束頁碼。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="m_pd"></a>  CPrintDialog::m_pd  
 結構，其成員儲存對話方塊物件的特性。  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>備註  
 之後建構`CPrintDialog`物件，您可以使用`m_pd`設定對話方塊中，會在呼叫之前的各個層面[DoModal](#domodal)成員函式。 如需有關`m_pd`結構，請參閱[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) Windows SDK 中。  
  
 如果您修改`m_pd`資料成員直接管理，您將會覆寫任何預設行為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>  CPrintDialog::PrintAll  
 決定是否要列印的文件的所有頁面。  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果文件中的所有頁面都的列印。否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印文件中的所有頁面。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="printcollate"></a>  CPrintDialog::PrintCollate  
 決定是否自動分頁複製要求。  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果使用者在對話方塊中，選取 [自動分頁] 核取方塊否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`判斷印表機是否應該自動分頁文件的所有列印的副本。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>  CPrintDialog::PrintRange  
 決定是否要列印指定的範圍的頁數。  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果只在文件中的頁面範圍的列印。否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印的文件中的頁面範圍。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::m_pd](#m_pd)。  
  
##  <a name="printselection"></a>  CPrintDialog::PrintSelection  
 決定是否要列印的目前選取項目。  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果只有選取的項目列印。否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後呼叫`DoModal`來判斷是否要列印的目前選取項目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPrintDialog::m_pd](#m_pd)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPrintInfo 結構](../../mfc/reference/cprintinfo-structure.md)
