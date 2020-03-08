---
title: CPropertySheet 類別
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865443"
---
# <a name="cpropertysheet-class"></a>CPropertySheet 類別

表示屬性工作表，也稱為索引標籤對話方塊。

## <a name="syntax"></a>語法

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPropertySheet：： CPropertySheet](#cpropertysheet)|建構 `CPropertySheet` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPropertySheet：： AddPage](#addpage)|將頁面新增至屬性工作表。|
|[CPropertySheet：：結構](#construct)|建構 `CPropertySheet` 物件。|
|[CPropertySheet：： Create](#create)|顯示非模式屬性工作表。|
|[CPropertySheet：:D oModal](#domodal)|顯示模式屬性工作表。|
|[CPropertySheet：： EnableStackedTabs](#enablestackedtabs)|指出屬性工作表是否使用堆疊或捲軸索引標籤。|
|[CPropertySheet：： EndDialog](#enddialog)|終止屬性工作表。|
|[CPropertySheet：： GetActiveIndex](#getactiveindex)|抓取屬性工作表之使用中頁面的索引。|
|[CPropertySheet：： GetActivePage](#getactivepage)|傳回使用中的頁面物件。|
|[CPropertySheet：： GetPage](#getpage)|抓取指定頁面的指標。|
|[CPropertySheet：： GetPageCount](#getpagecount)|抓取屬性工作表中的頁面數目。|
|[CPropertySheet：： GetPageIndex](#getpageindex)|抓取屬性工作表中指定之頁面的索引。|
|[CPropertySheet：： GetTabControl](#gettabcontrol)|抓取索引標籤控制項的指標。|
|[CPropertySheet：： MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換成螢幕單元。|
|[CPropertySheet：： OnInitDialog](#oninitdialog)|覆寫以擴大屬性工作表初始化。|
|[CPropertySheet：:P ressButton](#pressbutton)|模擬屬性工作表中指定之按鈕的選擇。|
|[CPropertySheet：： RemovePage](#removepage)|從屬性工作表中移除頁面。|
|[CPropertySheet：： SetActivePage](#setactivepage)|以程式設計方式設定使用中的頁面物件。|
|[CPropertySheet：： SetFinishText](#setfinishtext)|設定 [完成] 按鈕的文字。|
|[CPropertySheet：： SetTitle](#settitle)|設定屬性工作表的標題。|
|[CPropertySheet：： SetWizardButtons](#setwizardbuttons)|啟用 wizard 按鈕。|
|[CPropertySheet：： SetWizardMode](#setwizardmode)|啟用 wizard 模式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPropertySheet：： m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)結構。 提供基本屬性工作表參數的存取權。|

## <a name="remarks"></a>備註

屬性工作表是由 `CPropertySheet` 物件和一或多個[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件所組成。 架構會將屬性工作表顯示為具有一組索引標籤索引的視窗，以及包含目前所選取頁面的區域。 使用者可以使用適當的索引標籤，流覽至特定的頁面。

`CPropertySheet` 針對 Windows 98 和 Windows NT 2000 中引進的擴充[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)結構提供支援。 結構包含其他旗標和成員，可支援使用「浮水印」背景點陣圖。

若要在您的屬性工作表物件中自動顯示這些新影像，請在[CPropertySheet：：結構](#construct)或[CPropertySheet：： CPropertySheet](#cpropertysheet)的呼叫中傳遞點陣圖和調色板影像的有效值。

雖然 `CPropertySheet` 不是衍生自[CDialog](../../mfc/reference/cdialog-class.md)，但管理 `CPropertySheet` 物件就像是管理 `CDialog` 物件。 例如，建立屬性工作表需要兩個部分的結構：呼叫此函式，然後呼叫模式屬性工作表的[DoModal](#domodal) ，或針對非模式屬性工作表[建立](#create)。 `CPropertySheet` 有兩種類型的函式： [CPropertySheet：：結構](#construct)和[CPropertySheet：： CPropertySheet](#cpropertysheet)。

當您建立 `CPropertySheet` 物件時，某些[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能會導致發生第一個可能的例外狀況。 這是系統在建立工作表之前，嘗試變更屬性工作表樣式所產生的結果。 若要避免這個例外狀況，請確定您在建立 `CPropertySheet`時，設定了下列樣式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

下列樣式是選擇性的，而且不會造成第一個可能發生的例外狀況：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

禁止任何其他 `Window Styles`，而且您不應加以啟用。

在 `CPropertySheet` 物件與外部物件之間交換資料，類似于使用 `CDialog` 物件交換資料。 重要的差異在於屬性工作表的設定通常是 `CPropertyPage` 物件的成員變數，而不是 `CPropertySheet` 物件本身。

您可以建立一個稱為「wizard」的 [索引標籤] 對話方塊，其中包含具有一系列屬性頁的屬性工作表，可引導使用者完成作業的步驟，例如設定裝置或建立電子報。 在 [wizard-類型] 索引標籤對話方塊中，屬性頁沒有索引標籤，而且一次只能顯示一個屬性頁。 此外，[wizard type] 索引標籤對話方塊也有 [**上一頁**] 按鈕、 **[下一步** **] 或 [完成**] 按鈕、[**取消**] 按鈕和 [說明 **] 按鈕，** 而不是有 **[確定**] 和 [**立即**套用] 按鈕。

若要建立 [wizard 類型] 對話方塊，請遵循建立標準屬性工作表所遵循的相同步驟，但在呼叫[DoModal](#domodal)之前，請先呼叫[SetWizardMode](#setwizardmode) 。 若要啟用 wizard 按鈕，請呼叫[SetWizardButtons](#setwizardbuttons)，並使用旗標來自訂其功能和外觀。 若要啟用 [**完成]** 按鈕，請在使用者于 wizard 的最後一頁上採取動作之後，呼叫[SetFinishText](#setfinishtext) 。

如需如何使用 `CPropertySheet` 物件的詳細資訊，請參閱[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>需求

**標頭：** afxdlgs。h

##  <a name="addpage"></a>CPropertySheet：： AddPage

加入提供的頁面，其中包含屬性工作表中最右邊的索引標籤。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要加入至屬性工作表的頁面。 不能是 NULL。

### <a name="remarks"></a>備註

依您想要顯示的順序，將頁面加入至屬性工作表。

`AddPage` 會將[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)物件新增至 `CPropertySheet` 物件的頁面清單，但實際上並不會建立該頁面的視窗。 架構會延遲建立頁面的視窗，直到使用者選取該頁面為止。

當您使用 `AddPage`加入屬性頁時，`CPropertySheet` 是 `CPropertyPage`的父系。 若要從屬性頁取得屬性工作表的存取權，請呼叫[CWnd：： GetParent](../../mfc/reference/cwnd-class.md#getparent)。

您不需要等到建立屬性工作表視窗來呼叫 `AddPage`。 通常，您會在呼叫[DoModal](#domodal)或[Create](#create)之前呼叫 `AddPage`。

如果您在顯示內容頁之後呼叫 `AddPage`，索引標籤列會反映新加入的頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet：：結構

建構 `CPropertySheet` 物件。

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>參數

*nIDCaption*<br/>
要用於屬性工作表的標題識別碼。

*pParentWnd*<br/>
屬性工作表之父視窗的指標。 如果是 Null，父視窗會是應用程式的主視窗。

*iSelectPage*<br/>
一開始會排在最上層的頁面索引。 預設值是新增至工作表的第一頁。

*pszCaption*<br/>
字串的指標，其中包含要用於屬性工作表的標題。 不能是 NULL。

*hbmWatermark*<br/>
屬性頁浮水印點陣圖的控制碼。

*hpalWatermark*<br/>
浮水印點陣圖和（或）標頭點陣圖之色板的控制碼。

*hbmHeader*<br/>
屬性頁標頭點陣圖的控制碼。

### <a name="remarks"></a>備註

如果尚未呼叫其中一個類別的函式，請呼叫這個成員函式。 例如，當您宣告或配置 `CPropertySheet` 物件的陣列時，請呼叫 `Construct`。 如果是陣列，您必須針對陣列中的每個成員呼叫 `Construct`。

若要顯示內容表，請呼叫[DoModal](#domodal)或[建立](#create)。 第一個參數中所包含的字串將會放在屬性工作表的標題列中。

如果您使用以上所列的第三或第四個 `Construct`原型，而且您傳遞*hbmWatermark*、 *hpalWatermark*和/或*hbmHeader*參數的有效值，您就可以自動顯示浮水印和/或標頭影像。

### <a name="example"></a>範例

下列範例會在您 `Construct`呼叫的情況下示範。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet：： CPropertySheet

建構 `CPropertySheet` 物件。

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>參數

*nIDCaption*<br/>
要用於屬性工作表的標題識別碼。

*pParentWnd*<br/>
指向屬性工作表的父視窗。 如果是 Null，父視窗會是應用程式的主視窗。

*iSelectPage*<br/>
一開始會排在最上層的頁面索引。 預設值是新增至工作表的第一頁。

*pszCaption*<br/>
指向包含要用於屬性工作表之標題的字串。 不能是 NULL。

*hbmWatermark*<br/>
屬性工作表之背景點陣圖的控制碼。

*hpalWatermark*<br/>
浮水印點陣圖和（或）標頭點陣圖之調色板的控制碼。

*hbmHeader*<br/>
屬性頁之標頭點陣圖的控制碼。

### <a name="remarks"></a>備註

若要顯示內容表，請呼叫[DoModal](#domodal)或[建立](#create)。 第一個參數中所包含的字串將會放在屬性工作表的標題列中。

如果您有多個參數（例如，如果您使用的是陣列），請使用 [[結構](#construct)]，而不是 [`CPropertySheet`]。

如果您使用上述 `CPropertySheet`的第三或第四個原型，而且您傳遞*hbmWatermark*、 *hpalWatermark*和/或*hbmHeader*參數的有效值，您就可以自動顯示浮水印和/或標頭影像。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet：： Create

顯示非模式屬性工作表。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指向父視窗。 如果是 Null，父系就是桌面。

*dwStyle*<br/>
屬性工作表的視窗樣式。 如需可用樣式的完整清單，請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwExStyle*<br/>
屬性工作表的擴充視窗樣式。 如需可用樣式的完整清單，請參閱[擴充的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>傳回值

如果成功建立屬性工作表，則為非零;否則為0。

### <a name="remarks"></a>備註

`Create` 的呼叫可以在此函式內，您也可以在叫用此函式之後呼叫它。

預設樣式（以*dwStyle*傳遞-1 表示）實際上&#124;是 WS_SYSMENU WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 預設的擴充視窗樣式（以*dwExStyle*傳遞0表示）實際上是 WS_EX_DLGMODALFRAME。

建立屬性工作表之後，`Create` 成員函式會立即傳回。 若要摧毀屬性工作表，請呼叫[CWnd：:D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。

`Create` 的呼叫所顯示的非強制回應屬性工作表沒有 [確定]、[取消]、[立即套用] 和 [說明] 按鈕，因為模式屬性工作表會執行。 所需的按鈕必須由使用者建立。

若要顯示模式屬性工作表，請改為呼叫[DoModal](#domodal) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>CPropertySheet：:D oModal

顯示模式屬性工作表。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

如果函式成功，則為 IDOK 或 IDCANCEL;否則為0或-1。 如果已將屬性工作表建立為 wizard （請參閱[SetWizardMode](#setwizardmode)），`DoModal` 會傳回 ID_WIZFINISH 或 IDCANCEL。

### <a name="remarks"></a>備註

傳回值會對應至關閉屬性工作表之控制項的識別碼。 此函式傳回之後，對應至屬性工作表和所有頁面的視窗都會被終結。 物件本身仍會存在。 通常，您會在 `DoModal` 傳回 IDOK 之後，從[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件中取出資料。

若要顯示非模式屬性工作表，請改為呼叫[Create](#create) 。

從對應的對話資源建立屬性頁時，可能會造成第一個可能發生的例外狀況。 從屬性頁產生的結果，會在建立頁面之前，將對話方塊資源的樣式變更為所需的樣式。 因為資源通常是唯讀的，所以這會造成例外狀況。 系統會處理例外狀況，並複製已修改的資源。 因此，可能會忽略第一個可能發生的例外狀況。

> [!NOTE]
>  如果您使用非同步例外狀況處理模型進行編譯，作業系統就必須處理這個例外狀況。 如需例外狀況處理模型的詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)。 在此情況下，請勿使用C++ try-catch 區塊來包裝 `CPropertySheet::DoModal` 的呼叫，其中 catch 會處理所有例外狀況，例如 `catch (...)`。 此區塊會處理適用于作業系統的例外狀況，並造成無法預期的行為。 不過，您可以安全地C++使用例外狀況處理，搭配特定的例外狀況類型或結構化例外狀況處理，其中的存取違規例外狀況會傳遞至作業系統。

若要避免產生這個第一個可能發生的例外狀況，您可以手動保證屬性工作表具有正確的[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 您需要設定屬性工作表的下列樣式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

您可以使用下列選擇性樣式，而不會造成第一個可能發生的例外狀況：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

停用所有其他的 Windows 樣式，因為它們與屬性工作表不相容。 這段建議不適用於擴充樣式。 適當地設定這些標準樣式，可保證不需要修改屬性工作表，也會避免產生第一個可能發生的例外狀況。

### <a name="example"></a>範例

請參閱[CPropertySheet：： AddPage](#addpage)的範例。

##  <a name="enablestackedtabs"></a>CPropertySheet：： EnableStackedTabs

指出是否要堆疊屬性工作表中的索引標籤列。

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>參數

*bStacked*<br/>
指出屬性工作表中是否已啟用堆疊索引標籤。 將*bStacked*設定為 FALSE，以停用標記的堆疊資料列。

### <a name="remarks"></a>備註

根據預設，如果屬性工作表的索引標籤數目超過屬性工作表寬度的單一資料列，則索引標籤會堆疊在多個資料列中。 若要使用 [滾動索引標籤] 而非 [堆疊] 索引標籤，請在呼叫[DoModal](#domodal)或[Create](#create)之前，`EnableStackedTabs` 呼叫*bStacked*設定為 FALSE 的

當您建立模式或非模式屬性工作表時，必須呼叫 `EnableStackedTabs`。 若要將此樣式併入 `CPropertySheet`衍生的類別中，請撰寫 WM_CREATE 的訊息處理常式。 在覆寫版本的[CWnd：： OnCreate](../../mfc/reference/cwnd-class.md#oncreate)中，呼叫 `EnableStackedTabs( FALSE )`，然後再呼叫基類執行。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet：： EndDialog

終止屬性工作表。

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>參數

*nEndID*<br/>
要當做屬性工作表之傳回值使用的識別碼。

### <a name="remarks"></a>備註

當按下 [確定]、[取消] 或 [關閉] 按鈕時，架構會呼叫這個成員函式。 如果發生應關閉屬性工作表的事件，請呼叫這個成員函式。

這個成員函式只會搭配強制回應對話方塊使用。

### <a name="example"></a>範例

請參閱[CPropertySheet：:P ressbutton](#pressbutton)的範例。

##  <a name="getactiveindex"></a>CPropertySheet：： GetActiveIndex

取得屬性工作表視窗之作用中頁面的索引編號，然後使用傳回的索引編號做為 `GetPage`的參數。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>傳回值

使用中頁面的索引編號。

### <a name="example"></a>範例

請參閱[CPropertySheet：： GetActivePage](#getactivepage)的範例。

##  <a name="getactivepage"></a>CPropertySheet：： GetActivePage

抓取屬性工作表視窗的現用頁面。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>傳回值

使用中頁面的指標。

### <a name="remarks"></a>備註

使用此成員函式，在作用中頁面上執行某些動作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet：： GetPage

傳回這個屬性工作表中指定之頁面的指標。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>參數

*nPage*<br/>
所需頁面的索引（從0開始）。 必須介於0到1（含）的屬性工作表中的頁面數之間。

### <a name="return-value"></a>傳回值

對應至*nPage*參數之頁面的指標。

### <a name="example"></a>範例

請參閱[CPropertyPage：： OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)的範例。

##  <a name="getpagecount"></a>CPropertySheet：： GetPageCount

決定目前在屬性工作表中的頁面數目。

```
int GetPageCount() const;
```

### <a name="return-value"></a>傳回值

屬性工作表中的頁面數目。

### <a name="example"></a>範例

請參閱[CPropertyPage：： OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)的範例。

##  <a name="getpageindex"></a>CPropertySheet：： GetPageIndex

抓取屬性工作表中指定之頁面的索引編號。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向具有要尋找之索引的頁面。 不能是 NULL。

### <a name="return-value"></a>傳回值

頁面的索引編號。

### <a name="remarks"></a>備註

例如，您可以使用 `GetPageIndex` 取得頁面索引，以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。

### <a name="example"></a>範例

請參閱[CPropertySheet：： GetActivePage](#getactivepage)的範例。

##  <a name="gettabcontrol"></a>CPropertySheet：： GetTabControl

抓取索引標籤控制項的指標，以執行索引標籤控制項的特定內容（也就是使用[CTabCtrl](../../mfc/reference/ctabctrl-class.md)中的任何 api）。

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>傳回值

索引標籤控制項的指標。

### <a name="remarks"></a>備註

例如，如果您想要在初始化期間將點陣圖新增至每個索引標籤，請呼叫這個成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>CPropertySheet：： m_psh

結構，其成員會儲存[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)的特性。

### <a name="remarks"></a>備註

使用此結構來初始化屬性工作表在結構化後，但在它與[DoModal](#domodal)成員函式一起顯示之前的外觀。 例如，將 `m_psh` 的*dwSize*成員設定為您希望屬性工作表擁有的大小。

如需此結構的詳細資訊，包括其成員的清單，請參閱 Windows SDK 中的 PROPSHEETHEADER。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>CPropertySheet：： MapDialogRect

將矩形的對話方塊單位轉換成螢幕單元。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向[矩形](/previous-versions/dd162897\(v=vs.85\))結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含要轉換的對話方塊座標。

### <a name="remarks"></a>備註

對話方塊單位是以目前的對話方塊基底單位（衍生自用於對話方塊文字之字型中的字元的平均寬度和高度）來陳述。 一個水準單位是對話方塊基底寬度單位的四分之一，而一個垂直單位是對話方塊基底高度單位的八分之一。

[GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 函式會傳回系統字型的大小資訊，但如果您在資源定義檔中使用 DS_SETFONT 樣式，則可以為每個屬性工作表指定不同的字型。 Windows SDK 中所述的[MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows 函數會針對此對話方塊使用適當的字型。

`MapDialogRect` 成員函式會以螢幕單元（圖元）取代*lpRect*中的對話方塊單位，讓矩形可以用來建立對話方塊，或在方塊內放置控制項。

##  <a name="oninitdialog"></a>CPropertySheet：： OnInitDialog

覆寫以擴大屬性工作表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定應用程式是否已將輸入焦點設定為屬性工作表中的其中一個控制項。 如果 `OnInitDialog` 傳回非零值，Windows 會將輸入焦點設定為屬性工作表中的第一個控制項。 只有當應用程式已將輸入焦點明確設定為屬性工作表中的其中一個控制項時，才可以傳回0。

### <a name="remarks"></a>備註

此成員函式會在回應 WM_INITDIALOG 訊息時呼叫。 這則訊息會在[建立](#create)或[DoModal](#domodal)呼叫期間傳送至屬性工作表，這會在屬性工作表顯示之前立即發生。

如果您需要在初始化屬性工作表時執行特殊處理，請覆寫這個成員函式。 在覆寫的版本中，先呼叫基類 `OnInitDialog`，但忽略其傳回值。 您通常會從覆寫的成員函式傳回 TRUE。

您不需要這個成員函式的訊息對應專案。

##  <a name="pressbutton"></a>CPropertySheet：:P ressButton

模擬屬性工作表中指定之按鈕的選擇。

```
void PressButton(int nButton);
```

### <a name="parameters"></a>參數

*nButton*<br/>
nButton：識別要按下的按鈕。 這個參數可以是下列其中一個值：

- PSBTN_BACK 選擇 [上一頁] 按鈕。

- PSBTN_NEXT 選擇 [下一步] 按鈕。

- PSBTN_FINISH 選擇 [完成] 按鈕。

- PSBTN_OK 選擇 [確定] 按鈕。

- PSBTN_APPLYNOW 選擇 [立即套用] 按鈕。

- PSBTN_CANCEL 選擇 [取消] 按鈕。

- PSBTN_HELP 選擇 [說明] 按鈕。

### <a name="remarks"></a>備註

如需 Windows SDK Pressbutton 訊息的詳細資訊，請參閱[PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) 。

`PressButton` 的呼叫不會將[PSN_APPLY](/windows/win32/Controls/psn-apply)通知從屬性頁傳送至架構。 若要傳送此通知，請呼叫[CPropertyPage：： OnOK](../../mfc/reference/cpropertypage-class.md#onok)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>CPropertySheet：： RemovePage

從屬性工作表中移除頁面，並終結關聯的視窗。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要從屬性工作表中移除的頁面。 不能是 NULL。

*nPage*<br/>
要移除之頁面的索引。 必須介於0到1（含）的屬性工作表中的頁面數之間。

### <a name="remarks"></a>備註

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件本身不會被終結，直到 `CPropertySheet` 視窗的擁有者關閉為止。

##  <a name="setactivepage"></a>CPropertySheet：： SetActivePage

變更使用中的頁面。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*nPage*<br/>
要設定之頁面的索引。 它必須介於0到1（含）之間的頁面數目之間。

*pPage*<br/>
指向要在屬性工作表中設定的頁面。 它不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功啟用屬性工作表，則為非零;否則為0。

### <a name="remarks"></a>備註

例如，如果使用者在單一頁面上的動作，應該會導致另一個頁面變成使用中的頁面，請使用 `SetActivePage`。

### <a name="example"></a>範例

請參閱[CPropertySheet：： GetActivePage](#getactivepage)的範例。

##  <a name="setfinishtext"></a>CPropertySheet：： SetFinishText

設定 [完成] 命令按鈕中的文字。

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要在 [完成] 命令按鈕上顯示的文字。

### <a name="remarks"></a>備註

呼叫 `SetFinishText` 以顯示 [完成] 命令按鈕上的文字，並在使用者于 wizard 的最後一頁完成動作之後，隱藏 [下一步] 和 [上一頁] 按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet：： SetTitle

指定屬性工作表的標題（在框架視窗的標題列中顯示的文字）。

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
指定屬性工作表標題的樣式。 樣式必須指定為0或 PSH_PROPTITLE。 如果樣式設定為 [PSH_PROPTITLE]，則 "Properties" 這個字會出現在指定為標題的文字後面。 例如，呼叫 `SetTitle`（"Simple"，PSH_PROPTITLE）將會產生「簡單屬性」的屬性工作表標題。

*lpszText*<br/>
指向要用來做為屬性工作表標題列標題的文字。

### <a name="remarks"></a>備註

根據預設，屬性工作表會在屬性工作表的函式中使用 caption 參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet：： SetWizardButtons

啟用或停用 wizard 屬性工作表中的 [上一步]、[下一步] 或 [完成] 按鈕。

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
一組旗標，可自訂嚮導按鈕的功能和外觀。 這個參數可以是下列值的組合：

- PSWIZB_BACK 上一頁 按鈕

- PSWIZB_NEXT 下一步 按鈕

- PSWIZB_FINISH 完成 按鈕

- PSWIZB_DISABLEDFINISH 停用的完成 按鈕

### <a name="remarks"></a>備註

只有在開啟對話方塊之後，才呼叫 `SetWizardButtons`;在呼叫[DoModal](#domodal)之前，您無法呼叫 `SetWizardButtons`。 一般來說，您應該從[CPropertyPage：： OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)呼叫 `SetWizardButtons`。

如果您想要變更 [完成] 按鈕上的文字，或在使用者完成嚮導後隱藏 [下一步] 和 [上一頁] 按鈕，請呼叫[SetFinishText](#setfinishtext)。 請注意，相同的按鈕會針對 [完成] 和 [下一步] 共用。 您可以一次顯示 [完成] 或 [下一步] 按鈕，但不能同時顯示兩者。

### <a name="example"></a>範例

`CPropertySheet` 有三個 wizard 屬性頁： `CStylePage`、`CColorPage`和 `CShapePage`。  下面的程式碼片段顯示如何啟用和停用 wizard 屬性頁上的 [**上一頁**] 和 **[下一步]** 按鈕。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet：： SetWizardMode

建立屬性頁作為 wizard。

```
void SetWizardMode();
```

### <a name="remarks"></a>備註

Wizard 屬性頁的主要特性是使用者流覽的是使用 [下一步] 或 [完成]、[上一頁] 和 [取消] 按鈕，而不是 [定位字元]。

在呼叫[DoModal](#domodal)之前，請先呼叫 `SetWizardMode`。 呼叫 `SetWizardMode`之後，`DoModal` 會傳回 ID_WIZFINISH （如果使用者以 [完成] 按鈕關閉）或 IDCANCEL。

`SetWizardMode` 設定 PSH_WIZARD 旗標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
