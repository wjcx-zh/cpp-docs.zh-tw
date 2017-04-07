---
title: "CPageSetupDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- page setup
- Print Setup dialog box
- Page Setup dialog box
- OLE Page Setup dialog box
- CPageSetupDialog class
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 81d36b3a005a291aca4c77dc9771a4fe92c304ee
ms.lasthandoff: 02/24/2017

---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog 類別
封裝 Windows 通用 OLE 版面設定對話方塊所提供的服務，以及設定和修改列印邊界的額外支援。  
  
## <a name="syntax"></a>語法  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|建構 `CPageSetupDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|建立裝置內容進行列印。|  
|[CPageSetupDialog::DoModal](#domodal)|顯示對話方塊，並允許使用者進行選取。|  
|[CPageSetupDialog::GetDeviceName](#getdevicename)|傳回印表機的裝置名稱。|  
|[CPageSetupDialog::GetDevMode](#getdevmode)|傳回目前`DEVMODE`的印表機。|  
|[CPageSetupDialog::GetDriverName](#getdrivername)|傳回由印表機驅動程式。|  
|[CPageSetupDialog::GetMargins](#getmargins)|傳回目前的邊界設定的印表機。|  
|[CPageSetupDialog::GetPaperSize](#getpapersize)|傳回印表機的紙張的大小。|  
|[CPageSetupDialog::GetPortName](#getportname)|傳回的輸出連接埠名稱。|  
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|要呈現列印頁面的螢幕影像架構呼叫。|  
|[CPageSetupDialog::PreDrawPage](#predrawpage)|由架構呼叫才能呈現螢幕影像列印的頁面。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPageSetupDialog::m_psd](#m_psd)|結構，用來自訂`CPageSetupDialog`物件。|  
  
## <a name="remarks"></a>備註  
 這個類別被設計來取代 [設定列印格式] 對話方塊。  
  
 若要使用`CPageSetupDialog`物件，請先建立物件使用`CPageSetupDialog`建構函式。 一旦建構的對話方塊中，您可以設定或修改中的任何值`m_psd`來初始化對話方塊的控制項值的資料成員。 [M_psd](#m_psd)結構的型別是**PAGESETUPDLG**。  
  
 初始化對話方塊的控制項之後, 呼叫`DoModal`成員函式來顯示對話方塊，並允許使用者選取列印選項。 `DoModal`傳回使用者是否已選取 確定 ( **IDOK**) 或 取消 ( **IDCANCEL**) 按鈕。  
  
 如果`DoModal`傳回**IDOK**，您可以使用數個`CPageSetupDialog`的成員函式或存取`m_psd`来擷取使用者輸入資訊的資料成員。  
  
> [!NOTE]
>  通用 OLE 版面設定對話方塊關閉之後，使用者所做的任何變更將不會儲存架構。 它是取決於應用程式本身儲存至永久的位置，例如應用程式的文件或應用程式類別的成員從這個對話方塊中任何值。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdlgs.h  
  
##  <a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog  
 呼叫此函式來建構`CPageSetupDialog`物件。  
  
```  
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 一或多個旗標可用於自訂的對話方塊中設定。 其值可以使用位元 OR 運算子結合。 這些值具有下列意義︰  
  
- **PSD_DEFAULTMINMARGINS**設定印表機的最小值相同的頁面邊界可允許最小寬度。 如果這個旗標則會忽略**PSD_MARGINS**和**PSD_MINMARGINS**也指定旗標。  
  
- **PSD_INWININIINTLMEASURE**未實作。  
  
- **PSD_MINMARGINS**會導致系統使用中指定的值**rtMinMargin**成員做為最小允許左側、 頂端、 右側和下邊界的寬度。 系統可防止使用者輸入小於指定的最小寬度。 如果**PSD_MINMARGINS**未指定，系統會將可允許的最小寬度設定所允許的印表機。  
  
- **PSD_MARGINS**啟動邊界控制項區域。  
  
- **PSD_INTHOUSANDTHSOFINCHES**會導致在對話方塊中的單位以英吋的 1/1000年。  
  
- **PSD_INHUNDREDTHSOFMILLIMETERS**會導致在對話方塊中的單位以 1/100 公釐。  
  
- **PSD_DISABLEMARGINS**停用邊界對話方塊的控制項。  
  
- **PSD_DISABLEPRINTER**停用 [印表機] 按鈕。  
  
- **PSD_NOWARNING**避免預設的印表機時顯示警告訊息。  
  
- **PSD_DISABLEORIENTATION**停用頁面方向對話方塊控制項。  
  
- **PSD_RETURNDEFAULT**造成`CPageSetupDialog`傳回[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)結構，而不會顯示一個對話方塊會初始化為系統預設的印表機。 它假設這兩個**hDevNames**和**hDevMode**是**NULL**; 否則此函數會傳回錯誤。 如果系統預設的印表機支援舊的印表機驅動程式 （早於 Windows 3.0 版） 只能**hDevNames**會傳回。**hDevMode** is **NULL**.  
  
- **PSD_DISABLEPAPER**停用的紙張選取控制項。  
  
- **PSD_SHOWHELP**讓對話方塊顯示 [說明] 按鈕。 **HwndOwner**成員不能**NULL**如果指定這個旗標。  
  
- **PSD_ENABLEPAGESETUPHOOK**啟用的攔截函式中指定**lpfnSetupHook**。  
  
- **PSD_ENABLEPAGESETUPTEMPLATE**造成作業系統來建立對話方塊中使用 [範本] 對話方塊來識別**hInstance**和**lpSetupTemplateName**。  
  
- **PSD_ENABLEPAGESETUPTEMPLATEHANDLE**表示**hInstance**識別包含預先載入的對話方塊範本的資料區塊。 系統會忽略**lpSetupTemplateName**如果指定這個旗標。  
  
- **PSD_ENABLEPAGEPAINTHOOK**啟用的攔截函式中指定**lpfnPagePaintHook**。  
  
- **PSD_DISABLEPAGEPAINTING**停用 對話方塊中的繪圖區域。  
  
 `pParentWnd`  
 對話方塊的父系或擁有者的指標。  
  
### <a name="remarks"></a>備註  
 使用[DoModal](../../mfc/reference/cdialog-class.md#domodal)函式，以顯示對話方塊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&94;](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC  
 建立印表機裝置內容從[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)和[DEVNAMES](../../mfc/reference/devnames-structure.md)結構。  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>傳回值  
 新建立的印表機裝置內容 (DC) 的控制代碼。  
  
##  <a name="domodal"></a>CPageSetupDialog::DoModal  
 呼叫此函式來顯示 Windows 通用 OLE 版面設定對話方塊中，並允許使用者選取各種列印設定選項，例如列印邊界、 大小和方向的紙張，以及目的地印表機。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**會傳回，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 **IDOK**和**IDCANCEL**都是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 此外，使用者可以存取印表機設定選項，例如網路位置和所選印表機的特定屬性。  
  
 如果您想要設定的成員初始化各種版面設定對話方塊選項`m_psd`結構應該這麼做之前，先呼叫`DoModal`，並建構對話方塊物件。 在呼叫`DoModal`，呼叫其他成員函式來擷取設定或使用者的資訊輸入到對話方塊。  
  
 如果您想要傳播目前使用者所輸入的設定，請呼叫[CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)。 此函式中的資訊`CPageSetupDialog`物件初始化，並選取新印表機 DC 使用適當的屬性。  
  
 [!code-cpp[NVC_MFCDocView #&95;](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]  
  
### <a name="example"></a>範例  
  請參閱範例[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。  
  
##  <a name="getdevicename"></a>CPageSetupDialog::GetDeviceName  
 呼叫此函式之後`DoModal`來擷取目前所選印表機的名稱。  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所使用的裝置名稱**CPageSetupDialog**物件。  
  
##  <a name="getdevmode"></a>CPageSetupDialog::GetDevMode  
 呼叫此函式之後呼叫`DoModal`擷取印表機裝置內容的相關資訊`CPageSetupDialog`物件。  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)資料結構，其中包含裝置初始化和列印驅動程式的環境的相關資訊。 您必須解除鎖定此結構與 Windows 所佔用的記憶體[GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595)函式中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getdrivername"></a>CPageSetupDialog::GetDriverName  
 呼叫此函式之後呼叫[DoModal](../../mfc/reference/cprintdialog-class.md#domodal)來擷取系統定義的印表機裝置驅動程式的名稱。  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`指定的系統定義的驅動程式名稱。  
  
### <a name="remarks"></a>備註  
 使用指標`CString`所傳回的物件`GetDriverName`的值為`lpszDriverName`呼叫[CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc)。  
  
##  <a name="getmargins"></a>CPageSetupDialog::GetMargins  
 呼叫此函式呼叫之後`DoModal`擷取印表機裝置驅動程式的邊界。  
  
```  
void GetMargins(
    LPRECT lpRectMargins,  
    LPRECT lpRectMinMargins) const;  
```  
  
### <a name="parameters"></a>參數  
 *lpRectMargins*  
 指標[RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)告訴您目前所選印表機的列印邊界 （以 1/1000年英吋或 1/100 公釐） 的物件。 傳遞**NULL**這個參數，如果您不想在這個矩形中。  
  
 *lpRectMinMargins*  
 指標`RECT`結構或`CRect`物件，描述 （在 1/1000年英吋或 1/100 公釐） 的最小目前選取的印表機列印邊界。 傳遞**NULL**這個參數，如果您不想在這個矩形中。  
  
##  <a name="getpapersize"></a>CPageSetupDialog::GetPaperSize  
 呼叫此函式可擷取選取要列印的紙張大小。  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含 （在 1/1000年英吋或 1/100 公釐） 列印選取的紙張大小。  
  
##  <a name="getportname"></a>CPageSetupDialog::GetPortName  
 呼叫此函式之後呼叫`DoModal`擷取目前選取的印表機連接埠的名稱。  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前選取的印表機連接埠的名稱。  
  
##  <a name="m_psd"></a>CPageSetupDialog::m_psd  
 型別的結構**PAGESETUPDLG**，其成員儲存對話方塊物件的特性。  
  
```  
PAGESETUPDLG m_psd;  
```  
  
### <a name="remarks"></a>備註  
 在建構之後`CPageSetupDialog`物件時，您可以使用`m_psd`設定 對話方塊中，然後再呼叫的各種層面`DoModal`成員函式。  
  
 如果您修改`m_psd`資料成員直接，您將會覆寫任何預設行為。  
  
 如需有關[PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842)結構，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 請參閱範例[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)。  
  
##  <a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage  
 要繪製列印頁面的螢幕影像架構呼叫。  
  
```  
virtual UINT OnDrawPage(
    CDC* pDC,  
    UINT nMessage,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 印表機裝置內容的指標。  
  
 `nMessage`  
 指定的訊息，指出頁面目前所繪製的區域。 可以是下列其中一項：  
  
- **WM_PSD_FULLPAGERECT**整個頁面區域。  
  
- **WM_PSD_MINMARGINRECT**目前的最小邊界。  
  
- **WM_PSD_MARGINRECT**目前邊界。  
  
- **WM_PSD_GREEKTEXTRECT**頁面的內容。  
  
- **WM_PSD_ENVSTAMPRECT**使用郵票表示法的保留區域。  
  
- **WM_PSD_YAFULLPAGERECT**傳回位址表示法的區域。 這個區域會擴充範例頁面區域的邊緣。  
  
 `lpRect`  
 指標[CRect](../../atl-mfc-shared/reference/crect-class.md)或[RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us)物件，其中包含在繪圖區域的座標。  
  
### <a name="return-value"></a>傳回值  
 非零值處理。否則為 0。  
  
### <a name="remarks"></a>備註  
 此映像，這時會顯示通用 OLE 版面設定對話方塊的一部分。 預設實作會繪製的文字頁面的影像。  
  
 覆寫這個函式來自訂特定區域的影像或整個影像繪製。 您可以使用`switch`陳述式搭配**案例**陳述式檢查的值`nMessage`。 例如，若要自訂內容的頁面影像轉譯，您可以使用下列範例程式碼︰  
  
 [!code-cpp[NVC_MFCDocView #&96;](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]  
  
 請注意，您不需要處理的每個案例`nMessage`。 您可以選擇要處理的映像的映像或整個區域的數個元件的一個元件。  
  
##  <a name="predrawpage"></a>CPageSetupDialog::PreDrawPage  
 繪製列印頁面的螢幕影像之前，由框架呼叫。  
  
```  
virtual UINT PreDrawPage(
    WORD wPaper,  
    WORD wFlags,  
    LPPAGESETUPDLG pPSD);
```  
  
### <a name="parameters"></a>參數  
 *wPaper*  
 指定值，指出紙張大小。 這個值可以是其中一個**DMPAPER_**值的描述中所列[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)結構。  
  
 `wFlags`  
 指出方向的紙張或信封，以及印表機是否為點陣或 HPPCL （Hewlett Packard 印表機控制語言） 裝置。 這個參數的值可以是下列其中一個：  
  
-   0x001 紙張以橫向模式 （點陣式）  
  
-   0x003 紙張以橫向模式 (HPPCL)  
  
-   0x005 紙張直向模式 （點陣式）  
  
-   0x007 紙張直向模式 (HPPCL)  
  
-   0x00b 信封以橫向模式 (HPPCL)  
  
-   0x00d 信封以直向模式 （點陣式）  
  
-   0x019 信封以橫向模式 （點陣式）  
  
-   0x01f 信封以直向模式 （點陣式）  
  
 `pPSD`  
 指標**PAGESETUPDLG**結構。 如需有關[PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842)，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 非零值處理。否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來自訂繪製影像。 如果您覆寫這個函式，並傳回**TRUE**，您必須繪製整個影像。 如果您覆寫這個函式，並傳回**FALSE**，由架構繪製整個預設影像。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 WORDPAD](../../visual-cpp-samples.md)   
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




