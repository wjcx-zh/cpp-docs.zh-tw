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
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69505065"
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
|[CMFCPropertySheet::AddPage](#addpage)|將頁面新增至屬性工作表。|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|將新的屬性頁新增至樹狀目錄控制項。|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|將新的節點新增至樹狀目錄控制項。|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|在每個頁面頂端保留空間以繪製自訂標頭。|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|擷取目前標頭的高度。|
|[CMFCPropertySheet::GetLook](#getlook)|擷取指定目前屬性工作表外觀的列舉值。|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|重試巡覽列的寬度，以像素為單位。|
|[CMFCPropertySheet::GetTab](#gettab)|擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。|
|`CMFCPropertySheet::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化目前屬性工作表控制項的外觀。|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|啟用屬性頁時由架構呼叫。|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由架構呼叫以繪製自訂屬性頁標頭。|
|`CMFCPropertySheet::OnInitDialog`|處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)訊息。 （覆寫[CPropertySheet：： OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。）|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由架構呼叫以從樹狀目錄控制項移除屬性頁。|
|`CMFCPropertySheet::PreTranslateMessage`|會先轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 `CPropertySheet::PreTranslateMessage`。)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|從樹狀目錄控制項移除節點。|
|[CMFCPropertySheet::RemovePage](#removepage)|從屬性工作表中移除屬性頁。|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定在 Outlook 窗格之導覽控制項中使用的映像清單。|
|[CMFCPropertySheet::SetLook](#setlook)|指定屬性工作表的外觀。|

## <a name="remarks"></a>備註

`CMFCPropertySheet` 類別表示屬性工作表，也稱為索引標籤對話方塊。 `CMFCPropertySheet` 類別能以各種方式顯示屬性頁。

請執行下列步驟，在應用程式中使用 `CMFCPropertySheet` 類別。

1. 自 `CMFCPropertySheet` 類別衍生類別並加以命名，例如，CMyPropertySheet。

1. 為每個屬性頁建立[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)物件。

1. 在 CMyPropertySheet 的函式中呼叫[CMFCPropertySheet：： SetLook](#setlook)方法。 該方法的參數會指定屬性頁應該要顯示為沿著屬性工作表頂端或左邊的索引標籤；Microsoft OneNote 屬性工作表樣式的索引標籤；在 Microsoft Outlook 工具列控制項上的按鈕；在樹狀目錄控制項上的節點；或在屬性工作表左邊的項目清單。

1. 如果您使用 Microsoft Outlook 工具列的樣式建立屬性工作表，請呼叫[CMFCPropertySheet：： SetIconsList](#seticonslist)方法，將影像清單與屬性頁產生關聯。

1. 針對每個屬性頁呼叫[CMFCPropertySheet：： AddPage](#addpage)方法。

1. 建立 `CMFCPropertySheet` 控制項，並呼叫其 `DoModal` 方法。

## <a name="illustrations"></a>插圖

下圖描述其樣式為內嵌 Microsoft Outlook 工具列的屬性工作表。 Outlook 工具列會出現在屬性工作表的左邊。

![CMFCPropertySheet 色彩控制項](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet 色彩控制項")

下圖描述包含[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)物件的屬性工作表。 該物件是樣式為標準通用控制項屬性頁的屬性工作表。

![CMFCPropertySheet 清單和屬性控制項](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet 清單和屬性控制項")

下圖描述其樣式為樹狀目錄控制項的屬性工作表。

![屬性樹狀結構](../../mfc/reference/media/proptree.png "屬性樹狀結構")

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertysheet。h

##  <a name="addpage"></a>CMFCPropertySheet：： AddPage

將頁面新增至屬性工作表。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
在頁面物件的指標。 此參數不可以是 NULL。

### <a name="remarks"></a>備註

這個方法會將指定的屬性頁加入至屬性工作表中最右邊的索引標籤。 因此，請使用這個方法，以由左至右的順序來新增頁面。

如果屬性工作表是以 Microsoft Outlook 為樣式，則架構會在屬性工作表的左邊顯示導覽按鈕清單。 在這個方法加入屬性頁之後，它會將對應的按鈕加入清單中。 若要顯示內容頁，請按一下其對應的按鈕。 如需屬性工作表樣式的詳細資訊，請參閱[CMFCPropertySheet：： SetLook](#setlook)。

##  <a name="addpagetotree"></a>CMFCPropertySheet：： AddPageToTree

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
在父樹狀節點的指標，或 Null 會將指定的頁面與最上層節點產生關聯。 呼叫[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法以取得此指標。

*pPage*<br/>
在屬性頁物件的指標。

*nIconNum*<br/>
在圖示以零為基底的索引，如果沒有使用圖示，則為-1。 未選取頁面時，圖示會顯示在 [樹狀目錄控制項] 屬性頁的旁邊。 預設值為 -1。

*nSelIconNum*<br/>
在圖示以零為基底的索引，如果沒有使用圖示，則為-1。 選取頁面時，圖示會顯示在 [樹狀目錄控制項] 屬性頁的旁邊。 預設值為 -1。

### <a name="remarks"></a>備註

這個方法會加入屬性頁作為樹狀目錄控制項的分葉。 若要加入屬性頁，請建立`CMFCPropertySheet`物件，呼叫[CMFCPropertySheet：： SetLook](#setlook)方法，並將*外觀*參數設為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用這個方法來加入屬性頁。

##  <a name="addtreecategory"></a>CMFCPropertySheet：： AddTreeCategory

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
在節點的名稱。

*nIconNum*<br/>
在圖示以零為基底的索引，如果沒有使用圖示，則為-1。 未選取頁面時，圖示會顯示在 [樹狀目錄控制項] 屬性頁的旁邊。 預設值為 -1。

*nSelectedIconNum*<br/>
在圖示以零為基底的索引，如果沒有使用圖示，則為-1。 選取頁面時，圖示會顯示在 [樹狀目錄控制項] 屬性頁的旁邊。 預設值為 -1。

*pParentCategory*<br/>
在父樹狀節點的指標，或 Null 會將指定的頁面與最上層節點產生關聯。 請使用[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法來設定此參數。

### <a name="return-value"></a>傳回值

樹狀目錄控制項中新節點的指標。

### <a name="remarks"></a>備註

使用此方法，將新的節點（也稱為分類）新增至樹狀目錄控制項。 若要加入節點，請建立`CMFCPropertySheet`物件，呼叫[CMFCPropertySheet：： SetLook](#setlook)方法，並將*外觀*參數設為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用這個方法來加入節點。

在後續呼叫[CMFCPropertySheet：： AddPageToTree](#addpagetotree)和[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)時，使用此方法的傳回值。

##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet：： CMFCPropertySheet

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
在包含屬性工作表標題的字串。 不可以是 NULL。

*nIDCaption*<br/>
在包含屬性工作表標題的資源識別碼。

*pParentWnd*<br/>
在屬性工作表之父視窗的指標，如果父視窗是應用程式的主視窗，則為 Null。 預設值為 Null。

*iSelectPage*<br/>
在最上層屬性頁之以零為起始的索引。 預設值為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[CPropertySheet：： CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)函數的參數。

##  <a name="enablepageheader"></a>CMFCPropertySheet：： EnablePageHeader

在每個頁面頂端保留空間以繪製自訂標頭。

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>參數

*nHeaderHeight*<br/>
在標頭的高度（以圖元為單位）。

### <a name="remarks"></a>備註

若要使用*nHeaderHeight*參數的值來繪製自訂標頭，請覆寫[CMFCPropertySheet：： OnDrawPageHeader](#ondrawpageheader)方法。

##  <a name="getheaderheight"></a>CMFCPropertySheet：： GetHeaderHeight

擷取目前標頭的高度。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>傳回值

標頭的高度（以圖元為單位）。

### <a name="remarks"></a>備註

呼叫[CMFCPropertySheet：： EnablePageHeader](#enablepageheader)方法之前，請先呼叫這個方法。

##  <a name="getlook"></a>CMFCPropertySheet：： GetLook

擷取指定目前屬性工作表外觀的列舉值。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>傳回值

其中一個列舉值，指定屬性工作表的外觀。 如需可能值的清單，請參閱[CMFCPropertySheet：： SetLook](#setlook)的「備註」一節中的列舉表。

##  <a name="getnavbarwidth"></a>CMFCPropertySheet：： GetNavBarWidth

取得導覽列的寬度。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>傳回值

導覽列的寬度，以像素為單位。

##  <a name="gettab"></a>CMFCPropertySheet：： GetTab

擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>傳回值

內部的索引標籤控制項物件。

### <a name="remarks"></a>備註

您可以設定屬性工作表，使其以不同的樣式顯示，例如樹狀目錄控制項、導覽按鈕清單，或一組索引標籤式頁面。

在您呼叫這個方法之前，請先呼叫[CMFCPropertySheet：： SetLook](#setlook)方法，以設定屬性工作表控制項的外觀。 然後呼叫[CMFCPropertySheet：： InitNavigationControl](#initnavigationcontrol)方法，以初始化內部索引標籤控制項物件。 使用這個方法來抓取索引標籤控制項物件，然後使用該物件來處理屬性工作表上的索引標籤。

如果屬性工作表控制項未設定成以 Microsoft OneNote 的樣式顯示，這個方法就會在 [debug] 模式中判斷提示。

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet：： InitNavigationControl

初始化目前屬性工作表控制項的外觀。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>傳回值

屬性工作表控制項之視窗的指標。

### <a name="remarks"></a>備註

屬性工作表控制項可能會以數種不同的形式出現，例如一組索引標籤式頁面、樹狀目錄控制項或導覽按鈕清單。 使用[CMFCPropertySheet：： SetLook](#setlook)方法來指定屬性工作表控制項的外觀。

##  <a name="onactivatepage"></a>CMFCPropertySheet：： OnActivatePage

啟用屬性頁時由架構呼叫。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
在屬性頁物件的指標，表示已啟用的屬性頁。

### <a name="remarks"></a>備註

根據預設，這個方法會確保 [已啟用] 屬性頁會滾動至 [視圖]。 如果目前屬性工作表的樣式包含 Microsoft Outlook 窗格，這個方法會將對應的 Outlook 按鈕設定為已核取狀態。

##  <a name="ondrawpageheader"></a>CMFCPropertySheet：： OnDrawPageHeader

由架構呼叫以繪製自訂屬性頁的標頭。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*nPage*<br/>
在以零為基底的屬性頁號。

*rectHeader*<br/>
在周框，指定要在何處繪製標頭。

### <a name="remarks"></a>備註

根據預設，這個方法不會執行任何操作。 如果您覆寫這個方法，請呼叫[CMFCPropertySheet：： EnablePageHeader](#enablepageheader)方法，然後架構才會呼叫這個方法。

##  <a name="onremovetreepage"></a>CMFCPropertySheet：： OnRemoveTreePage

由架構呼叫以從樹狀目錄控制項移除屬性頁。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
在屬性頁物件的指標，代表要移除的屬性頁。

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

##  <a name="removecategory"></a>CMFCPropertySheet：： RemoveCategory

從樹狀目錄控制項移除節點。

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>參數

*pCategory*<br/>
在要移除之類別目錄（節點）的指標。

### <a name="remarks"></a>備註

使用此方法可從樹狀目錄控制項移除節點（也稱為分類）。 使用[CMFCPropertySheet：： AddTreeCategory](#addtreecategory)方法，將節點加入至樹狀目錄控制項。

##  <a name="removepage"></a>CMFCPropertySheet：： RemovePage

從屬性工作表中移除屬性頁。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
在屬性頁物件的指標，代表要移除的屬性頁。 不可以是 NULL。

*nPage*<br/>
在要移除的頁面之以零為起始的索引。

### <a name="remarks"></a>備註

這個方法會移除指定的屬性頁，並終結其相關聯的視窗。 *PPage*參數指定的屬性頁物件在[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)視窗關閉之前不會終結。

##  <a name="seticonslist"></a>CMFCPropertySheet：： SetIconsList

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
在影像清單的資源識別碼。

*cx*<br/>
在影像清單中圖示的寬度（以圖元為單位）。

*clrTransparent*<br/>
在透明影像色彩。 屬於此色彩的影像部分會是透明的。 預設值為 [洋紅色]、[RGB （255，0255）] 色彩。

*hIcons*<br/>
在現有影像清單的控制碼。

### <a name="return-value"></a>傳回值

在第一個方法多載語法中，如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果內容工作表使用 Microsoft Outlook 的樣式，則架構會在屬性工作表的左邊顯示一個導覽按鈕清單，稱為 Outlook 窗格控制項。 使用此方法可設定 [Outlook 窗格] 控制項所要使用的影像清單。

如需支援此方法之方法的詳細資訊，請參閱[CImageList：： Create](../../mfc/reference/cimagelist-class.md#create)和[CImageList：： Add](../../mfc/reference/cimagelist-class.md#add)。 如需如何設定屬性工作表樣式的詳細資訊，請參閱[CMFCPropertySheet：： SetLook](#setlook)。

##  <a name="setlook"></a>CMFCPropertySheet：： SetLook

指定屬性工作表的外觀。

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>參數

*look*<br/>
在其中一個列舉值，指定屬性工作表的外觀。 屬性工作表的預設樣式為`CMFCPropertySheet::PropSheetLook_Tabs`。 如需詳細資訊，請參閱本主題的「備註」一節中的表格。

*nNavControlWidth*<br/>
在導覽控制項的寬度（以圖元為單位）。 預設值為 100。

### <a name="remarks"></a>備註

若要以預設值以外的樣式顯示內容表，請在建立屬性工作表視窗之前呼叫這個方法。

下表列出可在 [*外觀*] 參數中指定的列舉值。

|值|描述|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|預設顯示每個屬性頁的索引標籤。 索引標籤會顯示在屬性工作表的頂端，而且如果索引標籤超過單一資料列容納的數目，則會堆疊。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在屬性工作表的左側，以 Microsoft Outlook 工具列的樣式顯示導覽按鈕清單。 清單中的每個按鈕都會對應至一個屬性頁。 如果按鈕數目超過清單的可見區域中的大小，則架構會顯示捲軸箭號。|
|`CMFCPropertySheet::PropSheetLook_Tree`|在屬性工作表的左邊顯示樹狀目錄控制項。 樹狀目錄控制項的每個父節點或子節點都會對應至一個屬性頁。 如果節點數目超過樹狀結構控制項的可見區域，此架構會顯示捲軸箭號。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|顯示每個屬性頁的索引標籤（以 Microsoft OneNote 的樣式表示）。 此架構會在屬性工作表的頂端顯示索引標籤，如果有超過單一資料列容納的索引標籤，則會捲動箭號。|
|`CMFCPropertySheet::PropSheetLook_List`|在屬性工作表的左邊顯示清單。 每個清單專案都會對應到一個屬性頁。 如果清單專案比清單的可見區域還多，則此架構會顯示捲軸箭號。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage 類別](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
