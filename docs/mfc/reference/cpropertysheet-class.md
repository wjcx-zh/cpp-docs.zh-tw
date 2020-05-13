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
ms.openlocfilehash: e8ab91b9a6fe76070d79ea2eee2e5765db2e99e3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750967"
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
|[C 屬性表:C屬性表](#cpropertysheet)|建構 `CPropertySheet` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 屬性表::新增頁](#addpage)|將頁面新增至屬性工作表。|
|[C 屬性表:建構](#construct)|建構 `CPropertySheet` 物件。|
|[C 屬性表:建立](#create)|顯示無模式屬性表。|
|[C屬性表::Do 模態](#domodal)|顯示模態屬性表。|
|[C 屬性表::啟用堆疊選項卡](#enablestackedtabs)|指示屬性表是使用堆疊選項卡還是滾動選項卡。|
|[C 屬性表:結束對話](#enddialog)|終止屬性表。|
|[C 屬性表:抓取活動索引](#getactiveindex)|檢索屬性表的活動頁的索引。|
|[C 屬性表:抓取活動頁面](#getactivepage)|返回活動頁物件。|
|[C 屬性表:取得頁面](#getpage)|檢索指向指定頁面的指標。|
|[C 屬性表:取得頁面計數](#getpagecount)|檢索屬性表中的頁數。|
|[C 屬性表:取得頁面索引](#getpageindex)|檢索屬性表指定頁的索引。|
|[C 屬性表:抓取Tab控制](#gettabcontrol)|檢索指向選項卡控件的指標。|
|[C 屬性表:mapDialogrect](#mapdialogrect)|將矩形的對話框單位轉換為屏幕單位。|
|[C屬性表:onInitDialog](#oninitdialog)|重寫以增強屬性表初始化。|
|[C屬性表::PresButton](#pressbutton)|類比屬性表中指定按鈕的選擇。|
|[C 屬性表:刪除頁](#removepage)|從屬性工作表中刪除頁面。|
|[C 屬性表::設定活動頁](#setactivepage)|以程式設計方式設置活動頁面物件。|
|[C 屬性表::設定完成文字](#setfinishtext)|設置"完成"按鈕的文字。|
|[C 屬性表::設定標題](#settitle)|設置屬性表的標題。|
|[C 屬性表::設定精靈按鈕](#setwizardbuttons)|啟用嚮導按鈕。|
|[C 屬性表::設定精靈模式](#setwizardmode)|啟用嚮導模式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C屬性表:m_psh](#m_psh)|Windows [PROPSHEETHEADER 結構](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)。 提供對基本屬性表參數的訪問。|

## <a name="remarks"></a>備註

屬性表由物件`CPropertySheet`和一個或多個[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件組成。 框架將屬性表顯示為一個視窗,其中包含一組選項卡索引和包含當前選取頁面的區域。 使用者使用相應的選項卡導航到特定頁面。

`CPropertySheet`支援 Windows 98 和 Windows NT 2000 中引入的擴展[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)結構。 該結構包含支援使用「水印」背景位圖的其他標誌和成員。

要在屬性表物件中自動顯示這些新影像,請將呼叫[CPropertySheet::建構](#construct)或[CPropertySheet:CPropertySheet](#cpropertysheet)中的位圖和調色板影像的有效值傳遞給 。

即使`CPropertySheet`不是從[CDialog](../../mfc/reference/cdialog-class.md)`CPropertySheet`派生的 ,管理物件`CDialog`就像管理物件一 樣。 例如,建立屬性表需要兩個部分建構:呼叫式建構函數,然後呼叫樣式屬性表[DoModal](#domodal)或為無模式屬性表[建立](#create)。 `CPropertySheet`有兩種類型的建構函數[:C 屬性表:建構](#construct)與 C[屬性表::C 屬性表](#cpropertysheet)。

構造`CPropertySheet`物件時,某些[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)可能會導致發生第一次異常。 這是系統嘗試在創建工作表之前更改屬性表樣式的結果。 為了避免此異常,請確保在建立`CPropertySheet`時 設定以下樣式:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

以下樣式是可選的,不會導致第一次機會異常:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

任何其他`Window Styles`是被禁止的,你不應該啟用他們。

在`CPropertySheet`物件和外部對象之間交換數據類似`CDialog`於與 物件交換數據。 重要的區別是屬性表的設置通常是物件的成員變數,`CPropertyPage`而不是物件本身的成員`CPropertySheet`變數。

您可以創建稱為嚮導的選項卡對話框類型,該對話方塊由包含一系列屬性頁的屬性表組成,該屬性頁指導使用者完成操作的步驟,例如設置設備或創建新聞稿。 在嚮導類型選項卡對話方塊中,屬性頁沒有選項卡,並且一次只能看到一個屬性頁。 此外,精靈類型選項卡對話框沒有 **「確定**」和 **「立即應用」** 按鈕,而是具有 **「後退」** 按鈕 **、「下一步**」 或 **「完成」** 按鈕 **、」取消「 按鈕**和 **」説明**「 按鈕」。

要創建嚮導類型對話框,請按照創建標準屬性表的步驟執行相同的步驟,但在調用[DoModal](#domodal)之前調用[SetWizardMode。](#setwizardmode) 要啟用精靈按鈕,請使用標誌調用[SetWizardButtons](#setwizardbuttons)來自定義其功能和外觀。 要啟用 **「完成」** 按鈕,請使用者在嚮導的最後一頁上執行操作後呼叫[SetFinishText。](#setfinishtext)

有關如何使用`CPropertySheet`物件的詳細資訊,請參閱文章[「屬性表」和「屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>C 屬性表::新增頁

在屬性表中添加提供的最右側選項卡的頁面。

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要添加到屬性表的頁面。 不能是 NULL。

### <a name="remarks"></a>備註

按從左至右的順序將頁面添加到屬性工作表,您希望它們顯示。

`AddPage`將[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)物件`CPropertySheet`添加到 物件的頁面清單中,但實際上不會為頁面創建視窗。 框架將推遲創建頁面的視窗,直到用戶選擇該頁面。

使用`AddPage`新增 屬性頁`CPropertySheet`時,`CPropertyPage`是的父頁。 要從屬性頁存取屬性表,請致電[CWnd::getParent](../../mfc/reference/cwnd-class.md#getparent)。

不必建立屬性表視窗才能呼叫`AddPage`。 通常,您將在呼叫`AddPage` [DoModal](#domodal)或[建立](#create)之前呼叫 。

如果在顯示屬性`AddPage`頁後調用,選項卡行將反映新添加的頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>C 屬性表:建構

建構 `CPropertySheet` 物件。

```cpp
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
用於屬性表的標題的 ID。

*pparentwnd*<br/>
指向屬性表的父視窗。 如果為 NULL,則父視窗將是應用程式的主視窗。

*iSelectPage*<br/>
最初位於頂部的頁面索引。 默認值是添加到工作表的第一頁。

*pszCaption*<br/>
指向包含要用於屬性表的標題的字串的指標。 不能是 NULL。

*hbm沃特馬克*<br/>
處理屬性頁的水印位圖。

*赫帕爾沃特馬克*<br/>
處理水印位圖和/或標題位圖的調色板。

*hbmHeader*<br/>
處理屬性頁的頭點陣圖。

### <a name="remarks"></a>備註

如果尚未調用一個類構造函數,請調用此成員函數。 例如,在聲明`Construct`或`CPropertySheet`分配 物件陣列時調用。 對於陣列,必須調用`Construct`陣列中的每個成員。

要顯示屬性工作表,請呼叫[「使用模式」](#domodal)或[「建立](#create)」 。 第一個參數中包含的字串將放置在屬性表的標題欄中。

如果使用上面列出的 第三個或第`Construct`四 個原型,並且傳遞*hbmWatermark、hpalWatermark*和/或*hbmHeader*參數的有效值*hpalWatermark*,則可以自動顯示浮浮水印和/或標題圖像。

### <a name="example"></a>範例

下面的範例展示在什麼情況下調用`Construct`。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>C 屬性表:C屬性表

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
用於屬性表的標題的 ID。

*pparentwnd*<br/>
指向屬性表的父視窗。 如果為 NULL,則父視窗將是應用程式的主視窗。

*iSelectPage*<br/>
最初位於頂部的頁面索引。 默認值是添加到工作表的第一頁。

*pszCaption*<br/>
指向包含要用於屬性表的標題的字串。 不能是 NULL。

*hbm沃特馬克*<br/>
屬性表的背景位圖的句柄。

*赫帕爾沃特馬克*<br/>
水印位圖和/或頭位圖調色板的句柄。

*hbmHeader*<br/>
屬性頁頭點圖的句柄。

### <a name="remarks"></a>備註

要顯示屬性工作表,請呼叫[「使用模式」](#domodal)或[「建立](#create)」 。 第一個參數中包含的字串將放置在屬性表的標題欄中。

如果有多個參數(例如,如果使用陣列),請使用[建構](#construct)而不是`CPropertySheet`。

如果您使用上面的第三個或第四`CPropertySheet`個原型,並且傳遞*hbmWatermark、hpalWatermark*和/或*hbmHeader*參數的有效值*hpalWatermark*,則可以自動顯示水印和/或標題圖像。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>C 屬性表:建立

顯示無模式屬性表。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向父視窗。 如果為 NULL,則父級是桌面。

*dwStyle*<br/>
屬性表的視窗樣式。 關於可用樣式的完整清單,請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。

*dwExStyle*<br/>
屬性表的擴展視窗樣式。 有關可用樣式的完整清單,請參閱[延伸視窗樣式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>傳回值

成功創建屬性表時為非零;否則 0。

### <a name="remarks"></a>備註

調用`Create`可以位於構造函數內部,也可以在調用構造函數后調用它。

默認樣式,通過傳遞 -1 表示為*dwStyle,* 實際上是WS_SYSMENU&#124;&#124;WS_POPUP&#124;&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE。 默認擴展視窗樣式(通過將 0 表示為*dwExStyle)* 表示,實際上是WS_EX_DLGMODALFRAME。

成員`Create`函數在創建屬性表後立即返回。 要銷毀屬性表,請致電[CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow)。

與模式屬性表一樣,顯示的`Create`未模屬性表具有"確定"、"取消"、"立即應用"和"説明"按鈕。 所需的按鈕必須由用戶創建。

要顯示模態屬性表,請改為調用[DoModal。](#domodal)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>C屬性表::Do 模態

顯示模態屬性表。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

IDOK 或 IDCANCEL(如果函數成功);否則為 0 或 -1。 如果屬性表已設置為嚮導(請參閱[SetWizardMode),](#setwizardmode)`DoModal`則返回ID_WIZFINISH或 IDCANCEL。

### <a name="remarks"></a>備註

返回值對應於關閉屬性表的控制項的 ID。 返回此函數後,與屬性表和所有頁面對應的視窗將被銷毀。 物件本身將仍然存在。 通常,您將在返回 IDOK`DoModal`後從[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件檢索數據。

要顯示無模式屬性表,請改為"[創建](#create)"。

當從相應的對話框資源創建屬性頁時,可能會導致第一次異常。 這源於屬性頁在創建頁面之前將對話框資源的樣式更改為所需的樣式。 由於資源通常是唯讀的,因此會導致異常。 系統處理異常,並創建修改後的資源的副本。 因此,可以忽略第一個異常。

> [!NOTE]
> 如果要使用非同步異常處理模型進行編譯,操作系統必須處理此異常。 有關異常處理模型的詳細資訊,請參閱[/EH(異常處理模型)。](../../build/reference/eh-exception-handling-model.md) 在這種情況下,不要`CPropertySheet::DoModal`用C++嘗試 catch 塊對 呼叫`catch (...)`進行包裝, 其中 catch 處理所有異常,例如 。 此塊將處理用於操作系統的異常,並導致不可預知的行為。 但是,在訪問衝突異常傳遞到操作系統時,可以使用具有特定異常類型或結構化異常處理C++異常處理。

為了避免產生此第一個異常,您可以手動保證屬性表具有正確的[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 您必須為屬性表設定以下樣式:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

您可以使用以下可選樣式,而不會造成第一次異常:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

禁用所有其他 Windows 樣式,因為它們與屬性表不相容。 此建議不適用於擴展樣式。 適當地設置這些標準樣式將保證屬性表不必修改,並且將避免生成第一個異常。

### <a name="example"></a>範例

請參考[CPropertySheet 的範例::新增頁](#addpage)。

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>C 屬性表::啟用堆疊選項卡

指示是否將選項卡行堆疊在屬性工作表中。

```cpp
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>參數

*b 堆疊*<br/>
指示在屬性表中是否啟用了堆疊選項卡。 通過將*bStacked*設置為 FALSE 來禁用堆疊的標記行。

### <a name="remarks"></a>備註

默認情況下,如果屬性工作表的選項卡數多於屬性工作表寬度中的一行,則選項卡將堆疊在多行中。 要使用捲軸選項卡而不是堆疊選項卡,請`EnableStackedTabs`呼叫*bStacked*設定為 FALSE,然後再呼叫[DoModal](#domodal)或[建立](#create)。

創建模態`EnableStackedTabs`或無模式屬性表時必須調用。 要將此樣式合併到`CPropertySheet`派生類中,請為WM_CREATE編寫消息處理程式。 在重寫版本的[CWnd::onCreate](../../mfc/reference/cwnd-class.md#oncreate)中,`EnableStackedTabs( FALSE )`調用 基類實現之前調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>C 屬性表:結束對話

終止屬性表。

```cpp
void EndDialog(int nEndID);
```

### <a name="parameters"></a>參數

*nEndID*<br/>
用作屬性表的返回值的標識符。

### <a name="remarks"></a>備註

按下"確定"、"取消"或"關閉"按鈕時,框架將調用此成員函數。 如果發生應關閉屬性表的事件,請調用此成員函數。

此成員函數僅與模式對話框一起使用。

### <a name="example"></a>範例

請參閱[CPropertySheet::PresButton](#pressbutton)"的範例。

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>C 屬性表:抓取活動索引

獲取屬性工作表視窗的活動頁的索引號,然後使用返回的索引號作為`GetPage`的參數。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>傳回值

活動頁的索引號。

### <a name="example"></a>範例

請參考[CPropertySheet 的範例:取得活動頁](#getactivepage)。

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>C 屬性表:抓取活動頁面

檢索屬性工作表視窗的活動頁。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>傳回值

指向活動頁的指標。

### <a name="remarks"></a>備註

使用此成員函數在活動頁上執行某些操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>C 屬性表:取得頁面

返回指向此屬性表中指定頁面的指標。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>參數

*nPage*<br/>
所需頁面的索引,從 0 開始。 必須小於屬性表中的頁數 0 和 1(包括)。

### <a name="return-value"></a>傳回值

指向與*nPage*參數對應的頁面的指標。

### <a name="example"></a>範例

請參閱[CPropertyPage 的範例::在精靈完成](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>C 屬性表:取得頁面計數

確定屬性表中目前頁數。

```
int GetPageCount() const;
```

### <a name="return-value"></a>傳回值

屬性表中的頁數。

### <a name="example"></a>範例

請參閱[CPropertyPage 的範例::在精靈完成](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>C 屬性表:取得頁面索引

檢索屬性表中指定頁面的索引號。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要找到的索引的頁面。 不能是 NULL。

### <a name="return-value"></a>傳回值

頁面的索引編號。

### <a name="remarks"></a>備註

例如,您可以使用`GetPageIndex`取得頁面索引,以便使用[SetActivePage](#setactivepage)或[GetPage](#getpage)。

### <a name="example"></a>範例

請參考[CPropertySheet 的範例:取得活動頁](#getactivepage)。

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>C 屬性表:抓取Tab控制

檢索指向選項卡控制項的指標,以執行特定於選項卡控制項(即使用[CTabCtrl](../../mfc/reference/ctabctrl-class.md)中的任何 API)

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>傳回值

指向選項卡控件的指標。

### <a name="remarks"></a>備註

例如,如果要在初始化期間向每個選項卡添加位圖,請調用此成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>C屬性表:m_psh

其成員存儲[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)特徵的結構。

### <a name="remarks"></a>備註

使用此結構在建構屬性表後,但在使用[DoModal](#domodal)成員函數顯示屬性表之前初始化它的外觀。 例如,將的`m_psh` *dwSize*成員設置為您希望屬性表具有的大小。

有關此結構的詳細資訊(包括其成員的清單),請參閱 Windows SDK 中的 PROPSHEETHEADER。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>C 屬性表:mapDialogrect

將矩形的對話框單位轉換為屏幕單位。

```cpp
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含要轉換的對話方塊座標的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件。

### <a name="remarks"></a>備註

對話框單位根據當前對話框基本單位表示,該單位派生自對話框文本字體中字元的平均寬度和高度。 一個水平單位是對話框基寬單位的四分之一,一個垂直單位是對話框基本高度單位的八分之一。

[GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 函數傳回系統字型的大小資訊,但如果在資源定義檔中使用DS_SETFONT樣式,則可以為每個屬性表指定不同的字體。 Windows SDK 中描述的[MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows 功能為此對話方塊使用相應的字型。

成員`MapDialogRect`函數將*lpRect*中的對話框單元替換為螢幕單位(圖元),以便矩形可用於創建對話方塊或在框中放置控制項。

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>C屬性表:onInitDialog

用於增強屬性表初始化的重寫。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定應用程式是否已將輸入焦點設定為屬性表中的一個控制項。 如果`OnInitDialog`返回非零,Windows 會將輸入焦點設置到屬性表中的第一個控制項。 僅當應用程式顯示式將輸入焦點設定為屬性表中的一個控制項時,應用程式才能返回 0。

### <a name="remarks"></a>備註

調用此成員函數以回應WM_INITDIALOG消息。 此消息在[創建](#create)或[DoModal](#domodal)調用期間發送到屬性表,這些調用在顯示屬性表之前發生。

如果在初始化屬性表時需要執行特殊處理,則重寫此成員函數。 在重寫版本中,首先調用基類`OnInitDialog`,但忽略其返回值。 您通常會從重寫的成員函數返回 TRUE。

不需要此成員函數的消息映射條目。

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>C屬性表::PresButton

類比屬性表中指定按鈕的選擇。

```cpp
void PressButton(int nButton);
```

### <a name="parameters"></a>參數

*nButton*<br/>
nButton :標識要按下的按鈕。 這裡可以是以下值之一:

- PSBTN_BACK選擇"後退"按鈕。

- PSBTN_NEXT選擇「下一步」 按鈕。

- PSBTN_FINISH 選擇"完成"按鈕。

- PSBTN_OK 選擇"確定"按鈕。

- PSBTN_APPLYNOW選擇「立即應用」按鈕。

- PSBTN_CANCEL選擇"取消"按鈕。

- PSBTN_HELP 選擇"説明"按鈕。

### <a name="remarks"></a>備註

有關 Windows SDK 按下按鈕消息的詳細資訊,請參閱[PSM_PRESSBUTTON。](/windows/win32/Controls/psm-pressbutton)

呼叫`PressButton`不會將[PSN_APPLY](/windows/win32/Controls/psn-apply)通知從屬性頁發送到框架。 要送出此通知,請致電[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>C 屬性表:刪除頁

從屬性工作表中刪除頁面並銷毀關聯的視窗。

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
指向要從屬性表中刪除的頁面。 不能是 NULL。

*nPage*<br/>
要刪除的頁面的索引。 必須小於屬性表中的頁數 0 和 1(包括)。

### <a name="remarks"></a>備註

在`CPropertySheet`關閉視窗的所有者之前,不會銷毀[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件本身。

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>C 屬性表::設定活動頁

更改活動頁。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*nPage*<br/>
要設置的頁面的索引。 它必須小於屬性表中的頁數 0 和 1(包括)。

*pPage*<br/>
指向要在屬性表中設置的頁面。 它不可為 NULL。

### <a name="return-value"></a>傳回值

如果成功激活屬性表,則非零;否則 0。

### <a name="remarks"></a>備註

例如,如果使用者在`SetActivePage`一頁上的操作應導致另一個頁面成為活動頁,請使用。

### <a name="example"></a>範例

請參考[CPropertySheet 的範例:取得活動頁](#getactivepage)。

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>C 屬性表::設定完成文字

在"完成"指令按鈕中設置文本。

```cpp
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向要顯示在"完成"指令按鈕上的文字。

### <a name="remarks"></a>備註

呼叫`SetFinishText`以在「完成」指令按鈕上顯示文本,並在使用者完成嚮導最後一頁上的操作後隱藏「下一步」 和「後退」 按鈕。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>C 屬性表::設定標題

指定屬性表的標題(框架視窗的標題列中顯示的文字)。

```cpp
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
指定屬性工作表標題的樣式。 樣式必須在 0 或 PSH_PROPTITLE時指定。 如果樣式設置為PSH_PROPTITLE,則單詞"屬性"將顯示在指定為標題的文本之後。 例如,調用`SetTitle`("簡單",PSH_PROPTITLE)將導致「簡單屬性」的屬性表標題。

*lpszText*<br/>
指向要用作屬性表標題列中標題的文本。

### <a name="remarks"></a>備註

預設情況下,屬性表在屬性表構造函數中使用標題參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>C 屬性表::設定精靈按鈕

啟用或禁用嚮導屬性表中的"後退"、"下一步"或"完成"按鈕。

```cpp
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
一組標誌,用於自定義嚮導按鈕的功能和外觀。 這裡可以是以下值的組合:

- PSWIZB_BACK「後退」按鈕

- PSWIZB_NEXT 下一個按鈕

- PSWIZB_FINISH完成按鈕

- PSWIZB_DISABLEDFINISH關閉完成按鈕

### <a name="remarks"></a>備註

僅在`SetWizardButtons`對話框打開後調用;在致電[DoModal](#domodal)之前`SetWizardButtons`,你不能打電話。 通常,您應該從`SetWizardButtons`[CPropertyPage 呼叫:開啟活動](../../mfc/reference/cpropertypage-class.md#onsetactive)。

如果要更改「完成」按鈕上的文字,或在使用者完成精靈後隱藏「下一步」和「後退」按鈕,請呼叫[SetFinishText](#setfinishtext)。 請注意,為"完成"和"下一步"共用同一按鈕。 可以一次顯示"完成"或"下一步"按鈕,但不能同時顯示兩者。

### <a name="example"></a>範例

A`CPropertySheet`有三個精靈屬性`CStylePage``CColorPage`頁`CShapePage`: 與 。  下面的片段的示範如何啟用和關閉精靈屬性頁上的 **「後退**」和 **「下一步**」按鈕。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>C 屬性表::設定精靈模式

將屬性頁建立為嚮導。

```cpp
void SetWizardMode();
```

### <a name="remarks"></a>備註

嚮導屬性頁的一個關鍵特徵是使用者使用「下一步」或「完成」、「後退」 和「取消」按鈕而不是選項卡進行導航。

通話`SetWizardMode` [DoModal](#domodal)之前撥打電話 。 呼叫`SetWizardMode`後,`DoModal`將傳回ID_WIZFINISH(如果使用者關閉"完成"按鈕)或 IDCANCEL。

`SetWizardMode`設置PSH_WIZARD標誌。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
