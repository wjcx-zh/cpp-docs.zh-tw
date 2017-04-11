---
title: "CPropertySheet 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- dialog boxes, tabs
- CPropertySheet class
- property sheets, CPropertySheet class
- tab dialog boxes
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: 30
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: bfd4280a9163023ff9b824aee0d37fd50e2fb678
ms.lasthandoff: 04/01/2017

---
# <a name="cpropertysheet-class"></a>CPropertySheet 類別
表示屬性工作表，也稱為索引標籤對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CPropertySheet : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](#cpropertysheet)|建構 `CPropertySheet` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Cpropertysheet:: Addpage](#addpage)|將頁面新增至屬性工作表。|  
|[CPropertySheet::Construct](#construct)|建構 `CPropertySheet` 物件。|  
|[CPropertySheet::Create](#create)|顯示強制回應屬性工作表。|  
|[Cpropertysheet:: Setwizardmode](#domodal)|顯示強制回應屬性工作表。|  
|[Cpropertysheet:: Enablestackedtabs](#enablestackedtabs)|表示屬性工作表是否使用堆疊或捲動的索引標籤。|  
|[CPropertySheet::EndDialog](#enddialog)|屬性工作表就會終止。|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|擷取的屬性工作表的使用中頁面的索引。|  
|[CPropertySheet::GetActivePage](#getactivepage)|傳回使用中的頁面物件。|  
|[CPropertySheet::GetPage](#getpage)|擷取指定的頁面的指標。|  
|[CPropertySheet::GetPageCount](#getpagecount)|擷取的屬性工作表中的頁數。|  
|[CPropertySheet::GetPageIndex](#getpageindex)|擷取指定的屬性工作表頁面索引。|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|擷取索引標籤控制項的指標。|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|將矩形的對話方塊單位轉換成螢幕單位。|  
|[Cpropertysheet:: Oninitdialog](#oninitdialog)|覆寫以擴大屬性工作表的初始設定。|  
|[CPropertySheet::PressButton](#pressbutton)|模擬選擇的屬性工作表中指定的按鈕。|  
|[CPropertySheet::RemovePage](#removepage)|移除屬性工作表中的頁面。|  
|[CPropertySheet::SetActivePage](#setactivepage)|以程式設計方式設定的使用中的頁面物件。|  
|[CPropertySheet::SetFinishText](#setfinishtext)|設定完成 5d; 按鈕的文字。|  
|[CPropertySheet::SetTitle](#settitle)|設定屬性工作表的標題。|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|可讓精靈按鈕。|  
|[Cpropertysheet:: Domodal](#setwizardmode)|可讓精靈模式。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)結構。 提供基本的屬性工作表參數的存取權。|  
  
## <a name="remarks"></a>備註  
 屬性工作表包含`CPropertySheet`物件和一或多個[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件。 架構具有一組索引標籤索引和包含在目前選取的頁面區域的視窗以顯示屬性工作表。 使用者巡覽至特定頁面使用適當的索引標籤。  
  
 `CPropertySheet`提供支援展開[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)結構中導入[!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)]和 Windows NT 2000。 此結構包含其他旗標和支援使用 「 配額上限 」 的背景點陣圖的成員。  
  
 在屬性工作表物件中自動顯示這些新的映像，有效值的點陣圖和調色盤映像的呼叫中傳遞[CPropertySheet::Construct](#construct)或[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 即使`CPropertySheet`不衍生自[CDialog](../../mfc/reference/cdialog-class.md)、 管理`CPropertySheet`物件就像是管理`CDialog`物件。 例如，屬性工作表的建立需要兩部分建構︰ 呼叫建構函式，然後再呼叫[DoModal](#domodal)強制回應屬性工作表或[建立](#create)非強制回應屬性工作表。 `CPropertySheet`有兩種類型的建構函式︰ [CPropertySheet::Construct](#construct)和[CPropertySheet::CPropertySheet](#cpropertysheet)。  
  
 當您建構`CPropertySheet`物件時，有些[視窗樣式](../../mfc/reference/window-styles.md)可能會導致發生 first-chance 例外狀況。 這會產生從系統嘗試要變更屬性工作表樣式之前建立的工作表。 若要避免這個例外狀況，請確定當您建立時，設定下列樣式您`CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 下列樣式為選擇性，且不會發生第一個例外狀況︰  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 任何其他`Window Styles`禁止使用，您應該不啟用它們。  
  
 之間交換資料`CPropertySheet`物件和外部的物件是類似於與之交換資料`CDialog`物件。 重要的差異在於屬性工作表的設定通常是的成員變數`CPropertyPage`物件而不是的`CPropertySheet`物件本身。  
  
 您可以建立一種稱為精靈，其中包含屬性工作表使用一連串的步驟的作業，例如設定裝置，或建立新聞稿引導使用者的屬性頁 索引標籤對話方塊。 在精靈類型索引標籤 對話方塊中，屬性頁沒有索引標籤上，而且只有一個屬性頁面會顯示一次。 此外，而不需**確定**和**立即套用**按鈕時，精靈類型索引標籤對話方塊具有**回** 按鈕，**下一步**或**完成** 按鈕，**取消** 按鈕，和**協助** 按鈕。  
  
 若要建立精靈類型的對話方塊，請遵循相同的步驟，若要建立的標準屬性工作表，但呼叫之後，您會[SetWizardMode](#setwizardmode)之前先呼叫[DoModal](#domodal)。 若要啟用的精靈按鈕，請呼叫[SetWizardButtons](#setwizardbuttons)，若要自訂其功能與外觀上使用旗標。 若要啟用**完成**按鈕，請呼叫[SetFinishText](#setfinishtext)之後在精靈的最後一頁上的使用者採取動作。  
  
 如需有關如何使用`CPropertySheet`物件，請參閱文章[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。 此外，請參閱知識庫文章 Q146916︰ 如何︰ 建立非強制回應 CPropertySheet 標準按鈕，且發行項 Q300606︰ 如何︰ 設計可調整大小的 MFC 屬性工作表。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdlgs.h  
  
##  <a name="addpage"></a>Cpropertysheet:: Addpage  
 將提供的頁面索引標籤的最右邊加入屬性工作表中。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 `pPage`  
 指向要加入至屬性工作表頁。 不能**NULL**。  
  
### <a name="remarks"></a>備註  
 將頁面加入至屬性工作表，您想要顯示的左到右順序。  
  
 `AddPage`新增[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)物件`CPropertySheet`物件的頁面的清單，但實際上不會建立 [頁面] 視窗。 架構延後建立之視窗的頁面，直到使用者選擇該頁面。  
  
 當您將使用屬性頁`AddPage`、`CPropertySheet`的父系`CPropertyPage`。 若要存取的屬性工作表在內容頁上，呼叫[CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent)。  
  
 不需要等到建立屬性工作表視窗才呼叫`AddPage`。 一般而言，您會呼叫`AddPage`之前先呼叫[DoModal](#domodal)或[建立](#create)。  
  
 如果您呼叫`AddPage`之後顯示屬性頁，索引標籤列將會反映新加入的頁面。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>CPropertySheet::Construct  
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
 `nIDCaption`  
 要用於屬性工作表的標題識別碼。  
  
 `pParentWnd`  
 屬性工作表的父視窗的指標。 如果**NULL**，父視窗會在應用程式的主視窗。  
  
 `iSelectPage`  
 一開始會是最上層顯示頁面的索引。 預設值為加入至工作表的第一頁。  
  
 `pszCaption`  
 包含要用於屬性工作表的標題字串的指標。 不能**NULL**。  
  
 `hbmWatermark`  
 屬性頁的浮水印點陣圖的控制代碼。  
  
 `hpalWatermark`  
 浮水印點陣圖和/或標頭點陣圖的調色盤的控制代碼。  
  
 `hbmHeader`  
 [屬性] 頁面的標頭點陣圖的控制代碼。  
  
### <a name="remarks"></a>備註  
 如果類別建構函式的其中一個已尚未呼叫，請呼叫此成員函式。 例如，呼叫`Construct`當您宣告或配置的陣列`CPropertySheet`物件。 您必須在陣列的情況下呼叫`Construct`陣列中每個成員。  
  
 若要顯示屬性工作表，請呼叫[DoModal](#domodal)或[建立](#create)。 第一個參數中所包含的字串將放置在屬性工作表的標題列。  
  
 如果可以顯示浮水印和/或標頭的映像會自動使用第三個或第四個原型的`Construct`、 上面所列，而且您通過有效值`hbmWatermark`， `hpalWatermark`，及/或`hbmHeader`參數。  
  
### <a name="example"></a>範例  
 下列範例會示範在何種情況下您會呼叫`Construct`。  
  
 [!code-cpp[NVC_MFCDocView # 130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>CPropertySheet::CPropertySheet  
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
 `nIDCaption`  
 要用於屬性工作表的標題識別碼。  
  
 `pParentWnd`  
 指向父視窗的屬性工作表。 如果**NULL**，父視窗會在應用程式的主視窗。  
  
 `iSelectPage`  
 一開始會是最上層顯示頁面的索引。 預設值為加入至工作表的第一頁。  
  
 `pszCaption`  
 指向字串，包含要用於屬性工作表的標題。 不能**NULL**。  
  
 `hbmWatermark`  
 屬性工作表的背景點陣圖的控制代碼。  
  
 `hpalWatermark`  
 浮水印點陣圖和/或標頭點陣圖的調色盤的控制代碼。  
  
 `hbmHeader`  
 標頭點陣圖屬性頁的控制代碼。  
  
### <a name="remarks"></a>備註  
 若要顯示屬性工作表，請呼叫[DoModal](#domodal)或[建立](#create)。 第一個參數中所包含的字串將放置在屬性工作表的標題列。  
  
 如果您有多個參數 （例如，如果您使用的陣列） 時，使用[建構](#construct)而不是`CPropertySheet`。  
  
 如果可以顯示浮水印和/或標頭的映像會自動使用第三個或第四個原型的`CPropertySheet`、 以上版本，而且您將有效的值`hbmWatermark`， `hpalWatermark`，及/或`hbmHeader`參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>CPropertySheet::Create  
 顯示強制回應屬性工作表。  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 指向父視窗。 如果**NULL**，父為桌面。  
  
 `dwStyle`  
 屬性工作表的視窗樣式。 如需完整的可用樣式清單，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 `dwExStyle`  
 屬性工作表的延伸的視窗樣式。 可用樣式的完整清單，請參閱[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)  
  
### <a name="return-value"></a>傳回值  
 為非零，如果成功; 建立屬性工作表否則便是 0。  
  
### <a name="remarks"></a>備註  
 若要呼叫**建立**能放在建構函式，或在叫用建構函式之後呼叫它。  
  
 預設樣式，藉由傳遞為-1 表示`dwStyle`，實際上是**WS_SYSMENU |**`WS_POPUP`**|WS_CAPTION |DS_MODALFRAME |DS_CONTEXTHELP |WS_VISIBLE**。 預設的延伸視窗樣式，藉由傳遞 0 做為表示`dwExStyle`，實際上是**WS_EX_DLGMODALFRAME**。  
  
 **建立**成員函式傳回之後立即建立屬性工作表。 若要損毀的屬性工作表，請呼叫[cwnd:: Destroywindow](../../mfc/reference/cwnd-class.md#destroywindow)。  
  
 非強制回應屬性工作表顯示呼叫**建立**沒有 確定、 取消，立即套用 和 說明 按鈕強制回應屬性工作表一樣。 使用者必須建立所需的按鈕。  
  
 若要顯示強制回應屬性工作表，請呼叫[DoModal](#domodal)改為。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>Cpropertysheet:: Setwizardmode  
 顯示強制回應屬性工作表。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 `IDOK`或`IDCANCEL`函式是否成功; 否則為 0 或-1。 如果已為精靈建立屬性工作表 (請參閱[SetWizardMode](#setwizardmode))，`DoModal`傳回`ID_WIZFINISH`或`IDCANCEL`。  
  
### <a name="remarks"></a>備註  
 傳回值會對應至關閉屬性工作表控制項的 ID。 此函式傳回之後，將被終結對應至屬性工作表和所有頁面的視窗。 物件本身仍會存在。 一般而言，您將從中擷取資料[CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件之後`DoModal`傳回`IDOK`。  
  
 若要顯示非強制回應屬性工作表，請呼叫[建立](#create)改為。  
  
 從其對應的對話方塊資源建立屬性頁時，它可能會導致第一個可能發生例外狀況。 這會產生從 [屬性] 頁面建立頁面之前，變更對話方塊資源的樣式為必要的樣式。 因為資源通常是唯讀，則這會導致例外狀況。 系統會處理例外狀況，並會建立一份已修改的資源。 所以將略過第一個可能發生的例外狀況。  
  
> [!NOTE]
>  作業系統必須處理這個例外狀況，如果您正在編譯與非同步例外狀況處理模型。 多個例外狀況處理模型的詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)。 在此情況下，不會包裝對呼叫`CPropertySheet::DoModal`與 c + + try catch 區塊中捕捉處理所有例外狀況，例如`catch (...)`。 此區塊會處理例外狀況適用於作業系統，以及可能的原因無法預期的行為。 不過，您可以安全地使用 c + + 例外狀況處理與特定的例外狀況型別或結構化例外狀況處理其中存取違規的例外狀況會傳遞至作業系統。  
  
 若要避免產生此 first-chance 例外狀況，您可以手動保證屬性工作表已正確[視窗樣式](../../mfc/reference/window-styles.md)。 您必須設定下列屬性工作表樣式︰  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD  
  
-   WS_TABSTOP  
  
 您可以使用下列選擇性樣式，而不會造成 first-chance 例外狀況︰  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN  
  
 停用所有其他 Windows 樣式，因為它們不是與屬性工作表相容。 這項建議不適用於擴充的樣式。 適當地設定這些標準的樣式，將會保證不需要修改屬性工作表，並將可避免產生第一個可能發生例外狀況。  
  
### <a name="example"></a>範例  
  請參閱範例的[cpropertysheet:: Addpage](#addpage)。  
  
##  <a name="enablestackedtabs"></a>Cpropertysheet:: Enablestackedtabs  
 指出是否要在堆疊中的屬性工作表索引標籤的資料列。  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>參數  
 `bStacked`  
 表示屬性工作表中是否已啟用堆疊索引標籤。 停用堆疊的資料列的標籤設定`bStacked`至**FALSE**。  
  
### <a name="remarks"></a>備註  
 根據預設，如果屬性工作表具有多個索引標籤會超過單一資料列寬度屬性工作表索引標籤就會堆疊在多個資料列。 若要使用捲動的索引標籤而非堆疊索引標籤，呼叫`EnableStackedTabs`與`bStacked`設**FALSE**之前先呼叫[DoModal](#domodal)或[建立](#create)。  
  
 您必須呼叫`EnableStackedTabs`當您建立強制回應或非強制回應屬性工作表。 若要納入此樣式中的`CPropertySheet`-衍生類別，撰寫訊息處理常式的`WM_CREATE`。 中的覆寫版本[CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)，呼叫**EnableStackedTabs (FALSE)**然後再呼叫基底類別實作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>CPropertySheet::EndDialog  
 屬性工作表就會終止。  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>參數  
 *nEndID*  
 要做為傳回值的屬性工作表的識別碼。  
  
### <a name="remarks"></a>備註  
 按下 [確定]、 [取消] 或 [關閉] 按鈕時，此成員函式是由架構呼叫。 呼叫此成員函式，如果發生錯誤，應該關閉屬性工作表。  
  
 此成員函式只能搭配強制回應對話方塊。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertySheet::PressButton](#pressbutton)。  
  
##  <a name="getactiveindex"></a>CPropertySheet::GetActiveIndex  
 取得屬性工作表視窗的使用中頁面的索引數目，然後使用傳回的索引編號，做為參數`GetPage`。  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用中頁面的索引編號。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="getactivepage"></a>CPropertySheet::GetActivePage  
 擷取屬性工作表視窗的使用中的頁面。  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 要使用中頁面的指標。  
  
### <a name="remarks"></a>備註  
 使用此成員函式，以在使用中的頁面上執行某些動作。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>CPropertySheet::GetPage  
 讓指標回到指定的頁面，此屬性工作表中。  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>參數  
 `nPage`  
 所需的頁面上，索引 0 開始。 必須介於 0 與小於屬性工作表，內含頁數。  
  
### <a name="return-value"></a>傳回值  
 對應至的頁面指標`nPage`參數。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpagecount"></a>CPropertySheet::GetPageCount  
 決定目前在屬性工作表中的頁數。  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 屬性工作表中的頁面數目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)。  
  
##  <a name="getpageindex"></a>CPropertySheet::GetPageIndex  
 擷取指定屬性工作表中的頁面索引數目。  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 `pPage`  
 指向包含要尋找的索引的頁面。 不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 頁面的索引編號。  
  
### <a name="remarks"></a>備註  
 例如，您會使用`GetPageIndex`才能使用取得的頁面索引[SetActivePage](#setactivepage)或[提示](#getpage)。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="gettabcontrol"></a>CPropertySheet::GetTabControl  
 擷取執行特定的索引標籤控制項項目索引標籤控制項的指標 (也就是說，若要使用的 Api 中的任何[CTabCtrl](../../mfc/reference/ctabctrl-class.md))。  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤控制項的指標。  
  
### <a name="remarks"></a>備註  
 例如，如果您想要在初始化期間，新增至每個索引標籤的點陣圖時，才能呼叫此成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>CPropertySheet::m_psh  
 結構，其成員儲存的特性[PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546)。  
  
### <a name="remarks"></a>備註  
 使用此結構來初始化屬性工作表的外觀，它由建構後，但它會顯示與[DoModal](#domodal)成員函式。 例如，設定`dwSize`隸屬`m_psh`大小，您想將屬性工作表。  
  
 如需有關此結構，包括其成員的清單，請參閱**PROPSHEETHEADER**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>CPropertySheet::MapDialogRect  
 將矩形的對話方塊單位轉換成螢幕單位。  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含對話方塊来轉換的座標。  
  
### <a name="remarks"></a>備註  
 對話方塊單位會指出衍生自平均寬度和高度使用對話方塊中文字的字型中的字元目前對話方塊基底單元方面。 水平的單位是 4 個對話方塊的基底寬度單位，而垂直的單位對話方塊基底高度單位的八分之一。  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) Windows 函式會傳回系統字型的大小資訊，但是您可以指定不同的字型，每一個屬性工作表，如果您使用**DS_SETFONT**資源定義檔中的樣式。 [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) Windows 函式中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，此對話方塊會使用適當的字型。  
  
 `MapDialogRect`成員函式取代對話方塊單位`lpRect`與畫面單位 （像素為單位），使矩形可以用來建立對話方塊或調整控制項的方塊內的位置。  
  
##  <a name="oninitdialog"></a>Cpropertysheet:: Oninitdialog  
 覆寫以擴大屬性工作表的初始設定。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 指定應用程式是否已設定為其中一個屬性工作表中的控制項的輸入的焦點。 如果**OnInitDialog**傳回非零值時，Windows 就會將輸入的焦點設定為屬性工作表中的第一個控制項。 只有當它已明確設為其中一個屬性工作表中控制項的輸入的焦點，應用程式可以傳回 0。  
  
### <a name="remarks"></a>備註  
 此成員函式呼叫以回應**WM_INITDIALOG**訊息。 此訊息會傳送至屬性工作表期間[建立](#create)或[DoModal](#domodal)呼叫，就會發生在屬性表顯示之前。  
  
 如果您需要執行特殊處理初始化的屬性工作表時，請覆寫此成員函式。 在覆寫的版本中，先呼叫基底類別`OnInitDialog`但忽略它的傳回值。 您通常會傳回**TRUE**從您的覆寫的成員函式。  
  
 您不需要此成員函式的訊息對應項目。  
  
##  <a name="pressbutton"></a>CPropertySheet::PressButton  
 模擬選擇的屬性工作表中指定的按鈕。  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>參數  
 `nButton`  
 nButton︰ 識別可按的按鈕。 這個參數可以是下列值之一︰  
  
- **PSBTN_BACK**選擇 [上一頁] 按鈕。  
  
- **PSBTN_NEXT**選擇 [下一步] 按鈕。  
  
- **PSBTN_FINISH**選擇 [完成] 按鈕。  
  
- **PSBTN_OK**選擇 [確定] 按鈕。  
  
- **PSBTN_APPLYNOW**選擇立即套用 按鈕。  
  
- **PSBTN_CANCEL**選擇 [取消] 按鈕。  
  
- **PSBTN_HELP**選擇 [說明] 按鈕。  
  
### <a name="remarks"></a>備註  
 請參閱[PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597)如需有關 Windows SDK Pressbutton 訊息。  
  
 呼叫`PressButton`不會傳送[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)屬性頁架構的通知。 若要傳送此告知，呼叫[CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>CPropertySheet::RemovePage  
 從屬性工作表移除頁面，並終結相關聯的視窗。  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>參數  
 `pPage`  
 指向要從此屬性工作表頁。 不能`NULL`。  
  
 `nPage`  
 要移除的頁面索引。 必須介於 0 與小於屬性工作表，內含頁數。  
  
### <a name="remarks"></a>備註  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)物件本身並不會終結之前的擁有者`CPropertySheet`視窗已關閉。  
  
##  <a name="setactivepage"></a>CPropertySheet::SetActivePage  
 變更使用中的頁面。  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 `nPage`  
 若要設定頁面的索引。 它必須介於 0 與小於屬性工作表，內含頁數。  
  
 `pPage`  
 在屬性工作表中設定頁面的點。 它不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果已成功; 啟動屬性工作表，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 例如，使用`SetActivePage`如果在單一頁面上的使用者動作應該會變成使用中頁面的另一個頁面。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertySheet::GetActivePage](#getactivepage)。  
  
##  <a name="setfinishtext"></a>CPropertySheet::SetFinishText  
 設定完成 5d; 命令按鈕的文字。  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 指向要顯示在 [完成] 5d; 命令按鈕的文字。  
  
### <a name="remarks"></a>備註  
 呼叫`SetFinishText`︰ 將文字顯示在 完成 5d; 命令按鈕，並隱藏使用者完成精靈的最後一頁動作之後的下一步 和 上一步 按鈕。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>CPropertySheet::SetTitle  
 指定屬性工作表的標題 （框架視窗的標題列中顯示的文字）。  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>參數  
 `nStyle`  
 指定的屬性工作表標題的樣式。 必須指定樣式，0 或**PSH_PROPTITLE**。 如果樣式設定為**PSH_PROPTITLE**，指定為標題的文字後面出現的文字 「 屬性 」。 例如，呼叫`SetTitle`(「 簡單 」 **PSH_PROPTITLE**) 會在屬性工作表標題的 「 簡單屬性 」。  
  
 `lpszText`  
 指向要做為屬性工作表的標題列中的標題文字。  
  
### <a name="remarks"></a>備註  
 根據預設，屬性工作表會使用屬性工作表的建構函式中 caption 參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons  
 啟用或停用精靈屬性工作表中的 [上一步]、 [下一步] 或 [完成] 按鈕。  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 一組自訂精靈按鈕的外觀與函式的旗標。 這個參數可以是下列值的組合︰  
  
- **PSWIZB_BACK**上一頁按鈕  
  
- **PSWIZB_NEXT**下一步按鈕  
  
- **PSWIZB_FINISH**完成 按鈕  
  
- **PSWIZB_DISABLEDFINISH**已停用 [完成] 按鈕  
  
### <a name="remarks"></a>備註  
 呼叫`SetWizardButtons`只對話方塊開啟之後, 您不能呼叫`SetWizardButtons`之前先呼叫[DoModal](#domodal)。 一般而言，您應該呼叫`SetWizardButtons`從[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。  
  
 如果您想要變更 [完成] 按鈕的文字或隱藏 [下一步] 及 [上一步] 按鈕一次使用者已完成精靈中，呼叫[SetFinishText](#setfinishtext)。 請注意，相同的按鈕共用完成和下一步。 您可以顯示 [完成] 5d; 或 [下一步] 按鈕一次，但非兩者。  
  
### <a name="example"></a>範例  
 A`CPropertySheet`具有三個精靈屬性頁︰ `CStylePage`， `CColorPage`，和`CShapePage`。  下列程式碼片段示範如何啟用和停用**回**和**下一步**在精靈的 屬性頁上的按鈕。  
  
 [!code-cpp[NVC_MFCDocView # 140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView # 138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>Cpropertysheet:: Domodal  
 為精靈中建立屬性頁。  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>備註  
 精靈屬性頁的主要特性是使用者瀏覽 下一步使用或完成、 備份，並 取消 按鈕，而不是索引標籤。  
  
 呼叫`SetWizardMode`之前先呼叫[DoModal](#domodal)。 在您呼叫後`SetWizardMode`，`DoModal`會傳回**ID_WIZFINISH** （如果使用者關閉與 [完成] 按鈕） 或**IDCANCEL**。  
  
 `SetWizardMode`設定 PSH_WIZARD 旗標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView # 142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 範例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




