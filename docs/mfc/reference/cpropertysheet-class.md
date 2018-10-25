---
title: CPropertySheet 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df22a7e2209b49f65d240336229a3c80ba4ddb7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063818"
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
|[CPropertySheet::CPropertySheet](#cpropertysheet)|建構 `CPropertySheet` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Cpropertysheet:: Addpage](#addpage)|將頁面新增至屬性工作表。|
|[CPropertySheet::Construct](#construct)|建構 `CPropertySheet` 物件。|
|[CPropertySheet::Create](#create)|顯示強制回應屬性工作表。|
|[Cpropertysheet:: Setwizardmode](#domodal)|顯示強制回應屬性工作表。|
|[Cpropertysheet:: Enablestackedtabs](#enablestackedtabs)|表示屬性工作表是否使用堆疊或捲動的索引標籤。|
|[CPropertySheet::EndDialog](#enddialog)|屬性工作表就會終止。|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|擷取屬性工作表的使用中頁面的索引。|
|[CPropertySheet::GetActivePage](#getactivepage)|傳回使用中的頁面物件。|
|[CPropertySheet::GetPage](#getpage)|擷取指定的頁面的指標。|
|[CPropertySheet::GetPageCount](#getpagecount)|擷取屬性工作表中的頁數。|
|[CPropertySheet::GetPageIndex](#getpageindex)|擷取指定的屬性工作表的頁面索引。|
|[CPropertySheet::GetTabControl](#gettabcontrol)|擷取索引標籤控制項的指標。|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換成螢幕單位中。|
|[Cpropertysheet:: Oninitdialog](#oninitdialog)|覆寫以擴大屬性工作表初始化。|
|[CPropertySheet::PressButton](#pressbutton)|模擬屬性工作表中指定的按鈕的選擇。|
|[CPropertySheet::RemovePage](#removepage)|從屬性工作表移除頁面。|
|[CPropertySheet::SetActivePage](#setactivepage)|以程式設計方式設定的使用中的頁面物件。|
|[CPropertySheet::SetFinishText](#setfinishtext)|設定 [完成] 按鈕的文字。|
|[CPropertySheet::SetTitle](#settitle)|設定屬性工作表的標題。|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|可讓精靈按鈕。|
|[Cpropertysheet:: Domodal](#setwizardmode)|可讓精靈模式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2)結構。 提供基本的屬性工作表參數的存取權。|

## <a name="remarks"></a>備註

屬性工作表組成`CPropertySheet`物件和一或多個[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件。 架構會顯示屬性工作表，為具有一組索引標籤索引和區域，其中包含目前所選的頁面的視窗。 使用者瀏覽至特定頁面中，使用適當的索引標籤。

`CPropertySheet` 提供支援展開[PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) Windows 98 和 Windows NT 2000 中導入的結構。 此結構包含其他旗標並支援使用 「 浮水印 」 背景點陣圖的成員。

若要在您的屬性工作表物件會自動顯示這些新的映像，請傳入有效值的點陣圖和調色盤映像呼叫[CPropertySheet::Construct](#construct)或[CPropertySheet::CPropertySheet](#cpropertysheet).

即使`CPropertySheet`不衍生自[CDialog](../../mfc/reference/cdialog-class.md)，所以管理`CPropertySheet`物件就像管理`CDialog`物件。 建立屬性工作表需要兩部分建構的例如： 呼叫建構函式，然後再呼叫[DoModal](#domodal)強制回應屬性工作表或[建立](#create)非強制回應屬性工作表。 `CPropertySheet` 有兩種類型的建構函式： [CPropertySheet::Construct](#construct)並[CPropertySheet::CPropertySheet](#cpropertysheet)。

當您建構`CPropertySheet`物件時，有些[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能會導致發生 first-chance 例外狀況。 這會產生從系統嘗試變更的屬性工作表樣式之前建立的工作表。 若要避免這個例外狀況，請確定您在建立時，設定下列樣式您`CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

下列樣式是選擇性的而且不會造成 first-chance 例外狀況：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

任何其他`Window Styles`禁止和您不應該啟用它們。

交換資料之間`CPropertySheet`物件和外部的物件是類似於與交換資料`CDialog`物件。 重要的差異是屬性工作表的設定通常是的成員變數`CPropertyPage`物件，而不是的`CPropertySheet`物件本身。

您可以建立一種稱為精靈，可引導使用者逐步完成的作業，例如設定裝置，或建立的電子報的屬性頁的序列包含屬性工作表的索引標籤對話方塊。 在精靈輸入 索引標籤對話方塊中，屬性頁沒有索引標籤上，而且只有一個屬性頁面會顯示一次。 此外，而不需要**確定**並**立即套用**按鈕，精靈類型索引標籤對話方塊具有**回** 按鈕，**下一步**或**完成** 按鈕，**取消** 按鈕，以及**協助** 按鈕。

若要建立精靈類型的對話方塊，請遵循與建立標準的屬性工作表，但呼叫時，會遵循相同的步驟[SetWizardMode](#setwizardmode)再呼叫[DoModal](#domodal)。 若要啟用精靈按鈕，請呼叫[SetWizardButtons](#setwizardbuttons)，若要自訂其功能與外觀上使用旗標。 若要啟用**完成**按鈕，呼叫[SetFinishText](#setfinishtext)使用者已在精靈的最後一頁上採取的動作之後。

如需有關如何使用`CPropertySheet`物件，請參閱文章[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="addpage"></a>  Cpropertysheet:: Addpage

加入屬性工作表中的最右邊的索引標籤的 [提供] 頁面。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要加入至屬性工作表頁。 不可以是 NULL。

### <a name="remarks"></a>備註

新增至您想要顯示的左到右順序的屬性工作表的頁面。

`AddPage` 新增[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)物件到`CPropertySheet`物件的清單中的頁面，但實際上不會建立頁面的視窗。 Framework 延後建立頁面的視窗，直到使用者選取該頁面。

當您將使用屬性頁`AddPage`，則`CPropertySheet`的父系`CPropertyPage`。 若要取得的屬性工作表的存取，從 [屬性] 頁面，呼叫[CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)。

您不需要一直等到建立屬性工作表視窗才呼叫`AddPage`。 一般而言，您會呼叫`AddPage`呼叫之前，先[DoModal](#domodal)或是[建立](#create)。

如果您呼叫`AddPage`之後顯示屬性頁、 索引標籤列將會反映新加入的頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>  CPropertySheet::Construct

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
要用於屬性工作表的標題的識別碼。

*pParentWnd*<br/>
屬性工作表的父視窗的指標。 如果是 NULL，則父視窗會是應用程式的主視窗。

*iSelectPage*<br/>
一開始會在最上層是頁面的索引。 預設值為加入至工作表的第一頁。

*pszCaption*<br/>
包含要用於屬性工作表的標題字串的指標。 不可以是 NULL。

*hbmWatermark*<br/>
[屬性] 頁面的浮水印點陣圖的控制代碼。

*hpalWatermark*<br/>
浮水印點陣圖和/或標頭點陣圖的調色盤的控制代碼。

*hbmHeader*<br/>
[屬性] 頁面的標頭點陣圖的控制代碼。

### <a name="remarks"></a>備註

如果其中一個類別建構函式不已經呼叫，請呼叫此成員函式。 例如，呼叫`Construct`當您宣告或配置的陣列`CPropertySheet`物件。 在陣列的情況下，您必須呼叫`Construct`陣列中每個成員。

若要顯示屬性工作表，請呼叫[DoModal](#domodal)或是[建立](#create)。 屬性工作表的標題列中，將會放在第一個參數中所包含的字串。

如果可以顯示浮水印和/或標頭的映像會自動使用的第三個或第四個原型`Construct`上面所列，您將有效的值傳給*hbmWatermark*， *hpalWatermark*及/或*hbmHeader*參數。

### <a name="example"></a>範例

下列範例示範在何種情況下您會呼叫`Construct`。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet

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
要用於屬性工作表的標題的識別碼。

*pParentWnd*<br/>
指向父視窗的屬性工作表。 如果是 NULL，則父視窗會是應用程式的主視窗。

*iSelectPage*<br/>
一開始會在最上層是頁面的索引。 預設值為加入至工作表的第一頁。

*pszCaption*<br/>
指向字串，包含要用於屬性工作表的標題。 不可以是 NULL。

*hbmWatermark*<br/>
屬性工作表的背景點陣圖控制代碼。

*hpalWatermark*<br/>
浮水印點陣圖和/或標頭點陣圖的調色盤控制代碼。

*hbmHeader*<br/>
[屬性] 頁面的標頭點陣圖控制代碼。

### <a name="remarks"></a>備註

若要顯示屬性工作表，請呼叫[DoModal](#domodal)或是[建立](#create)。 屬性工作表的標題列中，將會放在第一個參數中所包含的字串。

如果您有多個參數 （例如，如果您使用的陣列），使用[建構](#construct)而不是`CPropertySheet`。

如果可以顯示浮水印和/或標頭的映像會自動使用的第三個或第四個原型`CPropertySheet`上面，而且您將有效的值*hbmWatermark*， *hpalWatermark*，和 /或是*hbmHeader*參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>  CPropertySheet::Create

顯示強制回應屬性工作表。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
父視窗的點。 如果是 NULL，則父代是桌面。

*cheaderctrl:: Create*<br/>
屬性工作表的視窗樣式。 如需可用樣式的完整清單，請參閱[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwExStyle*<br/>
屬性工作表的延伸的視窗樣式。 如需可用樣式的完整清單，請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>傳回值

如果成功，建立屬性工作表，非零值。否則為 0。

### <a name="remarks"></a>備註

若要呼叫`Create`在建構函式，或您可以在叫用建構函式之後呼叫它。

預設樣式，藉由傳遞為-1 表示*cheaderctrl:: Create*，會實際 WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 預設的延伸視窗樣式，藉由傳遞 0 做為表示*dwExStyle*，是實際 WS_EX_DLGMODALFRAME。

`Create`成員函式傳回之後立即建立屬性工作表。 若要摧毀屬性工作表，呼叫[cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。

顯示呼叫的非強制回應屬性工作表`Create`並沒有 確定、 取消、 立即套用 和 說明 按鈕強制回應屬性工作表一樣。 使用者必須建立所需的按鈕。

若要顯示強制回應屬性工作表，請呼叫[DoModal](#domodal)改。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  Cpropertysheet:: Setwizardmode

顯示強制回應屬性工作表。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL 如果函式執行成功;否則便是 0 或-1。 如果已為精靈建立屬性工作表 (請參閱[SetWizardMode](#setwizardmode))，`DoModal`傳回 ID_WIZFINISH 或 IDCANCEL。

### <a name="remarks"></a>備註

傳回的值會對應到已關閉屬性工作表控制項的 ID。 此函式傳回之後，將已終結對應至屬性工作表，而且所有頁面的視窗。 物件本身仍會存在。 一般而言，您將從中擷取資料[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件之後`DoModal`傳回 IDOK。

若要顯示非強制回應屬性工作表，請呼叫[建立](#create)改。

從其對應的對話方塊資源建立屬性頁時，它可能會導致 first-chance 例外狀況。 這會產生從對話方塊資源的樣式變更為 必要樣式之前建立的頁面, 的 屬性 頁面。 因為資源通常是唯讀，則這會導致例外狀況。 系統會處理例外狀況，並會建立一份已修改的資源。 因此您可以忽略 first-chance 例外狀況。

> [!NOTE]
>  作業系統必須處理這個例外狀況，如果您使用非同步例外狀況處理模型進行編譯。 如需例外狀況處理模型的詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)。 在此情況下，不會換行對`CPropertySheet::DoModal`使用 c + + try / catch 區塊中捕捉處理所有例外狀況，例如`catch (...)`。 此區塊會處理例外狀況適用於作業系統，以及造成無法預期的行為。 不過，您可以安全地使用 c + + 例外狀況處理特定的例外狀況型別或結構化例外狀況處理其中的存取違規例外狀況會傳遞至作業系統。

若要避免產生此 first-chance 例外狀況，您可以手動保證屬性工作表具有正確[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 您必須設定下列屬性工作表樣式：

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

您可以使用下列的選擇性樣式，而不會造成 first-chance 例外狀況：

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

停用所有其他 Windows 樣式，因為它們不是與屬性工作表相容。 這項建議不適用於延伸樣式。 適當地設定這些標準的樣式，將會保證屬性工作表並沒有被修改，而且會避免在產生第一個可能發生的例外狀況。

### <a name="example"></a>範例

範例，請參閱[cpropertysheet:: Addpage](#addpage)。

##  <a name="enablestackedtabs"></a>  Cpropertysheet:: Enablestackedtabs

指出是否要在堆疊中的屬性工作表索引標籤的資料列。

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>參數

*bStacked*<br/>
表示屬性工作表中是否已啟用堆疊索引標籤。 設定停用堆疊的資料列的標籤*bStacked*為 FALSE。

### <a name="remarks"></a>備註

根據預設，如果屬性工作表有多個索引標籤，會超過單一資料列的寬度屬性工作表索引標籤就會堆疊在多個資料列。 若要使用捲動的索引標籤，而不是堆疊的索引標籤，呼叫`EnableStackedTabs`具有*bStacked*設為 FALSE，然後再呼叫[DoModal](#domodal)或是[建立](#create)。

您必須呼叫`EnableStackedTabs`當您建立強制回應或非強制回應屬性工作表。 若要將此樣式中的`CPropertySheet`-衍生類別，撰寫 WM_CREATE 訊息處理常式。 中的覆寫版本[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，呼叫`EnableStackedTabs( FALSE )`之前先呼叫基底類別實作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

屬性工作表就會終止。

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>參數

*nEndID*<br/>
要做為傳回值的屬性工作表的識別碼。

### <a name="remarks"></a>備註

按下 [確定]、 [取消] 或 [關閉] 按鈕時，此成員函式是由架構呼叫。 如果發生事件，此成員函式應該關閉屬性工作表的呼叫。

此成員函式只能搭配強制回應對話方塊。

### <a name="example"></a>範例

範例，請參閱[CPropertySheet::PressButton](#pressbutton)。

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

取得屬性工作表視窗的使用中頁面的索引數目，然後使用傳回的索引編號，做為參數`GetPage`。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>傳回值

使用中的頁面索引編號。

### <a name="example"></a>範例

範例，請參閱[CPropertySheet::GetActivePage](#getactivepage)。

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

擷取屬性工作表視窗的使用中的頁面。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>傳回值

使用中的頁面指標。

### <a name="remarks"></a>備註

使用此成員函式，以在使用中的頁面上執行某些動作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>  CPropertySheet::GetPage

讓指標回到指定的頁面，此屬性工作表中。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>參數

*n 版面*<br/>
所需的頁面上，索引從 0 開始。 必須介於 0 與小於屬性工作表，內含中的頁數。

### <a name="return-value"></a>傳回值

要對應至的頁面的指標*n 版面*參數。

### <a name="example"></a>範例

範例，請參閱[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

判斷目前在屬性工作表中的頁數。

```
int GetPageCount() const;
```

### <a name="return-value"></a>傳回值

屬性工作表中的頁面數目。

### <a name="example"></a>範例

範例，請參閱[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

擷取屬性工作表中指定的頁面索引數目。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
要尋找的索引頁面的點。 不可以是 NULL。

### <a name="return-value"></a>傳回值

頁面的索引編號。

### <a name="remarks"></a>備註

例如，您會使用`GetPageIndex`以取得頁面的索引，才能使用[SetActivePage](#setactivepage)或是[提示](#getpage)。

### <a name="example"></a>範例

範例，請參閱[CPropertySheet::GetActivePage](#getactivepage)。

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

擷取變數的指標，執行特定的索引標籤控制項項目索引標籤控制項 (也就是為使用中的 Api 任一[CTabCtrl](../../mfc/reference/ctabctrl-class.md))。

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>傳回值

指向的索引標籤控制項。

### <a name="remarks"></a>備註

例如，如果您想要在初始化期間，將點陣圖新增至每個索引標籤時，才能呼叫此成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

結構，其成員儲存的特性[PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2)。

### <a name="remarks"></a>備註

使用此結構來建構它之後，但它會顯示與之前初始化的屬性工作表外觀[DoModal](#domodal)成員函式。 例如，設定*dwSize*隸屬`m_psh`大小要將屬性工作表。

如需這個結構，包括其成員，清單的詳細資訊，請參閱 Windows SDK 中的 PROPSHEETHEADER。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

將矩形的對話方塊單位轉換成螢幕單位中。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)協調要轉換的物件，其中包含對話方塊。

### <a name="remarks"></a>備註

對話方塊單位是根據衍生自的平均的寬度和高度，用於對話方塊中文字的字型中的字元目前對話方塊基底單位所述。 水平的單位是對話方塊基底寬度單位的四分之一，一個垂直單位對話方塊基底的高度的單位的八分之一。

[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) Windows 函式會傳回系統字型的大小資訊，但如果您使用 DS_SETFONT 樣式在資源定義檔案中，您可以指定不同的字型，每一個屬性工作表。 [MapDialogRect](/windows/desktop/api/winuser/nf-winuser-mapdialogrect) Windows 函式，描述在 Windows SDK 中，會使用適當的字型，此對話方塊。

`MapDialogRect`成員函式會取代中的對話方塊單位*lpRect*與畫面單位 （像素），讓矩形可用來建立對話方塊或調整控制項在方塊內的位置。

##  <a name="oninitdialog"></a>  Cpropertysheet:: Oninitdialog

覆寫以擴大屬性工作表初始化。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定應用程式是否已設定為其中一個屬性工作表中的控制項的輸入的焦點。 如果`OnInitDialog`傳回非零值，Windows 就會將輸入的焦點設定為屬性工作表中的第一個控制項。 應用程式可以在明確設定為其中一個屬性工作表中的控制項輸入的焦點時，才傳回 0。

### <a name="remarks"></a>備註

此成員函式會呼叫以回應 WM_INITDIALOG 訊息。 此訊息會傳送至屬性工作表期間[建立](#create)或是[DoModal](#domodal)屬性工作表顯示之前，立即進行的呼叫。

如果您需要執行特殊處理初始化的屬性工作表時，請覆寫此成員函式。 在覆寫的版本中，先呼叫基底類別`OnInitDialog`但忽略它的傳回值。 您通常會從您的覆寫的成員函式傳回 TRUE。

您不需要此成員函式的訊息對應項目。

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

模擬屬性工作表中指定的按鈕的選擇。

```
void PressButton(int nButton);
```

### <a name="parameters"></a>參數

*n 按鈕*<br/>
n 按鈕： 識別被按下按鈕。 這個參數可以是下列值之一：

- PSBTN_BACK 會選擇 [上一頁] 按鈕。

- PSBTN_NEXT 選擇 [下一步] 按鈕。

- PSBTN_FINISH 會選擇 [完成] 按鈕。

- PSBTN_OK 會選擇 [確定] 按鈕。

- PSBTN_APPLYNOW 選擇立即套用 按鈕。

- PSBTN_CANCEL 會選擇 [取消] 按鈕。

- PSBTN_HELP 會選擇 [說明] 按鈕。

### <a name="remarks"></a>備註

請參閱[PSM_PRESSBUTTON](/windows/desktop/Controls/psm-pressbutton)如需有關 Windows SDK Pressbutton 訊息。

呼叫`PressButton`不會傳送[PSN_APPLY](/windows/desktop/Controls/psn-apply)屬性頁面架構的通知。 若要傳送此通知，請呼叫[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

從屬性工作表移除頁面，並終結相關聯的視窗。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要從屬性工作表移除頁面。 不可以是 NULL。

*n 版面*<br/>
要移除的頁面索引。 必須介於 0 與小於屬性工作表，內含中的頁數。

### <a name="remarks"></a>備註

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件本身並不會終結之前的擁有者`CPropertySheet`視窗已關閉。

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

變更使用中的頁面。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*n 版面*<br/>
若要設定頁面的索引。 它必須介於 0 與小於屬性工作表，內含中的頁數。

*pPage*<br/>
若要設定在屬性工作表頁面的點。 它不能是 NULL。

### <a name="return-value"></a>傳回值

如果屬性工作表已順利啟動，非零值。否則為 0。

### <a name="remarks"></a>備註

例如，使用`SetActivePage`如果在單一頁面上的使用者動作應該會造成另一個頁面，即可成為使用中的頁面。

### <a name="example"></a>範例

範例，請參閱[CPropertySheet::GetActivePage](#getactivepage)。

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

設定 [完成] 命令按鈕的文字。

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要顯示在 [完成] 命令按鈕的文字。

### <a name="remarks"></a>備註

呼叫`SetFinishText`顯示 完成 命令按鈕的文字，並在使用者完成精靈的最後一頁動作之後，隱藏下一步 和 上一步 按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

指定屬性工作表的標題 （框架視窗的標題列中顯示的文字）。

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
指定的屬性工作表頁標題的樣式。 必須指定樣式，在 0 或 PSH_PROPTITLE。 如果樣式設定為 PSH_PROPTITLE，「 屬性 」 這個字出現指定為標題的文字後面。 例如，呼叫`SetTitle`（"Simple"，PSH_PROPTITLE），將會導致屬性工作表頁標題的 「 簡單的屬性。 」

*lpszText*<br/>
指向要用作屬性工作表的標題列中的標題文字。

### <a name="remarks"></a>備註

根據預設，屬性工作表會使用屬性工作表的建構函式中 caption 參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

啟用或停用精靈屬性工作表中的 [上一步]、 [下一步] 或 [完成] 按鈕。

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
一組自訂的精靈按鈕的外觀與函式的旗標。 這個參數可以是下列值的組合：

- PSWIZB_BACK 上一步 按鈕

- PSWIZB_NEXT 下一步按鈕

- PSWIZB_FINISH 完成 按鈕

- PSWIZB_DISABLEDFINISH 已停用 [完成] 按鈕

### <a name="remarks"></a>備註

呼叫`SetWizardButtons`只有對話方塊開啟之後, 您不能呼叫`SetWizardButtons`再呼叫[DoModal](#domodal)。 一般而言，您應該呼叫`SetWizardButtons`從[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。

如果您想要變更 [完成] 按鈕的文字或隱藏 [下一步] 及 [上一步] 按鈕一次使用者已完成精靈中，呼叫[SetFinishText](#setfinishtext)。 請注意，同一個按鈕共用的 [完成] 和 [下一步]。 您可以顯示完成或下一步 按鈕一次，但非兩者。

### <a name="example"></a>範例

A`CPropertySheet`有三個精靈屬性頁面： `CStylePage`， `CColorPage`，和`CShapePage`。  下列程式碼片段示範如何啟用和停用**回復**並**下一步**精靈的 屬性 頁面上的按鈕。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  Cpropertysheet:: Domodal

為精靈就會建立屬性頁。

```
void SetWizardMode();
```

### <a name="remarks"></a>備註

精靈屬性頁的重要特性是使用者瀏覽下一步使用或完成，備份，請 [取消] 按鈕，而不是索引標籤。

呼叫`SetWizardMode`呼叫之前，先[DoModal](#domodal)。 在您呼叫後`SetWizardMode`，`DoModal`會傳回 IDCANCEL 或 ID_WIZFINISH （如果使用者關閉與 [完成] 按鈕）。

`SetWizardMode` 設定 PSH_WIZARD 旗標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)<br/>
[MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)<br/>
[MFC 範例 PROPDLG](../../visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
