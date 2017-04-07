---
title: "CMFCPropertySheet 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertySheet::PreTranslateMessage method
- CMFCPropertySheet::OnInitDialog method
- CMFCPropertySheet class
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
caps.latest.revision: 35
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
ms.openlocfilehash: a157a0afa4542bc023ba4d7149e78a71bbd56e74
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet 類別
`CMFCPropertySheet` 類別支援屬性工作表，其中每個屬性頁是由頁面索引標籤、工具列按鈕、樹狀目錄控制項節點或清單項目所表示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPropertySheet : public CPropertySheet  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
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
|`CMFCPropertySheet::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|初始化目前屬性工作表控制項的外觀。|  
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|啟用屬性頁時由架構呼叫。|  
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|由架構呼叫以繪製自訂屬性頁標頭。|  
|`CMFCPropertySheet::OnInitDialog`|處理[WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428)訊息。 (覆寫[CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)。)|  
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|由架構呼叫以從樹狀目錄控制項移除屬性頁。|  
|`CMFCPropertySheet::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫 `CPropertySheet::PreTranslateMessage`。)|  
|[CMFCPropertySheet::RemoveCategory](#removecategory)|從樹狀目錄控制項移除節點。|  
|[CMFCPropertySheet::RemovePage](#removepage)|從屬性工作表中移除屬性頁。|  
|[CMFCPropertySheet::SetIconsList](#seticonslist)|指定在 Outlook 窗格之導覽控制項中使用的映像清單。|  
|[CMFCPropertySheet::SetLook](#setlook)|指定屬性工作表的外觀。|  
  
## <a name="remarks"></a>備註  
 `CMFCPropertySheet` 類別表示屬性工作表，也稱為索引標籤對話方塊。 `CMFCPropertySheet` 類別能以各種方式顯示屬性頁。  
  
 請執行下列步驟，在應用程式中使用 `CMFCPropertySheet` 類別。  
  
1.  自 `CMFCPropertySheet` 類別衍生類別並加以命名，例如，CMyPropertySheet。  
  
2.  建構[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)每個屬性頁的物件。  
  
3.  呼叫[CMFCPropertySheet::SetLook](#setlook) CMyPropertySheet 建構函式中的方法。 該方法的參數會指定屬性頁應該要顯示為沿著屬性工作表頂端或左邊的索引標籤；Microsoft OneNote 屬性工作表樣式的索引標籤；在 Microsoft Outlook 工具列控制項上的按鈕；在樹狀目錄控制項上的節點；或在屬性工作表左邊的項目清單。  
  
4.  如果您建立屬性工作表中的 Microsoft Outlook 工具列的樣式時，呼叫[CMFCPropertySheet::SetIconsList](#seticonslist)方法，以將影像清單與屬性頁。  
  
5.  呼叫[CMFCPropertySheet::AddPage](#addpage)方法，每個屬性頁。  
  
6.  建立 `CMFCPropertySheet` 控制項，並呼叫其 `DoModal` 方法。  
  
## <a name="illustrations"></a>插圖  
 下圖描述其樣式為內嵌 Microsoft Outlook 工具列的屬性工作表。 Outlook 工具列會出現在屬性工作表的左邊。  
  
 ![CMFCPropertySheet 色彩控制項](../../mfc/reference/media/cmfcpropertysheet_color.png "cmfcpropertysheet_color")  
  
 下圖顯示屬性工作表，其中包含[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)物件。 該物件是樣式為標準通用控制項屬性頁的屬性工作表。  
  
 ![CMFCPropertySheet 清單和屬性控制項](../../mfc/reference/media/cmfcpropertysheet_list.png "cmfcpropertysheet_list")  
  
 下圖描述其樣式為樹狀目錄控制項的屬性工作表。  
  
 ![屬性樹狀目錄](../../mfc/reference/media/proptree.png "proptree")  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpropertysheet.h  
  
##  <a name="addpage"></a>CMFCPropertySheet::AddPage  
 將頁面新增至屬性工作表。  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPage`  
 Page 物件的指標。 此參數不得為`NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法與屬性工作表中最右邊的索引標籤加入指定的屬性頁面。 因此，使用這個方法來新增的網頁中左到右的順序。  
  
 Microsoft outlook 樣式中屬性工作表時，架構會顯示屬性工作表左邊的導覽按鈕的清單。 這個方法會加入屬性頁之後，它會將對應的按鈕加入至清單中。 若要顯示屬性頁，請按一下對應的按鈕。 如需有關樣式的屬性工作表，請參閱[CMFCPropertySheet::SetLook](#setlook)。  
  
##  <a name="addpagetotree"></a>CMFCPropertySheet::AddPageToTree  
 將新的屬性頁新增至樹狀目錄控制項。  
  
```  
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,  
    CMFCPropertyPage* pPage,  
    int nIconNum=-1,  
    int nSelIconNum=-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCategory`  
 父樹狀節點中，指標或`NULL`將指定的頁面與最上層節點。 呼叫[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法，以取得這個指標。  
  
 [in] `pPage`  
 屬性頁物件的指標。  
  
 [in] `nIconNum`  
 圖示，則為-1 會使用沒有圖示的以零為起始的索引。 如果未選取  頁面上，樹狀目錄控制項屬性頁旁會顯示圖示。 預設值為 -1。  
  
 [in] `nSelIconNum`  
 圖示，則為-1 會使用沒有圖示的以零為起始的索引。 選取頁面時，樹狀目錄控制項屬性頁旁會顯示圖示。 預設值為 -1。  
  
### <a name="remarks"></a>備註  
 這個方法會為分葉節點的樹狀目錄控制項加入屬性頁。 若要加入屬性頁，建立`CMFCPropertySheet`物件，請呼叫[CMFCPropertySheet::SetLook](#setlook)方法`look`參數設定為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用此方法加入屬性頁。  
  
##  <a name="addtreecategory"></a>CMFCPropertySheet::AddTreeCategory  
 將新的節點新增至樹狀目錄控制項。  
  
```  
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,  
    int nIconNum=-1,  
    int nSelectedIconNum=-1,  
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszLabel`  
 節點的名稱。  
  
 [in] `nIconNum`  
 圖示，則為-1 會使用沒有圖示的以零為起始的索引。 如果未選取  頁面上，樹狀目錄控制項屬性頁旁會顯示圖示。 預設值為 -1。  
  
 [in] `nSelectedIconNum`  
 圖示，則為-1 會使用沒有圖示的以零為起始的索引。 選取頁面時，樹狀目錄控制項屬性頁旁會顯示圖示。 預設值為 -1。  
  
 [in] `pParentCategory`  
 父樹狀節點中，指標或`NULL`將指定的頁面與最上層節點。 設定此參數與[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法。  
  
### <a name="return-value"></a>傳回值  
 新的節點樹狀結構控制項中的指標。  
  
### <a name="remarks"></a>備註  
 使用此方法將新的節點，也稱為類別，新增至樹狀目錄控制項。 若要加入的節點，建立`CMFCPropertySheet`物件，請呼叫[CMFCPropertySheet::SetLook](#setlook)方法`look`參數設定為`CMFCPropertySheet::PropSheetLook_Tree`，然後使用這個方法，將節點加入。  
  
 使用這個方法的傳回值中的後續呼叫[CMFCPropertySheet::AddPageToTree](#addpagetotree)和[CMFCPropertySheet::AddTreeCategory](#addtreecategory)。  
  
##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet::CMFCPropertySheet  
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
 [in] `pszCaption`  
 字串，包含屬性工作表的標題。 不能是`NULL`。  
  
 [in] `nIDCaption`  
 資源識別碼，其中包含的屬性工作表的標題。  
  
 [in] `pParentWnd`  
 屬性工作表的父視窗的指標或`NULL`父視窗是否為應用程式的主視窗。 預設值是 `NULL`。  
  
 [in] `iSelectPage`  
 最上層的屬性頁的以零為起始的索引。 預設值為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱參數[CPropertySheet::CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)建構函式。  
  
##  <a name="enablepageheader"></a>CMFCPropertySheet::EnablePageHeader  
 在每個頁面頂端保留空間以繪製自訂標頭。  
  
```  
void EnablePageHeader(int nHeaderHeight);
```  
  
### <a name="parameters"></a>參數  
 [in] `nHeaderHeight`  
 標頭，單位為像素的高度。  
  
### <a name="remarks"></a>備註  
 若要使用的值`nHeaderHeight`參數，以繪製自訂標頭，覆寫[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)方法。  
  
##  <a name="getheaderheight"></a>CMFCPropertySheet::GetHeaderHeight  
 擷取目前標頭的高度。  
  
```  
int GetHeaderHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 標頭，單位為像素的高度。  
  
### <a name="remarks"></a>備註  
 呼叫[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前呼叫這個方法。  
  
##  <a name="getlook"></a>CMFCPropertySheet::GetLook  
 擷取指定目前屬性工作表外觀的列舉值。  
  
```  
PropSheetLook GetLook() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個列舉值，指定屬性工作表的外觀。 可能值的清單，請參閱 < 備註 > 一節中的列舉型別資料表[CMFCPropertySheet::SetLook](#setlook)。  
  
##  <a name="getnavbarwidth"></a>CMFCPropertySheet::GetNavBarWidth  
 取得導覽列的寬度。  
  
```  
int GetNavBarWidth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 導覽列的寬度，以像素為單位。  
  
##  <a name="gettab"></a>CMFCPropertySheet::GetTab  
 擷取支援目前屬性工作表控制項的內部索引標籤控制項物件。  
  
```  
CMFCTabCtrl& GetTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 內部 索引標籤控制項物件。  
  
### <a name="remarks"></a>備註  
 您可以設定的屬性工作表，使其出現在不同的樣式，例如樹狀目錄控制項導覽按鈕或一組索引標籤式頁面的清單。  
  
 在呼叫這個方法之前，呼叫[CMFCPropertySheet::SetLook](#setlook)方法來設定屬性工作表控制項的外觀。 然後呼叫[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)方法來初始化內部 索引標籤控制項物件。 使用此方法來擷取索引標籤控制項物件，然後使用該物件使用屬性工作表上的索引標籤。  
  
 如果未設定屬性工作表控制項才會出現在 Microsoft onenote 樣式，在偵錯模式中這個方法會判斷提示。  
  
##  <a name="initnavigationcontrol"></a>CMFCPropertySheet::InitNavigationControl  
 初始化目前屬性工作表控制項的外觀。  
  
```  
virtual CWnd* InitNavigationControl();
```  
  
### <a name="return-value"></a>傳回值  
 屬性工作表控制項視窗的指標。  
  
### <a name="remarks"></a>備註  
 屬性工作表控制項可以出現在數種不同格式的詳細資訊，例如一組索引標籤式的頁面、 樹狀目錄控制項或瀏覽按鈕的清單。 使用[CMFCPropertySheet::SetLook](#setlook)方法，以指定的屬性工作表控制項的外觀。  
  
##  <a name="onactivatepage"></a>CMFCPropertySheet::OnActivatePage  
 啟用屬性頁時由架構呼叫。  
  
```  
virtual void OnActivatePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPage`  
 代表已啟用的屬性頁的屬性頁面物件的指標。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法可確保已啟用的屬性頁面上，捲動到檢視。 如果目前的屬性工作表的樣式會包含 Microsoft Outlook 窗格，這個方法會設定對應的 Outlook 按鈕為選取狀態。  
  
##  <a name="ondrawpageheader"></a>CMFCPropertySheet::OnDrawPageHeader  
 若要繪製自訂屬性頁的標頭架構呼叫。  
  
```  
virtual void OnDrawPageHeader(
    CDC* pDC,  
    int nPage,  
    CRect rectHeader);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `nPage`  
 以零為起始的屬性頁數目。  
  
 [in] `rectHeader`  
 指定要繪製的標頭的目標周框矩形。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法沒有作用。 如果您覆寫這個方法，呼叫[CMFCPropertySheet::EnablePageHeader](#enablepageheader)方法之前，架構會呼叫這個方法。  
  
##  <a name="onremovetreepage"></a>CMFCPropertySheet::OnRemoveTreePage  
 由架構呼叫以從樹狀目錄控制項移除屬性頁。  
  
```  
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPage`  
 代表要移除的屬性頁面的屬性頁面物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="removecategory"></a>CMFCPropertySheet::RemoveCategory  
 從樹狀目錄控制項移除節點。  
  
```  
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCategory`  
 若要移除的類別 （節點） 的指標。  
  
### <a name="remarks"></a>備註  
 若要移除的節點，也就是類別，從樹狀目錄控制項使用這個方法。 使用[CMFCPropertySheet::AddTreeCategory](#addtreecategory)方法，以將節點加入樹狀目錄控制項。  
  
##  <a name="removepage"></a>CMFCPropertySheet::RemovePage  
 從屬性工作表中移除屬性頁。  
  
```  
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `pPage`  
 屬性代表要移除的屬性頁面的 page 物件的指標。 不能是`NULL`。  
  
 [in] `nPage`  
 要移除之頁面的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 這個方法中移除指定的屬性頁面，並會終結其相關聯的視窗。 [屬性] 頁面上的物件，`pPage`參數會指定不會損毀之前[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  視窗已關閉。  
  
##  <a name="seticonslist"></a>CMFCPropertySheet::SetIconsList  
 指定在 Outlook 窗格之導覽控制項中使用的映像清單。  
  
```  
BOOL SetIconsList(
    UINT uiImageListResID,  
    int cx,  
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiImageListResID`  
 影像清單的資源識別碼。  
  
 [in] `cx`  
 寬度，單位為像素的影像清單中的圖示。  
  
 [in] `clrTransparent`  
 透明影像的色彩。 此色彩部分會是影像的透明的。 預設值是的洋紅色 RGB(255,0,255)。  
  
 [in] `hIcons`  
 現有的影像清單控制代碼。  
  
### <a name="return-value"></a>傳回值  
 第一個方法多載的語法，`TRUE`如果此方法成功，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果屬性工作表是在 Microsoft Outlook 的樣式，架構會顯示一份稱為 Outlook 窗格控制項中，屬性工作表左邊的瀏覽按鈕。 若要設定 Outlook 窗格控制項所使用的影像清單中使用這個方法。  
  
 如需有關支援這個方法的方法的詳細資訊，請參閱[CImageList::Create](../../mfc/reference/cimagelist-class.md#create)和[CImageList::Add](../../mfc/reference/cimagelist-class.md#add)。 如需如何設定的屬性工作表樣式的詳細資訊，請參閱[CMFCPropertySheet::SetLook](#setlook)。  
  
##  <a name="setlook"></a>CMFCPropertySheet::SetLook  
 指定屬性工作表的外觀。  
  
```  
void SetLook(
    PropSheetLook look,  
    int nNavControlWidth=100);
```  
  
### <a name="parameters"></a>參數  
 [in] `look`  
 其中一個列舉值，指定屬性工作表的外觀。 屬性工作表的預設樣式為`CMFCPropertySheet::PropSheetLook_Tabs`。 如需詳細資訊，請參閱本主題的 < 備註 > 一節中的資料表。  
  
 [in] `nNavControlWidth`  
 瀏覽控制項，單位為像素的寬度。 預設值為 100。  
  
### <a name="remarks"></a>備註  
 若要顯示屬性工作表中的樣式不是預設值，請建立屬性工作表視窗之前，先呼叫這個方法。  
  
 下表列出可以在指定的列舉值`look`參數。  
  
|值|說明|  
|-----------|-----------------|  
|`CMFCPropertySheet::PropSheetLook_Tabs`|（預設值）顯示每個屬性頁 索引標籤。 索引標籤會顯示在屬性工作表的頂部，會發生堆疊，如果有多個索引標籤會超過單一資料列。|  
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|在 Microsoft outlook 功能區，屬性工作表左側的樣式，會顯示一份瀏覽按鈕。 在清單中的每個按鈕對應至屬性頁。 如果有多個按鈕會超過清單的可見區域，架構會顯示捲軸箭號。|  
|`CMFCPropertySheet::PropSheetLook_Tree`|顯示屬性工作表左側的樹狀目錄控制項。 每個樹狀目錄控制項的父或子節點對應至屬性頁。 如果有多個節點會超過樹狀目錄控制項的可見區域，架構會顯示捲軸箭號。|  
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|顯示索引標籤上，Microsoft onenote 樣式，每個屬性頁中。 架構會顯示屬性工作表頂端的索引標籤並捲動箭號，如果有多個索引標籤，比能夠容納的單一資料列。|  
|`CMFCPropertySheet::PropSheetLook_List`|顯示屬性工作表左側的清單。 每個清單項目會對應至屬性頁。 如果有多個清單項目會超過清單的可見區域，架構會顯示捲軸箭號。|  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyPage 類別](../../mfc/reference/cmfcpropertypage-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)

