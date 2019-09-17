---
title: CDialog 類別
ms.date: 09/07/2019
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
ms.openlocfilehash: b07190c70fb11950b25aff45fb10e850c0e81b24
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907613"
---
# <a name="cdialog-class"></a>CDialog 類別

用來在螢幕上顯示對話方塊的基底類別。

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
|[CDialog::Create](#create)|初始化 `CDialog` 物件。 建立非強制回應對話方塊，並將其附加至`CDialog`物件。|
|[CDialog::CreateIndirect](#createindirect)|從記憶體中的對話方塊範本建立非強制回應對話方塊（不是以資源為基礎）。|
|[CDialog::DoModal](#domodal)|呼叫強制回應對話方塊，並在完成時傳回。|
|[CDialog::EndDialog](#enddialog)|關閉強制回應對話方塊。|
|[CDialog::GetDefID](#getdefid)|取得對話方塊之預設按鈕控制項的識別碼。|
|[CDialog::GotoDlgCtrl](#gotodlgctrl)|將焦點移至對話方塊中指定的對話方塊控制項。|
|[CDialog::InitModalIndirect](#initmodalindirect)|從記憶體中的對話方塊範本建立強制回應對話方塊（不是以資源為基礎）。 參數會儲存到呼叫函式`DoModal`為止。|
|[CDialog::MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換成螢幕單元。|
|[CDialog::NextDlgCtrl](#nextdlgctrl)|將焦點移至對話方塊中的下一個對話方塊控制項。|
|[CDialog::OnInitDialog](#oninitdialog)|覆寫以增強對話方塊初始化。|
|[CDialog::OnSetFont](#onsetfont)|覆寫以指定對話方塊控制項繪製文字時要使用的字型。|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|將焦點移至對話方塊中的上一個對話方塊控制項。|
|[CDialog::SetDefID](#setdefid)|將對話方塊的預設 [按鈕] 控制項變更為指定的按鍵。|
|[CDialog::SetHelpID](#sethelpid)|設定對話方塊的即時線上說明識別碼。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDialog::OnCancel](#oncancel)|覆寫以執行 [取消] 按鈕或 ESC 鍵動作。 預設會關閉對話方塊，並`DoModal`傳回 IDCANCEL。|
|[CDialog::OnOK](#onok)|覆寫以執行強制回應對話方塊中的 [確定] 按鈕動作。 預設會關閉對話方塊，並`DoModal`傳回 IDOK。|

## <a name="remarks"></a>備註

對話方塊有兩種類型：強制回應和非強制回應。 使用者必須先關閉強制回應對話方塊，應用程式才能繼續。 非強制回應對話方塊可讓使用者顯示對話方塊，並返回另一項工作，而不需要取消或移除對話方塊。

物件是對話方塊範本`CDialog`與衍生類別的組合。 `CDialog` 使用對話方塊編輯器來建立對話方塊範本，並將其儲存在資源中，然後使用 [加入類別] wizard 來建立衍生自`CDialog`的類別。

對話方塊就像任何其他視窗一樣，會從 Windows 接收訊息。 在對話方塊中，您特別有興趣處理來自對話方塊控制項的通知訊息，因為這是使用者與對話方塊互動的方式。 使用 [[類別] [Wizard]](mfc-class-wizard.md)來選取您想要處理的訊息，它會為您將適當的訊息對應專案和訊息處理常式成員函式新增至類別。 您只需要在處理常式成員函式中撰寫應用程式特定的程式碼。

如果您想要的話，一律可以手動撰寫訊息對應專案和成員函式。

除了最簡單的對話方塊之外，您還可以將成員變數加入至衍生的對話方塊類別，以儲存使用者在對話方塊控制項中輸入的資料，或顯示使用者的資料。 您可以使用 [新增變數] wizard 來建立成員變數，並將它們與控制項建立關聯。 同時，您可以針對每個變數選擇變數類型和允許的值範圍。 [程式碼] 會將成員變數加入至您的衍生對話方塊類別。

系統會產生資料對應，以自動處理成員變數與對話方塊控制項之間的資料交換。 資料地圖會提供函式，以使用適當的值來初始化對話方塊中的控制項、抓取資料，以及驗證資料。

若要建立強制回應對話方塊，請使用衍生對話方塊類別的函式，在堆疊上建立物件，然後呼叫`DoModal`來建立對話方塊視窗和其控制項。 如果您想要建立非強制回應對話方塊，請`Create`在對話方塊類別的函式中呼叫。

您也可以使用[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)資料結構在記憶體中建立範本，如 Windows SDK 中所述。 `CDialog`在您建立物件之後，請呼叫[CreateIndirect](#createindirect)來建立非強制回應對話方塊，或呼叫[InitModalIndirect](#initmodalindirect)和[DoModal](#domodal)來建立強制回應對話方塊。

Exchange 和驗證資料對應會以已新增至新對話方塊`CWnd::DoDataExchange`類別的覆寫來寫入。 如需 exchange 和驗證功能`CWnd`的詳細資訊，請參閱中的 [DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) 成員函式。

程式設計人員和架構會透過`DoDataExchange`呼叫[CWnd：： UpdateData](../../mfc/reference/cwnd-class.md#updatedata)間接呼叫。

當使用者按一下`UpdateData` [確定] 按鈕以關閉強制回應對話方塊時，架構會呼叫。 （如果按一下 [取消] 按鈕，則不會抓取資料）。[OnInitDialog](#oninitdialog)的預設實值也會`UpdateData`呼叫來設定控制項的初始值。 您通常會`OnInitDialog`覆寫以進一步初始化控制項。 `OnInitDialog`在建立所有對話方塊控制項之後，以及在對話方塊顯示之前呼叫。

在執行強制`CWnd::UpdateData`回應或非強制回應對話方塊時，您可以隨時呼叫。

如果您以手動方式開發對話方塊，您可以自行將必要的成員變數新增至衍生的對話方塊類別，並加入成員函式來設定或取得這些值。

當使用者按下 [確定] 或 [取消] 按鈕，或當您的程式碼呼叫`EndDialog`成員函式時，強制回應對話方塊會自動關閉。

當您執行非強制回應對話方塊時，請一律覆`OnCancel`寫成員函式`DestroyWindow` ，並從它內呼叫。 請勿呼叫基類`CDialog::OnCancel`，因為它會呼叫`EndDialog`，這會使對話方塊不可見，但不會將其損毀。 您也應該覆`PostNcDestroy`寫非強制回應對話方塊，**以便刪除，** 因為非強制回應對話方塊通常是以**new**來配置。 強制回應對話方塊通常會在框架上建立，不需要`PostNcDestroy`清除。

如需的詳細`CDialog`資訊，請參閱[對話方塊](../../mfc/dialog-boxes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cdialog"></a>CDialog：： CDialog

若要建立以資源為基礎的強制回應對話方塊，請呼叫此方法的公用形式。

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
包含以 null 終止的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的 ID 編號。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或主控視窗物件（類型為[CWnd](../../mfc/reference/cwnd-class.md)）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

### <a name="remarks"></a>備註

其中一種形式的函式依範本名稱提供對對話資源的存取。 另一個函式會依範本識別碼提供存取權，通常會使用**IDD_** 前置詞（例如 IDD_DIALOG1）。

若要從記憶體中的範本來建立強制回應對話方塊，請先叫用無參數、受保護的`InitModalIndirect`構造函式，然後再呼叫。

當您使用上述其中一種方法來建立強制回應對話方塊之後，請`DoModal`呼叫。

若要建立非強制回應對話方塊，請使用受保護的格式`CDialog`函數。 此函式會受到保護，因為您必須衍生自己的對話方塊類別，才能執行非強制回應對話方塊。 非強制回應對話方塊的結構是一個兩個步驟的處理常式。 第一次呼叫此函式;然後，呼叫`Create`成員函式來建立以資源為基礎的對話方塊，或`CreateIndirect`呼叫，以從記憶體中的範本建立對話方塊。

##  <a name="create"></a>CDialog：： Create

呼叫`Create`以使用來自資源的對話方塊範本來建立非強制回應對話方塊。

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
包含以 null 終止的字串，這是對話方塊範本資源的名稱。

*pParentWnd*<br/>
指向對話方塊物件所屬的父視窗物件（類型為[CWnd](../../mfc/reference/cwnd-class.md)）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊範本資源的 ID 編號。

### <a name="return-value"></a>傳回值

如果對話方塊建立和初始化成功，這兩種表單都會傳回非零。否則為0。

### <a name="remarks"></a>備註

您可以將呼叫`Create`放在函式內，或在叫用此函式之後呼叫它。

提供兩種形式`Create`的成員函式，可透過範本名稱或範本識別碼（例如 IDD_DIALOG1）來存取對話方塊範本資源。

不論是哪一種形式，請將指標傳遞給父視窗物件。 如果*pParentWnd*為 Null，則會建立對話方塊，並將其父系或擁有者視窗設定為主應用程式視窗。

`Create`成員函式會在建立對話方塊之後立即傳回。

如果在建立父視窗時應該出現對話方塊，請在對話方塊範本中使用 WS_VISIBLE 樣式。 否則，您必須呼叫`ShowWindow`。 如需進一步的對話方塊樣式及其應用程式，請參閱*MFC 參考*中 Windows SDK 和[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構。

使用函式來摧毀函式所`Create`建立的對話方塊。 `CWnd::DestroyWindow`

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

##  <a name="createindirect"></a>CDialog：： CreateIndirect

呼叫這個成員函式可從記憶體中的對話方塊範本建立非強制回應對話方塊。

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
指向記憶體，其中包含用來建立對話方塊的對話方塊範本。 此範本的格式為[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構和控制項資訊，如 Windows SDK 中所述。

*pParentWnd*<br/>
指向對話方塊物件的父視窗物件（類型為[CWnd](../../mfc/reference/cwnd-class.md)）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

*hDialogTemplate*<br/>
包含包含對話方塊範本之全域記憶體的控制碼。 此範本的格式`DLGTEMPLATE`為對話方塊中每個控制項的結構和資料。

### <a name="return-value"></a>傳回值

如果已成功建立並初始化對話方塊，則為非零;否則為0。

### <a name="remarks"></a>備註

`CreateIndirect`成員函式會在建立對話方塊之後立即傳回。

如果在建立父視窗時應該出現對話方塊，請在對話方塊範本中使用 WS_VISIBLE 樣式。 否則，您必須呼叫`ShowWindow` ，使其出現。 如需如何在範本中指定其他對話方塊樣式的詳細資訊，請參閱 Windows SDK 中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構。

使用函式來摧毀函式所`CreateIndirect`建立的對話方塊。 `CWnd::DestroyWindow`

包含 ActiveX 控制項的對話方塊需要 DLGINIT 資源中提供的其他資訊。

##  <a name="domodal"></a>CDialog：:D oModal

呼叫這個成員函式來叫用強制回應對話方塊，並在完成時傳回對話方塊結果。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

**Int**值，指定傳遞至[CDialog：： EndDialog](#enddialog)成員函式（用來關閉對話方塊）的*n 結果*參數值。 如果函式無法建立對話方塊，則傳回值為-1，如果發生其他錯誤，則傳回 IDABORT，在此情況下，[輸出] 視窗會包含[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)的錯誤資訊。

### <a name="remarks"></a>備註

此成員函式會在對話方塊為作用中時，處理與使用者的所有互動。 這就是讓對話方塊強制回應的方式。也就是說，使用者無法與其他視窗互動，直到對話方塊關閉為止。

如果使用者按一下對話方塊中的其中一個按鈕，例如 [確定] 或 [取消]，則會呼叫訊息處理常式成員函式（例如[OnOK](#onok)或[OnCancel](#oncancel)）來嘗試關閉對話方塊。 預設`OnOK`成員函式會驗證並更新對話方塊資料，並關閉含有 result IDOK 的對話方塊，而預設`OnCancel`成員函式會關閉含有 result IDCANCEL 的對話方塊，而不會驗證或更新對話方塊資料。 您可以覆寫這些訊息處理常式函式來改變其行為。

> [!NOTE]
> `PreTranslateMessage`現在會針對強制回應對話方塊訊息處理呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

##  <a name="enddialog"></a>CDialog：： EndDialog

呼叫這個成員函式以終止強制回應對話方塊。

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>參數

*nResult*<br/>
包含要從對話方塊傳回給呼叫端的`DoModal`值。

### <a name="remarks"></a>備註

此成員函式會傳回*n 結果*做為的`DoModal`傳回值。 每當建立強制回應對話方塊`EndDialog`時，您都必須使用函數來完成處理。

您可以隨時`EndDialog`呼叫，甚至是在[OnInitDialog](#oninitdialog)中，在此情況下，您應該在顯示或設定輸入焦點之前關閉對話方塊。

`EndDialog`不會立即關閉對話方塊。 相反地，它會設定旗標，以指示對話方塊在目前的訊息處理常式傳回時立即關閉。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

##  <a name="getdefid"></a>CDialog：： GetDefID

`GetDefID`呼叫成員函式，以取得對話方塊預設按鈕控制項的識別碼。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>傳回值

32位值（ `DWORD`）。 如果預設的按鈕具有識別碼值，則高序位單字會包含 DC_HASDEFID，而低序位字組則包含識別碼值。 如果預設的按鍵不具有識別碼值，則傳回值為0。

### <a name="remarks"></a>備註

這通常是 [確定] 按鈕。

##  <a name="gotodlgctrl"></a>  CDialog::GotoDlgCtrl

將焦點移至對話方塊中的指定控制項。

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>參數

*pWndCtrl*<br/>
識別要接收焦點的視窗（控制項）。

### <a name="remarks"></a>備註

若要取得控制項（子視窗）的指標以傳遞為*pWndCtrl*，請呼叫`CWnd::GetDlgItem`成員函式，該函式會傳回[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

### <a name="example"></a>範例

  請參閱[CWnd：： GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)的範例。

##  <a name="initmodalindirect"></a>  CDialog::InitModalIndirect

呼叫這個成員函式，使用您在記憶體中所建立的對話方塊範本來初始化強制回應對話方塊物件。

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
指向記憶體，其中包含用來建立對話方塊的對話方塊範本。 此範本的格式為[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構和控制項資訊，如 Windows SDK 中所述。

*hDialogTemplate*<br/>
包含包含對話方塊範本之全域記憶體的控制碼。 此範本的格式`DLGTEMPLATE`為對話方塊中每個控制項的結構和資料。

*pParentWnd*<br/>
指向對話方塊物件所屬的父系或主控視窗物件（類型為[CWnd](../../mfc/reference/cwnd-class.md)）。 如果它是 Null，則對話方塊物件的父視窗會設定為主應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

### <a name="return-value"></a>傳回值

如果成功建立並初始化對話方塊物件，則為非零;否則為0。

### <a name="remarks"></a>備註

若要間接建立強制回應對話方塊，請先配置記憶體的全域區塊，並使用對話方塊範本加以填入。 然後呼叫空`CDialog`的函式來建立對話方塊物件。 接下來， `InitModalIndirect`呼叫，將您的控制碼儲存至記憶體中的對話方塊範本。 當呼叫[DoModal](#domodal)成員函式時，會建立並顯示 [Windows] 對話方塊。

包含 ActiveX 控制項的對話方塊需要 DLGINIT 資源中提供的其他資訊。

##  <a name="mapdialogrect"></a>CDialog：： MapDialogRect

呼叫，將矩形的對話方塊單位轉換成螢幕單元。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含要轉換的對話方塊座標。

### <a name="remarks"></a>備註

對話方塊單位是以目前的對話方塊基底單位（衍生自用於對話方塊文字之字型中的字元的平均寬度和高度）來陳述。 一個水準單位是對話方塊基底寬度單位的四分之一，而一個垂直單位是對話方塊基底高度單位的八分之一。

`GetDialogBaseUnits` Windows 函數會傳回系統字型的大小資訊，但如果您在資源定義檔中使用 DS_SETFONT 樣式，則可以為每個對話方塊指定不同的字型。 `MapDialogRect` Windows 函數會針對此對話方塊使用適當的字型。

此`MapDialogRect`成員函式會以螢幕單元（圖元）取代*lpRect*中的對話方塊單位，讓矩形可以用來建立對話方塊，或在方塊內放置控制項。

##  <a name="nextdlgctrl"></a>CDialog：： NextDlgCtrl

將焦點移至對話方塊中的下一個控制項。

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點是在對話方塊中的最後一個控制項，它會移至第一個控制項。

##  <a name="oncancel"></a>CDialog：： OnCancel

當使用者按一下 [**取消**] 或按下 [模式] 或 [非模式] 對話方塊中的 ESC 鍵時，架構會呼叫這個方法。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

當使用者按一下 [**取消**] 或按下 ESC 鍵關閉對話方塊時，請覆寫此方法來執行動作（例如還原舊資料）。 預設會藉由呼叫[EndDialog](#enddialog)並導致[DoModal](#domodal)傳回 IDCANCEL，來關閉強制回應對話方塊。

如果您在非強制回應對話方塊中執行 [**取消**] 按鈕，則必須覆`OnCancel`寫方法並在其中呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) 。 請勿呼叫基類方法，因為它會呼叫`EndDialog`，這會使對話方塊不可見，但不會損毀。

> [!NOTE]
>  當您在 Windows XP 下編譯的程式`CFileDialog`中使用物件時，無法覆寫這個方法。 如需的詳細`CFileDialog`資訊，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

##  <a name="oninitdialog"></a>CDialog：： OnInitDialog

會呼叫這個方法來`WM_INITDIALOG`回應訊息。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定應用程式是否已將輸入焦點設定為對話方塊中的其中一個控制項。 如果`OnInitDialog`傳回非零值，Windows 會將輸入焦點設定為預設位置，也就是對話方塊中的第一個控制項。 只有當應用程式已將輸入焦點明確設定為對話方塊中的其中一個控制項時，才可以傳回0。

### <a name="remarks"></a>備註

Windows 會在 [[建立](#create)]、[ [CreateIndirect](#createindirect)] 或 [ [DoModal](#domodal)呼叫] 期間，將訊息傳送至對話方塊，這會在對話方塊顯示之前立即出現。`WM_INITDIALOG`

如果您想要在初始化對話方塊時執行特殊處理，請覆寫這個方法。 在覆寫的版本中，先呼叫基類`OnInitDialog` ，但忽略其傳回值。 您通常`TRUE`會從覆寫的方法傳回。

Windows 會使用`OnInitDialog`所有 MFC 程式庫對話方塊通用的標準全域對話方塊程式來呼叫函數。 它不會透過您的訊息對應來呼叫此函式，因此，您不需要此方法的訊息對應專案。

> [!NOTE]
> 當您在 Windows Vista 或更新版本的`CFileDialog`作業系統下編譯的程式中使用物件時，無法覆寫這個方法。 如需 Windows Vista 和更新`CFileDialog`版本底下變更的詳細資訊，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

##  <a name="onok"></a>CDialog：： OnOK

當使用者按一下 **[確定]** 按鈕（識別碼為 IDOK 的按鈕）時呼叫。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

覆寫此方法，以在啟用 [**確定]** 按鈕時執行動作。 如果對話方塊包含自動資料驗證和交換，這個方法的預設執行會驗證對話方塊資料，並更新您應用程式中的適當變數。

如果您在非強制回應對話方塊中執行 [**確定]** 按鈕，則必須覆`OnOK`寫方法並在其中呼叫[DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow) 。 請勿呼叫基類方法，因為它會呼叫[EndDialog](#enddialog) ，這會使對話方塊不可見，但不會損毀。

> [!NOTE]
>  當您在 Windows XP 下編譯的程式`CFileDialog`中使用物件時，無法覆寫這個方法。 如需的詳細`CFileDialog`資訊，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

##  <a name="onsetfont"></a>CDialog：： OnSetFont

指定在繪製文字時，對話方塊控制項將使用的字型。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
在指定字型的指標，這個字型會當做這個對話方塊中所有控制項的預設字型使用。

### <a name="remarks"></a>備註

對話方塊會使用指定的字型做為其所有控制項的預設值。

對話方塊編輯器通常會將對話方塊字型設定為對話方塊範本資源的一部分。

> [!NOTE]
> 當您在 Windows Vista 或更新版本的`CFileDialog`作業系統下編譯的程式中使用物件時，無法覆寫這個方法。 如需 Windows Vista 和更新`CFileDialog`版本底下變更的詳細資訊，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

##  <a name="prevdlgctrl"></a>  CDialog::PrevDlgCtrl

將焦點設定為對話方塊中的上一個控制項。

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點是在對話方塊中的第一個控制項，它會移至方塊中的最後一個控制項。

##  <a name="setdefid"></a>CDialog：： SetDefID

變更對話方塊的預設 [按鈕] 控制項。

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
指定將成為預設值的 [按鈕] 控制項的識別碼。

##  <a name="sethelpid"></a>CDialog：： SetHelpID

設定對話方塊的即時線上說明識別碼。

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>參數

*nIDR*<br/>
指定上下文相關的説明識別碼。

## <a name="see-also"></a>另請參閱

[MFC 範例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
