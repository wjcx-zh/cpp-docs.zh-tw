---
title: CMFCPropertySheet 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: 1168375606ef86061269454aa361a076efa331a4
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176402"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet 類別

`CMFCPropertySheet` 類別支援屬性工作表，其中每個屬性頁是由頁面索引標籤、工具列按鈕、樹狀目錄控制項節點或清單項目所表示。

## <a name="syntax"></a>語法

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|建構 `CMFCPropertySheet` 物件。|
|`CMFCPropertySheet::~CMFCPropertySheet`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[Cmfcpropertysheet:: Addpage](#addpage)|將頁面新增至屬性工作表。|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|將新的屬性頁新增至樹狀目錄控制項。|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|將新的節點新增至樹狀目錄控制項。|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|在每個頁面頂端保留空間以繪製自訂標頭。|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|擷取目前標頭的高度。|
|[CMFCPropertySheet::GetLook](#getlook)|擷取指定目前屬性工作表外觀的列舉值。|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|重試巡覽列的寬度，以像素為單位。|
|[CMFCPropertySheet::GetTab](#gettab)|擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。|
|`CMFCPropertySheet::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化目前屬性工作表控制項的外觀。|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|啟用屬性頁時由架構呼叫。|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由架構呼叫以繪製自訂屬性頁標頭。|
|`CMFCPropertySheet::OnInitDialog`|會處理[WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog)訊息。 (覆寫[cpropertysheet:: Oninitdialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由架構呼叫以從樹狀目錄控制項移除屬性頁。|
|`CMFCPropertySheet::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 `CPropertySheet::PreTranslateMessage`。)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|從樹狀目錄控制項移除節點。|
|[CMFCPropertySheet::RemovePage](#removepage)|從屬性工作表中移除屬性頁。|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定在 Outlook 窗格之導覽控制項中使用的映像清單。|
|[Cmfcpropertysheet:: Setlook](#setlook)|指定屬性工作表的外觀。|

## <a name="remarks"></a>備註

`CMFCPropertySheet` 類別表示屬性工作表，也稱為索引標籤對話方塊。 `CMFCPropertySheet` 類別能以各種方式顯示屬性頁。

請執行下列步驟，在應用程式中使用 `CMFCPropertySheet` 類別。

1. 自 `CMFCPropertySheet` 類別衍生類別並加以命名，例如，CMyPropertySheet。

1. 建構[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)每個屬性頁的物件。

1. 呼叫[cmfcpropertysheet:: Setlook](#setlook) CMyPropertySheet 建構函式中的方法。 該方法的參數會指定屬性頁應該要顯示為沿著屬性工作表頂端或左邊的索引標籤；Microsoft OneNote 屬性工作表樣式的索引標籤；在 Microsoft Outlook 工具列控制項上的按鈕；在樹狀目錄控制項上的節點；或在屬性工作表左邊的項目清單。

1. 如果您在 Microsoft Outlook 工具列的樣式建立屬性工作表，呼叫[CMFCPropertySheet::SetIconsList](#seticonslist)方法來建立影像清單與屬性頁的關聯。

1. 呼叫[cmfcpropertysheet:: Addpage](#addpage)每個屬性頁的方法。

1. 建立 `CMFCPropertySheet` 控制項，並呼叫其 `DoModal` 方法。

## <a name="illustrations"></a>插圖

下圖描述其樣式為內嵌 Microsoft Outlook 工具列的屬性工作表。 Outlook 工具列會出現在屬性工作表的左邊。

![CMFCPropertySheet 色彩控制項](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet 色彩控制項")

下圖顯示包含的屬性工作表[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)物件。 該物件是樣式為標準通用控制項屬性頁的屬性工作表。

![CMFCPropertySheet 清單和屬性控制項](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet 清單和屬性控制項")

下圖描述其樣式為樹狀目錄控制項的屬性工作表。

![屬性樹狀](../../mfc/reference/media/proptree.png "屬性樹狀結構")

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertysheet.h

##  <a name="addpage"></a>  Cmfcpropertysheet:: Addpage

將頁面新增至屬性工作表。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[in]Page 物件的指標。 這個參數不能是 NULL。

### <a name="remarks"></a>備註

這個方法會將指定的屬性頁面與屬性工作表中最右邊的索引標籤。 因此，使用這個方法來新增的網頁中左到右的順序。

如果屬性工作表是在 Microsoft outlook 樣式，架構就會顯示一份瀏覽按鈕左邊的屬性工作表。 這個方法會加入屬性頁之後，它會將對應的按鈕加入至清單中。 若要顯示的屬性頁，請按一下其對應的按鈕。 如需有關樣式的屬性工作表，請參閱[cmfcpropertysheet:: Setlook](#setlook)。

##  <a name="addpagetotree"></a>  CMFCPropertySheet::AddPageToTree

將新的屬性頁新增至樹狀目錄控制項。

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>參數

*pCategory*<br/>
[in]父樹狀節點或指定的頁面相關聯的最上層節點的 NULL 指標。 呼叫[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法，以取得此指標。

*pPage*<br/>
[in]屬性頁物件的指標。

*nIconNum*<br/>
[in]圖示或如果沒有使用-1 的以零為起始的索引。 如果未選取頁面樹狀結構的控制項屬性頁旁邊顯示圖示。 預設值為 -1。

*nSelIconNum*<br/>
[in]圖示或如果沒有使用-1 的以零為起始的索引。 樹狀結構的控制項屬性頁旁邊顯示圖示，選取頁面時。 預設值為 -1。

### <a name="remarks"></a>備註

這個方法會將屬性頁面為分葉節點的樹狀目錄控制項。 若要新增的屬性頁，建立`CMFCPropertySheet`物件，請呼叫[cmfcpropertysheet:: Setlook](#setlook)方法*尋找*參數設為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用此方法加入屬性頁.

##  <a name="addtreecategory"></a>  CMFCPropertySheet::AddTreeCategory

將新的節點新增至樹狀目錄控制項。

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
[in]節點的名稱。

*nIconNum*<br/>
[in]圖示或如果沒有使用-1 的以零為起始的索引。 如果未選取頁面樹狀結構的控制項屬性頁旁邊顯示圖示。 預設值為 -1。

*nSelectedIconNum*<br/>
[in]圖示或如果沒有使用-1 的以零為起始的索引。 樹狀結構的控制項屬性頁旁邊顯示圖示，選取頁面時。 預設值為 -1。

*pParentCategory*<br/>
[in]父樹狀節點或指定的頁面相關聯的最上層節點的 NULL 指標。 設定此參數與[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法。

### <a name="return-value"></a>傳回值

新的節點樹狀控制項中的指標。

### <a name="remarks"></a>備註

若要將新的節點，也稱為類別，新增至樹狀結構控制項中使用這個方法。 若要新增節點，建立`CMFCPropertySheet`物件，請呼叫[cmfcpropertysheet:: Setlook](#setlook)方法*尋找*參數設為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用這個方法，將節點加入。

在後續呼叫中使用這個方法的傳回值[CMFCPropertySheet::AddPageToTree](#addpagetotree)並[CMFCPropertySheet::AddTreeCategory](#addtreecategory)。

##  <a name="cmfcpropertysheet"></a>  CMFCPropertySheet::CMFCPropertySheet

建構 `CMFCPropertySheet` 物件。

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>參數

*pszCaption*<br/>
[in]字串，包含屬性工作表的標題。 不可以是 NULL。

*nIDCaption*<br/>
[in]資源識別碼，其中包含的屬性工作表的標題。

*pParentWnd*<br/>
[in]屬性工作表，則為 NULL，如果父視窗是應用程式的主視窗的父視窗指標。 預設值是 NULL。

*iSelectPage*<br/>
[in]最上層的屬性頁的以零為起始的索引。 預設值為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱的參數[CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)建構函式。

##  <a name="enablepageheader"></a>  CMFCPropertySheet::EnablePageHeader

在每個頁面頂端保留空間以繪製自訂標頭。

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>參數

*nHeaderHeight*<br/>
[in]標頭，單位為像素的高度。

### <a name="remarks"></a>備註

若要使用的值*nHeaderHeight*參數，以繪製自訂標頭，覆寫[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)方法。

##  <a name="getheaderheight"></a>  CMFCPropertySheet::GetHeaderHeight

擷取目前標頭的高度。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>傳回值

標頭，單位為像素的高度。

### <a name="remarks"></a>備註

呼叫[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前呼叫這個方法。

##  <a name="getlook"></a>  CMFCPropertySheet::GetLook

擷取指定目前屬性工作表外觀的列舉值。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>傳回值

其中一個列舉值，指定屬性工作表的外觀。 如需可能值的清單，請參閱列舉資料表中的 < 備註 > 一節[cmfcpropertysheet:: Setlook](#setlook)。

##  <a name="getnavbarwidth"></a>  CMFCPropertySheet::GetNavBarWidth

取得導覽列的寬度。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>傳回值

導覽列的寬度，以像素為單位。

##  <a name="gettab"></a>  CMFCPropertySheet::GetTab

擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>傳回值

內部索引標籤控制項物件。

### <a name="remarks"></a>備註

您可以設定的屬性工作表，使其出現在不同的樣式，例如樹狀結構控制項中，瀏覽按鈕或一組索引標籤式頁面的清單。

呼叫這個方法之前，先呼叫[cmfcpropertysheet:: Setlook](#setlook)方法來設定屬性工作表控制項的外觀。 然後呼叫[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)方法來初始化內部 索引標籤控制項物件。 使用此方法來擷取索引標籤控制項物件，然後使用該物件使用屬性工作表上的索引標籤。

如果屬性工作表控制項才會出現在 Microsoft onenote 樣式未設定此方法會判斷提示以偵錯模式。

##  <a name="initnavigationcontrol"></a>  CMFCPropertySheet::InitNavigationControl

初始化目前屬性工作表控制項的外觀。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>傳回值

屬性工作表控制項的視窗的指標。

### <a name="remarks"></a>備註

屬性工作表控制項可以出現在數種不同格式的詳細資訊，例如一組索引標籤式的頁面、 樹狀目錄控制項或瀏覽按鈕的清單。 使用[cmfcpropertysheet:: Setlook](#setlook)方法，以指定的屬性工作表控制項的外觀。

##  <a name="onactivatepage"></a>  CMFCPropertySheet::OnActivatePage

啟用屬性頁時由架構呼叫。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[in]表示已啟用的屬性頁的屬性頁面物件的指標。

### <a name="remarks"></a>備註

根據預設，此方法可確保已啟用的屬性頁面上，捲動到檢視。 如果目前的屬性工作表的樣式會包含 Microsoft Outlook 窗格，則這個方法會設定對應的 Outlook 按鈕已核取狀態。

##  <a name="ondrawpageheader"></a>  CMFCPropertySheet::OnDrawPageHeader

由架構呼叫以繪製自訂屬性頁的標頭。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*n 版面*<br/>
[in]以零為起始的屬性頁面的頁碼。

*rectHeader*<br/>
[in]指定要繪製的標頭位置的周框。

### <a name="remarks"></a>備註

根據預設，這個方法沒有任何作用。 如果您覆寫這個方法，呼叫[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前，架構會呼叫這個方法。

##  <a name="onremovetreepage"></a>  CMFCPropertySheet::OnRemoveTreePage

由架構呼叫以從樹狀目錄控制項移除屬性頁。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[in]表示要移除的屬性頁面的屬性頁面物件的指標。

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

##  <a name="removecategory"></a>  CMFCPropertySheet::RemoveCategory

從樹狀目錄控制項移除節點。

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>參數

*pCategory*<br/>
[in]若要移除的類別目錄 （節點） 的指標。

### <a name="remarks"></a>備註

若要移除的節點，也就是一種類別，從樹狀目錄控制項使用這個方法。 使用[CMFCPropertySheet::AddTreeCategory](#addtreecategory)將節點加入至樹狀目錄控制項的方法。

##  <a name="removepage"></a>  CMFCPropertySheet::RemovePage

從屬性工作表中移除屬性頁。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[in]屬性頁面物件，表示要移除的屬性頁面的指標。 不可以是 NULL。

*n 版面*<br/>
[in]要移除之頁面的以零為起始索引。

### <a name="remarks"></a>備註

這個方法中移除指定的屬性頁面，並終結其相關聯的視窗。 物件的屬性頁*pPage*參數指定不會終結之前[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)視窗已關閉。

##  <a name="seticonslist"></a>  CMFCPropertySheet::SetIconsList

指定在 Outlook 窗格之導覽控制項中使用的映像清單。

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>參數

*uiImageListResID*<br/>
[in]影像清單的資源識別碼。

*cx*<br/>
[in]寬度，單位為像素的影像清單中的圖示。

*clrTransparent*<br/>
[in]透明影像色彩。 這個色彩影像部分會是透明的。 洋紅色，RGB(255,0,255) 為預設值。

*hIcons*<br/>
[in]現有的影像清單控制代碼。

### <a name="return-value"></a>傳回值

第一種方法多載的語法，為 true，則這個方法會成功; 如果否則為 FALSE。

### <a name="remarks"></a>備註

如果屬性工作表是在 Microsoft outlook 樣式，架構會顯示一份瀏覽按鈕，稱為 Outlook 窗格控制項左邊的屬性工作表。 這個方法可用於設定要供 Outlook 窗格控制項之影像清單。

如需有關支援這個方法的方法的詳細資訊，請參閱[CImageList::Create](../../mfc/reference/cimagelist-class.md#create)並[CImageList::Add](../../mfc/reference/cimagelist-class.md#add)。 如需如何將屬性工作表的樣式設定的詳細資訊，請參閱[cmfcpropertysheet:: Setlook](#setlook)。

##  <a name="setlook"></a>  Cmfcpropertysheet:: Setlook

指定屬性工作表的外觀。

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>參數

*尋找*<br/>
[in]其中一個列舉值，指定屬性工作表的外觀。 屬性工作表的預設樣式為`CMFCPropertySheet::PropSheetLook_Tabs`。 如需詳細資訊，請參閱本主題的 < 備註 > 一節的表格。

*nNavControlWidth*<br/>
[in]瀏覽控制項，單位為像素的寬度。 預設值為 100。

### <a name="remarks"></a>備註

若要顯示非預設的樣式屬性工作表，請建立屬性工作表視窗之前呼叫這個方法。

下表列出列舉值，可以指定於*看起來*參數。

|值|描述|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|（預設值）顯示每個屬性頁 索引標籤。 索引標籤會顯示在屬性工作表的頂部，會發生堆疊，如果有多個索引標籤中的單一資料列無法全部。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在樣式中的 Microsoft Outlook 功能區，在屬性工作表的左邊顯示導覽按鈕的清單。 在清單中的每個按鈕對應至屬性頁。 如果有多個按鈕的可見區域的清單中無法全部，架構就會顯示捲軸箭號。|
|`CMFCPropertySheet::PropSheetLook_Tree`|顯示屬性工作表左邊的樹狀目錄控制項。 每個父或子節點的樹狀結構控制項中對應的屬性頁。 如果有多個節點的樹狀目錄控制項的可見區域中無法全部，架構就會顯示捲軸箭號。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|顯示索引標籤上，每個屬性頁的 Microsoft OneNote 樣式。 架構會顯示在屬性工作表頂端的索引標籤，並捲動箭號，如果有多個索引標籤，比將放入單一資料列。|
|`CMFCPropertySheet::PropSheetLook_List`|顯示屬性工作表左邊的清單。 每個清單項目會對應至屬性頁。 如果有多個清單項目清單的可見區域中無法全部，架構就會顯示捲軸箭號。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage 類別](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
