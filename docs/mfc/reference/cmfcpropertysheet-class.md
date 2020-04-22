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
ms.openlocfilehash: 9b1bb2ce9a957b9cd9f7add983b4da7a228d7a1d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750067"
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
|`CMFCPropertySheet::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化目前屬性工作表控制項的外觀。|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|啟用屬性頁時由架構呼叫。|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由架構呼叫以繪製自訂屬性頁標頭。|
|`CMFCPropertySheet::OnInitDialog`|處理[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)消息。 (覆寫[C 屬性表:oninitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由架構呼叫以從樹狀目錄控制項移除屬性頁。|
|`CMFCPropertySheet::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 (覆寫 `CPropertySheet::PreTranslateMessage`。)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|從樹狀目錄控制項移除節點。|
|[CMFCPropertySheet::RemovePage](#removepage)|從屬性工作表中移除屬性頁。|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定在 Outlook 窗格之導覽控制項中使用的映像清單。|
|[CMFCPropertySheet::SetLook](#setlook)|指定屬性工作表的外觀。|

## <a name="remarks"></a>備註

`CMFCPropertySheet` 類別表示屬性工作表，也稱為索引標籤對話方塊。 `CMFCPropertySheet` 類別能以各種方式顯示屬性頁。

請執行下列步驟，在應用程式中使用 `CMFCPropertySheet` 類別。

1. 自 `CMFCPropertySheet` 類別衍生類別並加以命名，例如，CMyPropertySheet。

1. 為每個屬性頁構造一個[CMFC 屬性頁](../../mfc/reference/cmfcpropertypage-class.md)物件。

1. 調用[CMFC 屬性表::](#setlook)在 CMyPropertySheet 構造函數中設置查找方法。 該方法的參數會指定屬性頁應該要顯示為沿著屬性工作表頂端或左邊的索引標籤；Microsoft OneNote 屬性工作表樣式的索引標籤；在 Microsoft Outlook 工具列控制項上的按鈕；在樹狀目錄控制項上的節點；或在屬性工作表左邊的項目清單。

1. 如果在 Microsoft Outlook 工具列的樣式中創建屬性表,請調用[CMFC 屬性表:setIconsList](#seticonslist)方法將圖像列表與屬性頁相關聯。

1. 呼叫[CMFC 屬性表::](#addpage)為每個屬性頁添加頁方法。

1. 建立 `CMFCPropertySheet` 控制項，並呼叫其 `DoModal` 方法。

## <a name="illustrations"></a>插圖

下圖描述其樣式為內嵌 Microsoft Outlook 工具列的屬性工作表。 Outlook 工具列會出現在屬性工作表的左邊。

![CMFCPropertySheet 色彩控制項](../../mfc/reference/media/cmfcpropertysheet_color.png "CMFCPropertySheet 色彩控制項")

下圖描述了包含[CMFCPropertyGridCtrl 類](../../mfc/reference/cmfcpropertygridctrl-class.md)物件的屬性表。 該物件是樣式為標準通用控制項屬性頁的屬性工作表。

![CMFCPropertySheet 清單和屬性控制項](../../mfc/reference/media/cmfcpropertysheet_list.png "CMFCPropertySheet 清單和屬性控制項")

下圖描述其樣式為樹狀目錄控制項的屬性工作表。

![屬性樹](../../mfc/reference/media/proptree.png "屬性樹")

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>需求

**標題:** afx屬性表.h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a>CMFC 屬性表:新增頁

將頁面新增至屬性工作表。

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[在]指向頁面物件的指標。 此參數不可以是 NULL。

### <a name="remarks"></a>備註

此方法將指定的屬性頁添加為屬性表中最右側的選項卡。 因此,使用此方法按從左到右的順序添加頁面。

如果屬性表以 Microsoft Outlook 樣式顯示,則框架將在屬性表的左側顯示導航按鈕的清單。 此方法添加屬性頁後,它將相應的按鈕添加到清單中。 要顯示屬性頁,請按兩下其相應的按鈕。 有關屬性表樣式的詳細資訊,請參閱[CMFC 屬性表:::SetLook](#setlook)。

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a>CMFC 屬性表::新增頁面到樹

將新的屬性頁新增至樹狀目錄控制項。

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>參數

*p 類別*<br/>
[在]指向父樹節點的指標,或 NULL 將指定的頁面與頂級節點相關聯。 調用[CMFC 屬性表:addTree 類別](#addtreecategory)方法以獲取此指標。

*pPage*<br/>
[在]指向屬性頁物件的指標。

*nIconNum*<br/>
[在]圖示的零索引,如果未使用圖示,則為 -1。 未選擇該頁時,該圖示將顯示在樹控件屬性頁旁邊。 預設值為 -1。

*恩塞爾克尼納姆*<br/>
[在]圖示的零索引,如果未使用圖示,則為 -1。 選擇頁面時,該圖示將顯示在樹控件屬性頁旁邊。 預設值為 -1。

### <a name="remarks"></a>備註

此方法將屬性頁添加為樹控件的葉。 要添加屬性頁,請建立一`CMFCPropertySheet`個物件,請調用[CMFC屬性表::SetLook](#setlook)方法,*外觀參數設置為*`CMFCPropertySheet::PropSheetLook_Tree`,然後使用此方法添加屬性頁。

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a>CMFC 屬性表::添加樹類別

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
[在]節點的名稱。

*nIconNum*<br/>
[在]圖示的零索引,如果未使用圖示,則為 -1。 未選擇該頁時,該圖示將顯示在樹控件屬性頁旁邊。 預設值為 -1。

*N 選擇圖示*<br/>
[在]圖示的零索引,如果未使用圖示,則為 -1。 選擇頁面時,該圖示將顯示在樹控件屬性頁旁邊。 預設值為 -1。

*p 父項目*<br/>
[在]指向父樹節點的指標,或 NULL 將指定的頁面與頂級節點相關聯。 使用[CMFC 屬性表設定此參數:addTree 類別](#addtreecategory)方法。

### <a name="return-value"></a>傳回值

指向樹控件中的新節點的指標。

### <a name="remarks"></a>備註

使用此方法向樹控件添加新節點(也稱為類別)。 要添加節點,請建立一`CMFCPropertySheet`個物件,請調用[CMFC 屬性表::SetLook](#setlook)方法,*外觀參數設置為*`CMFCPropertySheet::PropSheetLook_Tree`,然後使用此方法添加節點。

在後續呼叫 CMFC 屬性表時使用此方法的傳回值[::AddPageTotree](#addpagetotree)和[CMFC 屬性表::添加樹類別](#addtreecategory)。

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a>CMFC財產表:CMFC財產表

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
[在]包含屬性工作表標題的字串。 不能是 NULL。

*nIDCaption*<br/>
[在]包含屬性表標題的資源識別碼。

*pparentwnd*<br/>
[在]指標指向屬性表的父視窗,如果父視窗是應用程式的主視窗,則指向 NULL。 預設值是 NULL。

*iSelectPage*<br/>
[在]頂部屬性頁的零基索引。 預設值為 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[CPropertySheet:cPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)構造函數的參數。

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a>CMFC 屬性表:啟用頁眉

在每個頁面頂端保留空間以繪製自訂標頭。

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>參數

*nHeaderHeight*<br/>
[在]標頭的高度(以像素為單位)。

### <a name="remarks"></a>備註

要使用*nHeaderHeight*參數的值繪製自訂標頭,要重寫[CMFC 屬性表::OnDrawPageHeader](#ondrawpageheader)方法。

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a>CMFC 屬性表:取得標題高度

擷取目前標頭的高度。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>傳回值

標頭的高度(以像素為單位)。

### <a name="remarks"></a>備註

呼叫[CMFC 屬性表:啟用PageHeader](#enablepageheader)方法,然後再調用此方法。

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a>CMFC 屬性表:取得檢視

擷取指定目前屬性工作表外觀的列舉值。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>傳回值

指定屬性表外觀的枚舉值之一。 有關可能值的清單,請參閱 CMFC 屬性表註解部分中的枚舉表[::SetLook](#setlook)。

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a>CMFC 屬性表:取得導航欄寬度

取得導覽列的寬度。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>傳回值

導覽列的寬度，以像素為單位。

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a>CMFC財產表:GetTab

擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>傳回值

內部選項卡控件物件。

### <a name="remarks"></a>備註

您可以設置屬性表,使其以不同的樣式顯示,例如樹控件、導航按鈕列表或一組選項卡式頁面。

在調用此方法之前,調用[CMFC 屬性表::SetLook](#setlook)方法來設置屬性表控件的外觀。 然後調用[CMFC 屬性表:init導航控制](#initnavigationcontrol)方法以初始化內部選項卡控制物件。 使用此方法檢索選項卡控制項物件,然後使用該物件處理屬性表上的選項卡。

如果屬性表控件未設置為以 Microsoft OneNote 的樣式顯示,則此方法在調試模式下斷言。

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a>CMFC 屬性表:init 導覽控制

初始化目前屬性工作表控制項的外觀。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>傳回值

指向屬性工作表控件視窗的指標。

### <a name="remarks"></a>備註

屬性表控件可以以幾種不同形式顯示,例如一組選項卡式頁面、樹控件或導航按鈕清單。 使用[CMFC 屬性表::SetLook](#setlook)方法指定屬性表控制件的外觀。

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a>CMFC 屬性表:打開 Activatepage

啟用屬性頁時由架構呼叫。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[在]指向表示啟用的屬性頁的屬性頁物件的指標。

### <a name="remarks"></a>備註

默認情況下,此方法可確保啟用的屬性頁滾動到檢視中。 如果當前屬性表的樣式包含 Microsoft Outlook 窗格,則此方法將相應的 Outlook 按鈕設置為選中的狀態。

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a>CMFC 屬性表:在繪製頁眉

由框架調用以繪製自定義屬性頁的標頭。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*nPage*<br/>
[在]零基屬性頁碼。

*整流頭*<br/>
[在]指定繪製標題的位置的邊界矩形。

### <a name="remarks"></a>備註

默認情況下,此方法不執行任何操作。 如果重寫此方法,請調用[CMFC 屬性表::啟用PageHeader](#enablepageheader)方法,然後框架調用此方法。

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a>CMFC 屬性表::刪除樹頁

由架構呼叫以從樹狀目錄控制項移除屬性頁。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[在]指向表示要刪除的屬性頁的屬性頁物件的指標。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a>CMFC 屬性表:刪除類別

從樹狀目錄控制項移除節點。

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>參數

*p 類別*<br/>
[在]指向要刪除的類別(節點)的指標。

### <a name="remarks"></a>備註

使用此方法從樹控件中刪除節點(也稱為類別)。 使用[CMFC 屬性表:addTreeCategory](#addtreecategory)方法將節點添加到樹控制項。

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a>CMFC 屬性表:刪除頁

從屬性工作表中移除屬性頁。

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>參數

*pPage*<br/>
[在]指向表示要刪除的屬性頁的屬性頁物件的指標。 不能是 NULL。

*nPage*<br/>
[在]要刪除的頁面的從零開始索引。

### <a name="remarks"></a>備註

此方法刪除指定的屬性頁並銷毀其關聯的視窗。 在[關閉 CMFC 屬性表](../../mfc/reference/cmfcpropertysheet-class.md)視窗之前,pPage 參數指定的屬性頁物件*pPage*不會銷毀。

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a>CMFC 屬性表:設定圖示清單

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
[在]映射清單的資源識別碼。

*殘雪*<br/>
[在]圖像清單中圖示的寬度(以像素為單位)。

*clr透明*<br/>
[在]透明圖像顏色。 此顏色的圖像部分將是透明的。 默認值是色品紅色,RGB(255,0,255)。

*h圖示*<br/>
[在]現有圖像清單的句柄。

### <a name="return-value"></a>傳回值

在第一個方法重載語法中,如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果屬性表以 Microsoft Outlook 樣式顯示,則框架將在屬性表的左側顯示導航按鈕列表,稱為 Outlook 窗格控件。 使用此方法可設置要由Outlook窗格控件使用的圖像清單。

有關支援此方法的方法的詳細資訊,請參閱[CImageList::建立](../../mfc/reference/cimagelist-class.md#create)與[CImageList::新增](../../mfc/reference/cimagelist-class.md#add)。 有關如何設定屬性表樣式的詳細資訊,請參閱[CMFC 屬性表:::SetLook](#setlook)。

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a>CMFC 屬性表:設定檢視

指定屬性工作表的外觀。

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>參數

*看*<br/>
[在]指定屬性表外觀的枚舉值之一。 屬性表的預設樣式為`CMFCPropertySheet::PropSheetLook_Tabs`。 有關詳細資訊,請參閱本主題的備註部分中的表。

*nNavControl 寬度*<br/>
[在]導航控制項寬度(以像素為單位)。 預設值是 100。

### <a name="remarks"></a>備註

要在預設值以外的樣式中顯示屬性表,請先在創建屬性工作表視窗之前調用此方法。

下表列出了可在*look*參數中指定的枚舉值。

|值|描述|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|( 預設 )顯示每個屬性頁的選項卡。 選項卡顯示在屬性表的頂部,如果選項卡數多於單個行中容納的選項卡數,則選項卡將被堆疊。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在屬性表的左側顯示 Microsoft Outlook 欄樣式中的導航按鈕清單。 清單中的每個按鈕都對應於屬性頁。 如果按鈕數超過清單的可見區域,則框架將顯示滾動箭頭。|
|`CMFCPropertySheet::PropSheetLook_Tree`|在屬性手冊的左側顯示樹控件。 樹控件的每個父節點或子節點對應於屬性頁。 如果節點數多於樹控件的可見區域,則框架將顯示滾動箭頭。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|為每個屬性頁顯示一個選項卡,以 Microsoft OneNote 的樣式顯示。 如果選項卡數多於單行中容納的選項卡數,則框架在屬性表頂部顯示選項卡,並滾動箭頭。|
|`CMFCPropertySheet::PropSheetLook_List`|在屬性表的左側顯示一個清單。 每個清單項對應於屬性頁。 如果清單項數多於清單的可見區域,則框架將顯示滾動箭頭。|

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage 類別](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)
