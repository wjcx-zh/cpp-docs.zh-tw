---
title: CDialog 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: 879f7d6eb4887dfebcc9b2be393b60da4942a351
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614918"
---
# <a name="cdialog-class"></a>CDialog 類別

用於在螢幕上顯示對話方塊的基底類別。

## <a name="syntax"></a>語法

```
class CDialog : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDialog::CDialog](#cdialog)|建構 `CDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDialog::Create](#create)|初始化 `CDialog` 物件。 建立非強制回應對話方塊，並將它附加至`CDialog`物件。|
|[CDialog::CreateIndirect](#createindirect)|（沒有資源為基礎） 從記憶體中的對話方塊範本建立非強制回應對話方塊。|
|[CDialog::DoModal](#domodal)|呼叫強制回應對話方塊，並傳回完成。|
|[CDialog::EndDialog](#enddialog)|關閉強制回應對話方塊。|
|[CDialog::GetDefID](#getdefid)|取得對話方塊中的預設按鈕控制項的 ID。|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|將焦點移至對話方塊中指定的對話方塊控制項。|
|[CDialog::InitModalIndirect](#initmodalindirect)|（沒有資源為基礎） 從記憶體中的對話方塊範本建立強制回應對話方塊。 參數會儲存函式之前`DoModal`呼叫。|
|[CDialog::MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換成螢幕單位中。|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|將焦點移到下一個對話方塊控制項在對話方塊中。|
|[CDialog::OnInitDialog](#oninitdialog)|覆寫以擴大對話方塊的初始化。|
|[CDialog::OnSetFont](#onsetfont)|覆寫，以指定的對話方塊控制項是使用當它繪製文字的字型。|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|將焦點移至上一個對話方塊控制項在對話方塊中。|
|[CDialog::SetDefID](#setdefid)|變更指定按鈕的對話方塊中的預設按鈕控制項。|
|[CDialog::SetHelpID](#sethelpid)|設定對話方塊中的即時線上說明識別碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|若要執行的 [取消] 按鈕或 ESC 按鍵動作會覆寫。 預設會關閉對話方塊和`DoModal`傳回 IDCANCEL。|
|[CDialog::OnOK](#onok)|覆寫以執行在強制回應對話方塊的 [確定] 按鈕的動作。 預設會關閉對話方塊和`DoModal`傳回 IDOK。|

## <a name="remarks"></a>備註

對話方塊有兩種類型： 強制回應和非強制回應。 必須先由使用者關閉強制回應對話方塊中，應用程式會繼續。 非強制回應對話方塊可讓使用者顯示此對話方塊並返回而不需要取消，或移除 [] 對話方塊中的另一項工作。

A`CDialog`物件是對話方塊範本的組合和`CDialog`-衍生的類別。 使用對話方塊編輯器來建立對話方塊範本，並將它儲存在資源中，然後使用 [加入類別精靈] 建立類別，衍生自`CDialog`。

對話方塊中的，像任何其他視窗中，會接收來自 Windows 的訊息。 在對話方塊中，您特別感興趣處理從對話方塊的控制項通知訊息，因為這是使用者與您的對話方塊中的互動方式。 若要選取哪些訊息，您想要控制代碼和它會新增適當的訊息對應項目和訊息處理常式成員函式類別讓您使用 [屬性] 視窗。 您只需要撰寫處理常式成員函式中的應用程式特定的程式碼。

如果您想，您一律可以撰寫訊息對應項目和成員函式以手動方式。

在所有但最簡單的對話方塊中，您可以加入成員變數至您的衍生的對話方塊類別來儲存使用者在對話方塊的控制項中輸入的資料，或顯示使用者的資料。 您可以使用 [加入變數] 精靈來建立成員變數，並將它們關聯的控制項。 在此同時，您可以選擇的變數類型和允許的範圍的每個變數的值。 程式碼精靈 會將您的衍生的對話方塊類別中的成員變數。

資料對應會產生以自動處理的成員變數和對話方塊的控制項之間的資料交換。 在資料地圖提供初始化的控制項在對話方塊中，以適當的值的函式、 擷取資料，並驗證資料。

若要建立強制回應對話方塊中，建構使用您的衍生的對話方塊類別的建構函式在堆疊上的物件，然後呼叫`DoModal`建立對話方塊視窗和它的控制項。 如果您想要建立非強制回應對話方塊時，呼叫`Create`對話方塊類別的建構函式中。

您也可以建立在記憶體中的範本，使用[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)資料結構在 Windows SDK 中所述。 建構之後`CDialog`物件，請呼叫[CreateIndirect](#createindirect)來建立非強制回應對話方塊中或呼叫[InitModalIndirect](#initmodalindirect)並[DoModal](#domodal)建立強制回應 對話方塊。

在交換和驗證資料的地圖以覆寫`CWnd::DoDataExchange`加入至您新的對話方塊類別。 請參閱[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函式中的`CWnd`如交換和驗證功能的詳細資訊。

程式設計人員和架構呼叫`DoDataExchange`間接透過呼叫[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)。

這個架構會呼叫`UpdateData`當使用者按一下 [確定] 按鈕來關閉強制回應對話方塊。 （不會擷取資料如果按下 [取消] 按鈕。）預設實作[OnInitDialog](#oninitdialog)也會呼叫`UpdateData`設定控制項的起始值。 您通常會覆寫`OnInitDialog`進一步初始化控制項。 `OnInitDialog` 會呼叫後已建立所有對話方塊控制項和對話方塊之前，只會顯示。

您可以呼叫`CWnd::UpdateData`任何時間執行的強制回應或非強制回應對話方塊。

如果您以手動方式開發對話方塊中，您新增必要的成員變數至衍生的對話方塊類別，並新增成員函式，來設定或取得這些值。

當使用者按下 [確定] 或 [取消] 按鈕，或當您的程式碼呼叫時自動關閉強制回應對話方塊`EndDialog`成員函式。

當您實作非強制回應對話方塊時，一律會覆寫`OnCancel`成員函式和呼叫`DestroyWindow`從在其中。 請不要呼叫基底類別`CDialog::OnCancel`，因為它會呼叫`EndDialog`，會隱藏對話方塊中，但是會終結。 您也應該覆寫`PostNcDestroy`若要刪除的非強制回應對話方塊**這**，因為非強制回應對話方塊通常被配置**新**。 強制回應對話方塊通常建構在框架上，而不需要`PostNcDestroy`清除。

如需詳細資訊`CDialog`，請參閱 < [Dialog Boxes](../../mfc/dialog-boxes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cdialog"></a>  CDialog::CDialog

若要建構資源為基礎的強制回應對話方塊中，呼叫其中一個公用的形式的建構函式。

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

*lpszTemplateName*<br/>
包含 null 結束的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (型別的[CWnd](../../mfc/reference/cwnd-class.md)) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

### <a name="remarks"></a>備註

一種形式的建構函式提供範本名稱對話方塊資源的存取權。 其他建構函式以提供存取由範本的識別碼，通常**IDD_** 前置詞 (例如 IDD_DIALOG1)。

若要建構的強制回應對話方塊，從記憶體中的範本，第一次叫用的無參數、 受保護建構函式，然後呼叫`InitModalIndirect`。

您使用其中一種以上的方法建構的強制回應對話方塊之後，請呼叫`DoModal`。

若要建構非強制回應對話方塊，請使用 受保護的形式的`CDialog`建構函式。 建構函式會受到保護，因為您必須衍生您自己的對話方塊類別，來實作非強制回應對話方塊。 非強制回應對話方塊的建構是兩步驟程序。 第一次呼叫建構函式然後呼叫`Create`成員函式來建立資源為基礎的對話方塊，或呼叫`CreateIndirect`建立對話方塊中，從記憶體中的範本。

##  <a name="create"></a>  CDialog::Create

呼叫`Create`建立非強制回應對話方塊，使用對話方塊範本資源。

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含 null 結束的字串，這是對話方塊範本資源的名稱。

*pParentWnd*<br/>
指向父視窗物件 (型別的[CWnd](../../mfc/reference/cwnd-class.md)) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

### <a name="return-value"></a>傳回值

這兩種形式傳回非零值，如果對話方塊中建立和初始化成功;否則為 0。

### <a name="remarks"></a>備註

您可以將呼叫`Create`內建構函式或呼叫其建構函式之後叫用。

兩種形式的`Create`成員函式範本名稱或範本 ID 編號 (例如 IDD_DIALOG1) 所提供的對話方塊範本資源的存取權。

對於任一個表單，請將指標傳遞至父視窗物件。 如果*pParentWnd*是 NULL 時，對話方塊會建立與設定主應用程式視窗為其父系或擁有者視窗。

`Create`成員函式會傳回，它會建立對話方塊之後，立即。

如果父視窗建立時，應該會出現對話方塊，請使用對話方塊範本中的 WS_VISIBLE 樣式。 否則，您必須呼叫`ShowWindow`。 如需進一步對話方塊樣式和其應用程式，請參閱[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) Windows SDK 中的結構和[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中*MFC 參考 》*。

使用`CWnd::DestroyWindow`終結對話方塊中所建立的函式`Create`函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>  CDialog::CreateIndirect

呼叫此成員函式，從記憶體中的對話方塊範本建立非強制回應對話方塊。

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

*lpDialogTemplate*<br/>
指向包含用來建立對話方塊中的對話方塊範本的記憶體。 此範本會的形式[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)結構和控制資訊，在 Windows SDK 中所述。

*pParentWnd*<br/>
指向對話方塊物件的父視窗物件 (型別的[CWnd](../../mfc/reference/cwnd-class.md))。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

*hDialogTemplate*<br/>
包含包含對話方塊範本的全域記憶體控制代碼。 此範本的格式為`DLGTEMPLATE`結構和每個控制項在對話方塊中的資料。

### <a name="return-value"></a>傳回值

對話方塊中已建立並初始化成功; 如果為非零否則為 0。

### <a name="remarks"></a>備註

`CreateIndirect`成員函式會傳回，它會建立對話方塊之後，立即。

如果父視窗建立時，應該會出現對話方塊，請使用對話方塊範本中的 WS_VISIBLE 樣式。 否則，您必須呼叫`ShowWindow`，讓它出現。 如需有關如何指定其他對話方塊樣式，以及在範本中的詳細資訊，請參閱 < [DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate) Windows SDK 中的結構。

使用`CWnd::DestroyWindow`終結對話方塊中所建立的函式`CreateIndirect`函式。

包含 ActiveX 控制項的對話方塊需要 DLGINIT 資源中提供的其他資訊。

##  <a name="domodal"></a>  CDialog::DoModal

呼叫此成員函式，來叫用強制回應對話方塊，並傳回完成的對話方塊結果。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

**Int**值，指定的值*n 結果*參數傳遞給[CDialog::EndDialog](#enddialog)成員函式，用來關閉對話方塊。 傳回值為-1，如果函式無法建立 IDABORT 的對話方塊中，如果發生其他錯誤，在此情況下 [輸出] 視窗將包含錯誤資訊[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

### <a name="remarks"></a>備註

對話方塊為作用中時，此成員函式會處理使用者的所有互動。 這是讓對話方塊強制回應;也就是使用者無法互動與其他視窗中，直到在關閉對話方塊。

如果使用者按一下其中一個按鈕，在對話方塊中，例如 [確定] 或 [取消]，訊息處理常式成員函式，例如[OnOK](#onok)或是[OnCancel](#oncancel)，呼叫以嘗試關閉對話方塊。 預設值`OnOK`成員函式會將驗證和更新對話方塊中的資料，並關閉結果 IDOK 的對話方塊和預設`OnCancel`成員函式會關閉與結果 IDCANCEL 對話方塊，而不需要驗證或更新對話方塊中的資料。 您可以覆寫這些訊息處理常式函式，來改變其行為。

> [!NOTE]
> `PreTranslateMessage` 現在會強制回應對話方塊方塊中處理訊息的呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>  CDialog::EndDialog

呼叫此成員函式來終止強制回應對話方塊。

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>參數

*n 結果*<br/>
包含的呼叫端，從對話方塊傳回的值`DoModal`。

### <a name="remarks"></a>備註

此成員函式會傳回*n 結果*的傳回值為`DoModal`。 您必須使用`EndDialog`函式來完成處理時建立強制回應對話方塊。

您可以呼叫`EndDialog`在任何時間，即使是在[OnInitDialog](#oninitdialog)、 在對話方塊中，才會顯示這種情況下，您應該關閉或設定輸入的焦點之前。

`EndDialog` 不會立即關閉對話方塊。 相反地，它會設定旗標，指示關閉為目前的訊息處理常式傳回的對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>  CDialog::GetDefID

呼叫`GetDefID`成員函式來取得對話方塊中的預設按鈕控制項的 ID。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>傳回值

32 位元值 ( `DWORD`)。 如果預設按鈕具有識別碼值，高序位文字包含 DC_HASDEFID，而且低序位字組包含的識別碼值。 如果預設按鈕，並沒有 ID 值，傳回的值為 0。

### <a name="remarks"></a>備註

這通常是 [確定] 按鈕。

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

將焦點移至對話方塊中指定的控制項。

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>參數

*pWndCtrl*<br/>
識別要接收焦點的視窗 （控制）。

### <a name="remarks"></a>備註

若要取得的控制項 （子視窗），做為傳遞指標*pWndCtrl*，呼叫`CWnd::GetDlgItem`成員函式，將指標傳回至[CWnd](../../mfc/reference/cwnd-class.md)物件。

### <a name="example"></a>範例

  範例，請參閱[CWnd::GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

呼叫此成員函式，來初始化您建構在記憶體中的對話方塊範本的使用強制回應對話方塊物件。

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

*lpDialogTemplate*<br/>
指向包含用來建立對話方塊中的對話方塊範本的記憶體。 此範本會的形式[DLGTEMPLATE](/windows/desktop/api/winuser/ns-winuser-dlgtemplate)結構和控制資訊，在 Windows SDK 中所述。

*hDialogTemplate*<br/>
包含包含對話方塊範本的全域記憶體控制代碼。 此範本的格式為`DLGTEMPLATE`結構和每個控制項在對話方塊中的資料。

*pParentWnd*<br/>
指向的父系或擁有者的視窗物件 (型別的[CWnd](../../mfc/reference/cwnd-class.md)) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

### <a name="return-value"></a>傳回值

非零值，如果對話方塊物件已建立並初始化可順利啟動。否則為 0。

### <a name="remarks"></a>備註

若要間接建立強制回應對話方塊中，第一次配置全域記憶體區塊，並填入對話方塊範本。 然後呼叫空`CDialog`建構對話方塊物件的建構函式。 接下來，呼叫`InitModalIndirect`來儲存您的控制代碼至記憶體內部對話方塊範本。 建立並顯示 [Windows] 對話方塊中更新版本，當[DoModal](#domodal)呼叫成員函式。

包含 ActiveX 控制項的對話方塊需要 DLGINIT 資源中提供的其他資訊。

##  <a name="mapdialogrect"></a>  CDialog::MapDialogRect

將矩形的對話方塊單位轉換成螢幕單位的呼叫。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向[RECT](../../mfc/reference/rect-structure1.md)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)協調要轉換的物件，其中包含對話方塊。

### <a name="remarks"></a>備註

對話方塊單位是根據衍生自的平均的寬度和高度，用於對話方塊中文字的字型中的字元目前對話方塊基底單位所述。 水平的單位是對話方塊基底寬度單位的四分之一，一個垂直單位對話方塊基底的高度的單位的八分之一。

`GetDialogBaseUnits` Windows 函式會傳回系統字型的大小資訊，但是您可以指定不同的字型，每個對話方塊中，如果您使用 DS_SETFONT 樣式在資源定義檔案中。 `MapDialogRect` Windows 函式會使用適當的字型，此對話方塊。

`MapDialogRect`成員函式會取代中的對話方塊單位*lpRect*與畫面單位 （像素），讓矩形可用來建立對話方塊或調整控制項在方塊內的位置。

##  <a name="nextdlgctrl"></a>  CDialog::NextDlgCtrl

將焦點移到下一個控制項，在對話方塊中。

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點是在對話方塊中的最後一個控制項，它會移至第一個控制項。

##  <a name="oncancel"></a>  CDialog::OnCancel

架構會呼叫這個方法，當使用者按一下**取消**或按下 ESC 鍵，在強制回應或非強制回應對話方塊。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

覆寫這個方法，以執行動作 （例如還原舊的資料） 當使用者關閉對話方塊，即可**取消**或按下 ESC 鍵。 預設會關閉強制回應對話方塊中，藉由呼叫[EndDialog](#enddialog) ，並造成[DoModal](#domodal)傳回 IDCANCEL。

如果您實作**取消** 按鈕在非強制回應對話方塊方塊中，您必須覆寫`OnCancel`方法，並呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其內。 請勿呼叫基底類別方法，因為它會呼叫`EndDialog`，這會隱藏對話方塊中，但不是將它終結。

> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`在 Windows XP 下編譯的程式中的物件。 如需詳細資訊`CFileDialog`，請參閱 < [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>  CDialog::OnInitDialog

會呼叫這個方法，以回應`WM_INITDIALOG`訊息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定是否應用程式已設定輸入的焦點的控制項在對話方塊中。 如果`OnInitDialog`傳回非零值，Windows 就會將輸入的焦點設定為預設的位置，在對話方塊中的第一個控制項。 只有當它明確已設定為其中一個控制項輸入的焦點，在對話方塊中，應用程式可傳回 0。

### <a name="remarks"></a>備註

Windows 會傳送`WM_INITDIALOG`期間的對話方塊中的訊息[建立](#create)， [CreateIndirect](#createindirect)，或[DoModal](#domodal)對話方塊之前立即發生的呼叫隨即出現。

如果您想要執行特殊處理，初始化對話方塊時，請覆寫這個方法。 在覆寫的版本中，先呼叫基底類別`OnInitDialog`但忽略它的傳回值。 您通常會傳回`TRUE`從覆寫的方法。

Windows 呼叫`OnInitDialog`所有 Microsoft Foundation 類別庫對話方塊使用常用標準的通用對話方塊中的程序的函式。 它不會呼叫此函式，透過訊息對應，並因此都不需要這個方法的訊息對應項目。

> [!NOTE]
> 當您使用時，您無法覆寫這個方法`CFileDialog`Windows Vista 或更新版本的作業系統下編譯的程式中的物件。 如需有關變更`CFileDialog`Windows vista 和更新版本，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>  CDialog::OnOK

當使用者按一下時呼叫**確定**按鈕 （按鈕使用 IDOK 識別碼）。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

覆寫這個方法，以執行動作時**確定**按鈕會啟用。 如果對話方塊含有 自動的資料驗證和 exchange，這個方法的預設實作會驗證對話方塊中的資料，並更新您的應用程式中適當的變數。

如果您實作 **[確定]**  按鈕在非強制回應對話方塊方塊中，您必須覆寫`OnOK`方法，並呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)其內。 請勿呼叫基底類別方法，因為它會呼叫[EndDialog](#enddialog)讓對話方塊不可見，但是不會終結。

> [!NOTE]
>  當您使用時，您無法覆寫這個方法`CFileDialog`在 Windows XP 下編譯的程式中的物件。 如需詳細資訊`CFileDialog`，請參閱 < [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>  CDialog::OnSetFont

指定繪製文字時，會使用對話方塊控制項的字型。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[in]指定將當做預設字型使用此對話方塊中的所有控制項的字型的指標。

### <a name="remarks"></a>備註

對話方塊中將使用指定的字型作為預設值它的所有控制項。

對話方塊編輯器通常會設定對話方塊字型的對話方塊範本資源的一部分。

> [!NOTE]
> 當您使用時，您無法覆寫這個方法`CFileDialog`Windows Vista 或更新版本的作業系統下編譯的程式中的物件。 如需有關變更`CFileDialog`Windows vista 和更新版本，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

將焦點設定至先前的控制項，在對話方塊中。

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點是在對話方塊中的第一個控制項，它會移到最後一個控制項在方塊中。

##  <a name="setdefid"></a>  CDialog::SetDefID

變更對話方塊中的預設按鈕控制項。

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
指定將成為預設的按鈕控制項的 ID。

##  <a name="sethelpid"></a>  CDialog::SetHelpID

設定對話方塊中的即時線上說明識別碼。

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>參數

*nIDR*<br/>
指定即時線上說明識別碼。

## <a name="see-also"></a>另請參閱

[MFC 範例 DLGCBR32](../../visual-cpp-samples.md)<br/>
[MFC 範例 DLGTEMPL](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

