---
title: "CDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes, creating
- MFC dialog boxes, base class
- modeless dialog boxes, creating
- modeless dialog boxes, displaying
- CDialog class
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
caps.latest.revision: 23
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
ms.openlocfilehash: 0944d815e8aca591f2a09c09af60fa591a9b1a6d
ms.lasthandoff: 02/24/2017

---
# <a name="cdialog-class"></a>CDialog 類別
用於在螢幕上顯示對話方塊的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CDialog : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDialog::CDialog](#cdialog)|建構 `CDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDialog::Create](#create)|初始化`CDialog`物件。 建立非強制回應對話方塊，並將它附加`CDialog`物件。|  
|[CDialog::CreateIndirect](#createindirect)|（沒有資源為基礎） 從記憶體中的對話方塊範本建立非強制回應對話方塊。|  
|[CDialog::DoModal](#domodal)|呼叫強制回應對話方塊，並傳回完成。|  
|[CDialog::EndDialog](#enddialog)|關閉強制回應對話方塊。|  
|[CDialog::GetDefID](#getdefid)|取得對話方塊中的預設按鈕控制項的 ID。|  
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|將焦點移至對話方塊中指定的對話方塊控制項。|  
|[CDialog::InitModalIndirect](#initmodalindirect)|（沒有資源為基礎） 從記憶體中的對話方塊範本建立強制回應對話方塊。 儲存參數的函式之前`DoModal`呼叫。|  
|[CDialog::MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換為螢幕的單位。|  
|[CDialog::NextDlgCtrl](#nextdlgctrl)|將焦點移到下一個對話方塊中控制項在對話方塊中。|  
|[CDialog::OnInitDialog](#oninitdialog)|覆寫以擴大對話方塊的初始化。|  
|[CDialog::OnSetFont](#onsetfont)|覆寫指定的對話方塊控制項時所要使用它繪製文字的字型。|  
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|將焦點移至上一個對話方塊中控制項在對話方塊中。|  
|[CDialog::SetDefID](#setdefid)|指定按鈕會變為 對話方塊中的預設按鈕控制項。|  
|[CDialog::SetHelpID](#sethelpid)|設定對話方塊的即時線上說明識別碼。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDialog::OnCancel](#oncancel)|若要執行 [取消] 按鈕或 ESC 鍵的動作會覆寫。 預設會關閉對話方塊並**DoModal**傳回**IDCANCEL**。|  
|[CDialog::OnOK](#onok)|覆寫以執行在強制回應對話方塊的 [確定] 按鈕的動作。 預設會關閉對話方塊並`DoModal`傳回**IDOK**。|  
  
## <a name="remarks"></a>備註  
 對話方塊有兩種類型︰ 強制回應和非強制回應。 應用程式繼續之前，必須使用者關閉強制回應對話方塊。 非強制回應對話方塊可讓使用者顯示對話方塊，並傳回而不會取消，或移除之對話方塊的 另一項工作。  
  
 A`CDialog`物件是對話方塊範本的組合和`CDialog`-衍生的類別。 使用對話方塊編輯器建立對話方塊範本，並將它儲存在資源中，然後使用加入類別精靈來建立衍生自類別`CDialog`。  
  
 對話方塊中的，像任何其他視窗，會接收來自 Windows 的訊息。 在對話方塊中，您會特別有興趣處理從對話方塊的控制項通知訊息，因為這是您的對話方塊與使用者互動的方式。 若要選取您想要的訊息傳送至控制代碼，並將類別中新增適當的訊息對應項目和訊息處理常式成員函式讓您使用 [屬性] 視窗。 您只需要撰寫特定應用程式程式碼中的處理常式成員函式。  
  
 如果想要的話，您可以在撰寫訊息對應項目和成員函式以手動方式。  
  
 在所有但最簡單的對話方塊中，您可以加入成員變數至您的衍生的對話方塊類別來儲存使用者在對話方塊的控制項中輸入的資料，或顯示使用者的資料。 您可以使用 [加入變數] 精靈建立成員變數，並與控制項產生關聯。 在此同時，您可以選擇變數型別及所允許的範圍之每個變數的值。 程式碼精靈會將成員變數加入至您的衍生的對話方塊類別。  
  
 資料對應會產生來自動處理的成員變數和對話方塊的控制項之間的資料交換。 在資料地圖提供初始化的控制項在對話方塊中，使用適當的值的函式、 擷取資料，並驗證資料。  
  
 若要建立強制回應對話方塊，請建構使用您的衍生的對話方塊類別的建構函式的堆疊上的物件，然後呼叫`DoModal`建立對話方塊視窗和其控制項。 如果您想要建立非強制回應對話方塊時，呼叫**建立**對話方塊類別的建構函式中。  
  
 您也可以建立在記憶體中的範本，使用[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)資料結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 在建構之後`CDialog`物件，請呼叫[CreateIndirect](#createindirect)建立非強制回應對話方塊中或呼叫[InitModalIndirect](#initmodalindirect)和[DoModal](#domodal)若要建立強制回應對話方塊。  
  
 交換和驗證資料對應所撰寫的覆寫`CWnd::DoDataExchange`加入至新的對話方塊類別。 請參閱[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函式中的`CWnd`如需詳細資訊的交換和驗證功能。  
  
 程式設計人員和架構呼叫`DoDataExchange`間接透過呼叫[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)。  
  
 這個架構會呼叫`UpdateData`當使用者按一下 [確定] 按鈕來關閉強制回應對話方塊。 （不會擷取資料如果按下 [取消] 按鈕。）預設實作[OnInitDialog](#oninitdialog)也會呼叫`UpdateData`來設定控制項的初始值。 通常會覆寫`OnInitDialog`進一步初始化控制項。 `OnInitDialog`已建立所有對話方塊控制項和之前的對話方塊會顯示之後呼叫。  
  
 您可以呼叫`CWnd::UpdateData`隨時獨佔式或非強制回應對話方塊在執行期間。  
  
 如果您以手動方式開發對話方塊中，加入必要的成員變數的衍生的對話方塊類別，並加入成員函式來設定或取得這些值。  
  
 當使用者按下 [確定] 或 [取消] 按鈕，或當您的程式碼呼叫自動關閉強制回應對話方塊`EndDialog`成員函式。  
  
 當您實作非強制回應對話方塊時，一律會覆寫`OnCancel`成員函式的呼叫`DestroyWindow`從內。 請不要呼叫基底類別`CDialog::OnCancel`，因為它會呼叫`EndDialog`，這會使 對話方塊中看不，但不是會破壞它。 您也應該覆寫`PostNcDestroy`若要刪除的非強制回應對話方塊**這**，因為非強制回應對話方塊通常被配置**新**。 強制回應對話方塊通常建構在框架上，而且不需要`PostNcDestroy`清除。  
  
 如需有關`CDialog`，請參閱︰  
  
- [對話方塊](../../mfc/dialog-boxes.md)  
  
-   知識庫文件 Q262954︰ 如何︰ 建立含捲軸都對話方塊  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDialog`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cdialog"></a>CDialog::CDialog  
 若要建構資源為基礎的強制回應對話方塊中，呼叫建構函式是公用的格式。  
  
```  
explicit CDialog(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
explicit CDialog(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);  
  
CDialog();
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含的對話方塊範本資源名稱的 null 終止字串。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的 ID 編號。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別[CWnd](../../mfc/reference/cwnd-class.md)) 對話方塊物件所屬。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 一種形式的建構函式提供範本名稱對話方塊資源的存取。 其他建構函式提供存取由範本的識別碼，通常使用**IDD_**前置詞 (例如 IDD_DIALOG1)。  
  
 若要建構強制回應對話方塊，從記憶體中的範本，第一次叫用的無參數、 受保護建構函式，然後呼叫`InitModalIndirect`。  
  
 您使用上述方法的其中一個建構強制回應對話方塊之後，請呼叫`DoModal`。  
  
 若要建構非強制回應對話方塊，請使用 受保護的形式`CDialog`建構函式。 建構函式是受到保護，因為您必須衍生您自己的對話方塊類別來實作非強制回應對話方塊。 非強制回應對話方塊的建構是兩步驟程序。 第一次呼叫建構函式。然後呼叫**建立**成員函式來建立資源為基礎的對話方塊，或呼叫`CreateIndirect`建立對話方塊中，從記憶體中的範本。  
  
##  <a name="create"></a>CDialog::Create  
 呼叫**建立**若要建立非強制回應對話方塊，使用對話方塊範本資源。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszTemplateName,  
    CWnd* pParentWnd = NULL);

 
virtual BOOL Create(
    UINT nIDTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含的對話方塊範本資源名稱的 null 終止字串。  
  
 `pParentWnd`  
 指向父視窗物件 (型別[CWnd](../../mfc/reference/cwnd-class.md)) 對話方塊物件所屬。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的 ID 編號。  
  
### <a name="return-value"></a>傳回值  
 這兩種形式傳回非零，如果對話方塊建立和初始化成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以將呼叫**建立**內建構函式或呼叫其建構函式之後叫用。  
  
 兩種形式的**建立**對話方塊範本資源的存取權提供成員函式的範本名稱或範本 ID 編號 (例如 IDD_DIALOG1)。  
  
 對於任一個表單，請將指標傳遞的父視窗物件。 如果`pParentWnd`是**NULL**，對話方塊會建立與設定主應用程式視窗為其父系或擁有者視窗。  
  
 **建立**成員函式傳回之後它會建立對話方塊。  
  
 使用**WS_VISIBLE**樣式在對話方塊範本中，如果在建立父視窗時，應該會出現對話方塊。 否則，您必須呼叫`ShowWindow`。 進一步對話方塊樣式及它們的應用程式，請參閱[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]和[視窗樣式](../../mfc/reference/window-styles.md)中*MFC 參考*。  
  
 使用`CWnd::DestroyWindow`終結對話方塊中所建立的函式**建立**函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&62;](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]  
  
##  <a name="createindirect"></a>CDialog::CreateIndirect  
 呼叫此成員函式可從記憶體中的對話方塊範本中建立非強制回應對話方塊。  
  
```  
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpDialogTemplate`  
 指向包含用來建立對話方塊中的對話方塊範本的記憶體。 這個範本的形式是[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)結構及控制資訊，如述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pParentWnd`  
 指向對話方塊物件的父視窗物件 (型別[CWnd](../../mfc/reference/cwnd-class.md))。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
 `lpDialogInit`  
 指向**DLGINIT**資源。  
  
 `hDialogTemplate`  
 包含全域記憶體包含對話方塊範本的控制代碼。 這個範本的形式是**DLGTEMPLATE**結構和每個控制項在對話方塊中的資料。  
  
### <a name="return-value"></a>傳回值  
 如果對話方塊中建立和初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 `CreateIndirect`成員函式傳回之後它會建立對話方塊。  
  
 使用**WS_VISIBLE**樣式在對話方塊範本中，如果在建立父視窗時，應該會出現對話方塊。 否則，您必須呼叫`ShowWindow`，讓它出現。 如需有關如何指定其他對話方塊樣式範本中的詳細資訊，請參閱[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 使用`CWnd::DestroyWindow`終結對話方塊中所建立的函式`CreateIndirect`函式。  
  
 包含 ActiveX 控制項的對話方塊需要額外的資訊中提供**DLGINIT**資源。 如需詳細資訊，請參閱知識庫文件 Q231591，「 如何︰ 建立 ActiveX 控制項的 MFC 對話方塊中使用的對話方塊範本。 」 知識庫文件可在 MSDN Library 中的 Visual Studio 文件或[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="domodal"></a>CDialog::DoModal  
 呼叫此成員函式，來叫用強制回應對話方塊，並傳回完成的對話方塊結果。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 `int`值，指定的值`nResult`參數傳遞給[CDialog::EndDialog](#enddialog)成員函式，用來關閉對話方塊。 傳回值為 –&1;，如果函式無法建立對話方塊中，或**IDABORT**如果發生其他錯誤，在此情況下 [輸出] 視窗將包含錯誤資訊[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>備註  
 之對話方塊的 作用中時，此成員函式會處理所有的使用者互動。 這是讓對話方塊強制回應。也就是使用者無法互動與其他視窗中，直到關閉對話方塊。  
  
 如果使用者按一下其中一個按鈕，在對話方塊中，例如 [確定] 或 [取消]，訊息處理常式成員函式，例如[OnOK](#onok)或[OnCancel](#oncancel)，呼叫以嘗試關閉對話方塊。 預設`OnOK`成員函式會驗證和更新對話方塊中的資料，關閉 [結果] 對話方塊**IDOK**，而預設`OnCancel`成員函式會關閉對話方塊，產生的結果**IDCANCEL**卻未驗證或更新的對話方塊中的資料。 您可以覆寫這些訊息處理常式函式，來改變其行為。  
  
> [!NOTE]
> `PreTranslateMessage`現在會強制回應對話方塊方塊處理訊息的呼叫。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&63;](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]  
  
##  <a name="enddialog"></a>CDialog::EndDialog  
 呼叫此成員函式，若要強制回應對話方塊。  
  
```  
void EndDialog(int nResult);
```  
  
### <a name="parameters"></a>參數  
 `nResult`  
 包含要從對話方塊傳回至呼叫端的值`DoModal`。  
  
### <a name="remarks"></a>備註  
 此成員函式會傳回`nResult`的傳回值為`DoModal`。 您必須使用`EndDialog`函數來完成處理每次建立強制回應對話方塊。  
  
 您可以呼叫`EndDialog`在任何時間，即使是在[OnInitDialog](#oninitdialog)、 之前的對話方塊會顯示這種情況下，您應該關閉或設定輸入的焦點之前。  
  
 `EndDialog`不會立即關閉對話方塊。 相反地，它會設定旗標，指示對話方塊關閉，因為目前的訊息處理常式傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&64;](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCControlLadenDialog #&65;](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]  
  
##  <a name="getdefid"></a>CDialog::GetDefID  
 呼叫`GetDefID`成員函式來取得對話方塊中的預設按鈕控制項的 ID。  
  
```  
DWORD GetDefID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值 ( `DWORD`)。 如果預設按鈕的 ID 值，高序位文字包含**DC_HASDEFID**和低序位字組包含的識別碼值。 如果預設按鈕沒有 ID 值，則傳回值為 0。  
  
### <a name="remarks"></a>備註  
 這通常是 [確定] 按鈕。  
  
##  <a name="gotodlgctrl"></a>CDialog::GotoDlgCtrl  
 將焦點移至對話方塊中指定的控制項。  
  
```  
void GotoDlgCtrl(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>參數  
 `pWndCtrl`  
 識別要接收焦點的視窗 （控制）。  
  
### <a name="remarks"></a>備註  
 若要取得的控制項 （子視窗），做為傳遞指標`pWndCtrl`，呼叫`CWnd::GetDlgItem`成員函式，傳回的指標[CWnd](../../mfc/reference/cwnd-class.md)物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。  
  
##  <a name="initmodalindirect"></a>CDialog::InitModalIndirect  
 呼叫此成員函式，來初始化強制回應對話方塊物件，使用您建構在記憶體中的對話方塊範本。  
  
```  
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,  
    CWnd* pParentWnd = NULL,  
    void* lpDialogInit = NULL);

 
    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpDialogTemplate`  
 指向包含用來建立對話方塊中的對話方塊範本的記憶體。 這個範本的形式是[DLGTEMPLATE](http://msdn.microsoft.com/library/windows/desktop/ms645394)結構及控制資訊，如述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `hDialogTemplate`  
 包含全域記憶體包含對話方塊範本的控制代碼。 這個範本的形式是**DLGTEMPLATE**結構和每個控制項在對話方塊中的資料。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別[CWnd](../../mfc/reference/cwnd-class.md)) 對話方塊物件所屬。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
 `lpDialogInit`  
 指向**DLGINIT**資源。  
  
### <a name="return-value"></a>傳回值  
 如果對話方塊物件已建立並初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 若要間接建立強制回應對話方塊，先配置全域記憶體區塊，並填入對話方塊範本。 然後呼叫空`CDialog`建構對話方塊物件的建構函式。 接下來，呼叫`InitModalIndirect`來儲存您的控制代碼至記憶體中的對話方塊範本。 [Windows] 對話方塊中建立並顯示更新的版本，當[DoModal](#domodal)成員函式呼叫。  
  
 包含 ActiveX 控制項的對話方塊需要額外的資訊中提供**DLGINIT**資源。 如需詳細資訊，請參閱知識庫文件 Q231591，「 如何︰ 建立 ActiveX 控制項的 MFC 對話方塊中使用的對話方塊範本。 」 知識庫文件可在 MSDN Library 中的 Visual Studio 文件或[http://support.microsoft.com](http://support.microsoft.com/)。  
  
##  <a name="mapdialogrect"></a>CDialog::MapDialogRect  
 若要將矩形的對話方塊單位轉換畫面單位的呼叫。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向[RECT](../../mfc/reference/rect-structure1.md)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)座標為轉換的物件，其中包含對話方塊。  
  
### <a name="remarks"></a>備註  
 對話方塊單位是根據衍生自平均寬度和高度的對話方塊中的文字所使用的字型字元的目前對話方塊基底單元所述。 水平的單位是&4; 個對話方塊中的基底寬度單位，而垂直的單位對話方塊基底高度單位的八分之一。  
  
 **GetDialogBaseUnits** Windows 函式會傳回系統字型的大小資訊，但是您可以指定不同的字型，每個對話方塊中，如果您使用**DS_SETFONT**資源定義檔中的樣式。 `MapDialogRect` Windows 函式會使用適當的字型，此對話方塊。  
  
 `MapDialogRect`成員函式會取代對話方塊單位`lpRect`與畫面使矩形可用來建立對話方塊或調整控制項的位置 方塊內的單位 （像素）。  
  
##  <a name="nextdlgctrl"></a>CDialog::NextDlgCtrl  
 將焦點移至 對話方塊中的下一個控制項。  
  
```  
void NextDlgCtrl() const;  
```  
  
### <a name="remarks"></a>備註  
 如果焦點是在對話方塊中的最後一個控制項，它會移至第一個控制項。  
  
##  <a name="oncancel"></a>CDialog::OnCancel  
 架構會呼叫這個方法，當使用者按一下**取消**或按下的 ESC 鍵，在強制回應或非強制回應對話方塊。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>備註  
 覆寫此方法以執行動作 （例如還原舊的資料） 當使用者關閉對話方塊，即可**取消**或按 ESC 鍵。 預設會關閉強制回應對話方塊，藉由呼叫[EndDialog](#enddialog) ，並導致[DoModal](#domodal)傳回 IDCANCEL。  
  
 如果您實作**取消**按鈕在非強制回應對話方塊，您必須覆寫`OnCancel`方法，並呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)裡面。 請勿呼叫基底類別方法，因為它會呼叫`EndDialog`，這會隱藏對話方塊中，但未損毀。  
  
> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`在 Windows XP 下編譯的程式中的物件。 如需詳細資訊`CFileDialog`，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&66;](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]  
  
##  <a name="oninitdialog"></a>CDialog::OnInitDialog  
 會呼叫這個方法，以回應`WM_INITDIALOG`訊息。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 指定是否應用程式具有輸入的焦點之控制項的其中一個在對話方塊中設定。 如果`OnInitDialog`傳回非零值，Windows 就會將輸入的焦點設定為預設的位置，在對話方塊中的第一個控制項。 只有當它明確已設定為其中一個控制項輸入的焦點，在對話方塊中，應用程式可以傳回 0。  
  
### <a name="remarks"></a>備註  
 Windows 會傳送`WM_INITDIALOG`訊息到對話方塊期間[建立](#create)， [CreateIndirect](#createindirect)，或[DoModal](#domodal)呼叫，就會發生之前的對話方塊隨即出現。  
  
 如果您想要執行特殊處理初始化對話方塊時，覆寫這個方法。 在覆寫的版本，先呼叫基底類別`OnInitDialog`，但忽略它的傳回值。 您通常會傳回`TRUE`從覆寫的方法。  
  
 Windows 呼叫`OnInitDialog`Mfc 程式庫對話方塊使用通用標準的通用對話方塊中的程序的函式。 不會呼叫此函式，透過訊息對應，並因此都不需要這個方法的訊息對應項目。  
  
> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`下已編譯的程式中的物件[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 如需有關變更`CFileDialog`下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]看到[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&67;](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]  
  
##  <a name="onok"></a>CDialog::OnOK  
 當使用者按一下時呼叫**確定**按鈕 （IDOK ID 的按鈕）。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>備註  
 覆寫這個方法來執行動作時**確定**按鈕就會啟用。 如果對話方塊包含自動資料驗證和 exchange，這個方法的預設實作會驗證對話方塊中的資料，並更新應用程式中適當的變數。  
  
 如果您實作**確定**按鈕在非強制回應對話方塊，您必須覆寫`OnOK`方法，並呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)裡面。 請勿呼叫基底類別方法，因為它會呼叫[EndDialog](#enddialog)這會讓對話方塊中，但不會終結。  
  
> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`在 Windows XP 下編譯的程式中的物件。 如需詳細資訊`CFileDialog`，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&68;](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]  
  
##  <a name="onsetfont"></a>CDialog::OnSetFont  
 指定對話方塊控制項用來繪製文字的字型。  
  
```  
Virtual void OnSetFont(CFont* pFont);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFont`  
 指定的指標會做此對話方塊中的所有控制項的預設字型的字型。  
  
### <a name="remarks"></a>備註  
 對話方塊中將使用指定的字型作為預設其所有控制項。  
  
 對話方塊編輯器通常會設定對話方塊字型的對話方塊範本資源的一部分。  
  
> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`下已編譯的程式中的物件[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 如需有關變更`CFileDialog`下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]看到[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
##  <a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl  
 在對話方塊中設定前一個控制項焦點。  
  
```  
void PrevDlgCtrl() const;  
```  
  
### <a name="remarks"></a>備註  
 如果焦點是在對話方塊中的第一個控制項，它將移到最後一個控制項方塊中。  
  
##  <a name="setdefid"></a>CDialog::SetDefID  
 變更對話方塊中的預設按鈕控制項。  
  
```  
void SetDefID(UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 指定將成為預設的按鈕控制項的 ID。  
  
##  <a name="sethelpid"></a>CDialog::SetHelpID  
 設定對話方塊的即時線上說明識別碼。  
  
```  
void SetHelpID(UINT nIDR);
```  
  
### <a name="parameters"></a>參數  
 *nIDR*  
 指定即時線上說明識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DLGCBR32](../../visual-cpp-samples.md)   
 [MFC 範例 DLGTEMPL](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


