---
title: "CMFCRibbonCategory 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCategory class
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
caps.latest.revision: 38
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dccbaac6450985f0d5255a790d83f374b52f06f9
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory 類別
`CMFCRibbonCategory`類別會實作功能區索引標籤，其中包含一群[功能區面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](#addhidden)|將隱藏的項目加入至功能區分類。|  
|[CMFCRibbonCategory::AddPanel](#addpanel)|將新的面板加入至功能區分類。|  
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||  
|[CMFCRibbonCategory::FindByData](#findbydata)||  
|[CMFCRibbonCategory::FindByID](#findbyid)||  
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||  
|[CMFCRibbonCategory::GetContextID](#getcontextid)|傳回功能區類別的內容識別碼。|  
|[CMFCRibbonCategory::GetData](#getdata)|傳回與功能區類別相關聯的使用者定義的資料。|  
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonCategory::GetElements](#getelements)||  
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|取得屬於功能區類別的第一個可見項目。|  
|[CMFCRibbonCategory::GetFocused](#getfocused)|傳回具有焦點的項目。|  
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|傳回反白顯示的項目。|  
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||  
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||  
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|取得最後一個可見項目屬於功能區分類|  
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|傳回的功能區類別使用的大型影像清單的參考。|  
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||  
|[CMFCRibbonCategory::GetName](#getname)||  
|[CMFCRibbonCategory::GetPanel](#getpanel)|傳回位於指定索引上的功能區面板的指標。|  
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|在 功能區類別傳回功能區面板的數目。|  
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||  
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|傳回指定之功能區面板的索引。|  
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||  
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||  
|[CMFCRibbonCategory::GetRect](#getrect)||  
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|傳回的類別使用的小型影像清單的參考。|  
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|傳回目前功能區類別目錄 索引標籤的色彩。|  
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||  
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||  
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|取得所有屬於功能區類別的可見項目。|  
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||  
|[CMFCRibbonCategory::HitTest](#hittest)||  
|[CMFCRibbonCategory::HitTestEx](#hittestex)||  
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||  
|[CMFCRibbonCategory::IsActive](#isactive)||  
|[CMFCRibbonCategory::IsVisible](#isvisible)|判斷是否為可見的功能區分類。|  
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|表示父功能區是否有 Windows 7 樣式外觀 （矩形的小型應用程式按鈕）|  
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||  
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||  
|[CMFCRibbonCategory::OnDraw](#ondraw)||  
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||  
|[CMFCRibbonCategory::OnKey](#onkey)|當使用者按下鍵盤 按鈕時，由架構呼叫。|  
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||  
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||  
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||  
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||  
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||  
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||  
|[CMFCRibbonCategory::RemovePanel](#removepanel)||  
|[CMFCRibbonCategory::ReposPanels](#repospanels)||  
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|定義摺疊的順序出現在功能區類別的功能區面板。|  
|[CMFCRibbonCategory::SetData](#setdata)|將使用者定義資料存放區分類。|  
|[CMFCRibbonCategory::SetKeys](#setkeys)|將 keytip 指派給功能區分類。|  
|[CMFCRibbonCategory::SetName](#setname)||  
|[CMFCRibbonCategory::SetTabColor](#settabcolor)|設定的功能區分類的色彩。|  
  
## <a name="remarks"></a>備註  
 通常您會建立功能區類別間接呼叫[CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory)，其傳回的指標給新建立的功能區分類。 將面板加入至類別的呼叫[CMFCRibbonCategory::AddPanel](#addpanel)。  
  
 `CMFCRibbonTab`類別繪製功能區分類。 它衍生自[CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)。  
  
 下列範例示範如何建立功能區分類和面板加入。  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 下圖顯示首頁分類 RibbonApp 範例應用程式的圖形。  
  
 ![CMFCRibbonCategory 影像](../../mfc/reference/media/cmfcribboncategory.png "cmfcribboncategory")  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCRibbonCategory`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribboncategory.h  
  
##  <a name="addhidden"></a>CMFCRibbonCategory::AddHidden  
 將指定的功能區項目加入至功能區項目會顯示在自訂 對話方塊中的陣列。  
  
```  
void AddHidden(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in] `pElem`  
 功能區元素的指標。  
  
### <a name="remarks"></a>備註  
 在 [自訂] 對話方塊上的功能區項目是您可以加入快速存取工具列命令。  
  
##  <a name="addpanel"></a>CMFCRibbonCategory::AddPanel  
 建立功能區類別的功能區面板。  
  
```  
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,  
    HICON hIcon = 0,  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszPanelName`  
 新的功能區面板的名稱指標。  
  
 [in] `hIcon`  
 新的功能區面板的預設圖示的控制代碼。  
  
 [in] `pRTI`  
 自訂功能區面板的執行階段類別資訊的指標。  
  
### <a name="return-value"></a>傳回值  
 指向新的功能區面板如果方法成功。否則`NULL`若未建立面板。  
  
### <a name="remarks"></a>備註  
 如果您想要建立自訂功能區面板，您必須指定在其執行階段類別資訊`pRTI`。 自訂功能區面板類別必須衍生自`CMFCRibbonPanel`類別。  
  
 空間不足而無法顯示功能區項目時，會顯示功能區面板的預設圖示。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`AddPanel`方法中的`CMFCRibbonCategory`類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&10;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]  
  
##  <a name="cmfcribboncategory"></a>CMFCRibbonCategory::CMFCRibbonCategory  
 建構並初始化[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)物件。  
  
```  
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,  
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32));
```  
  
### <a name="parameters"></a>參數  
 [in] `pParenrRibbonBar`  
 功能區類別的父功能區列的指標。  
  
 [in] `lpszName`  
 功能區分類的名稱。  
  
 [in] `uiSmallImagesResID`  
 在功能區類別的功能區項目所使用的小型影像的影像清單的資源識別碼。  
  
 [in] `uiLargeImagesResID`  
 在功能區類別的功能區項目所使用的大型影像的影像清單的資源識別碼。  
  
 [in] `sizeSmallImage`  
 預設的功能區項目在功能區類別中的小型影像的大小。  
  
 [in] `sizeLargeImage`  
 預設功能區項目在功能區類別中的大型影像的大小。  
  
##  <a name="copyfrom"></a>CMFCRibbonCategory::CopyFrom  
 複製指定的狀態[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)目前[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)物件。  
  
```  
virtual void CopyFrom(CMFCRibbonCategory& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 來源 `CMFCRibbonCategory` 物件。  
  
### <a name="remarks"></a>備註  
  
##  <a name="findbydata"></a>CMFCRibbonCategory::FindByData  
 擷取與指定的資料相關聯的功能區項目。  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `dwData`  
 使用功能區項目相關聯的資料。  
  
 [in] `bVisibleOnly`  
 `TRUE`快速存取功能區項目包含在搜尋。`FALSE`排除在搜尋中的快速存取功能區項目。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="findbyid"></a>CMFCRibbonCategory::FindByID  
 擷取與指定的命令識別碼相關聯的功能區項目  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 功能區項目相關聯的命令識別碼。  
  
 [in] `bVisibleOnly`  
 `TRUE`快速存取功能區項目包含在搜尋。`FALSE`排除在搜尋中的快速存取功能區項目。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="findpanelwithelem"></a>CMFCRibbonCategory::FindPanelWithElem  
 擷取功能區面板，其中包含指定的功能區項目。  
  
```  
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>參數  
 [in] `pElement`  
 功能區元素的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 在功能區面板的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getcontextid"></a>CMFCRibbonCategory::GetContextID  
 擷取功能區類別的內容識別碼。  
  
```  
UINT GetContextID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區類別目錄的內容識別碼。  
  
### <a name="remarks"></a>備註  
 內容識別碼為 0，如果功能區類別不是內容的功能區分類。  
  
##  <a name="getdata"></a>CMFCRibbonCategory::GetData  
 擷取與功能區類別相關聯的使用者定義的資料。  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>傳回值  
 使用者定義的資料與功能區類別相關聯。  
  
##  <a name="getdroppeddown"></a>CMFCRibbonCategory::GetDroppedDown  
 擷取目前有顯示其快顯功能表功能區元素的指標。  
  
```  
CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getelements"></a>CMFCRibbonCategory::GetElements  
 擷取在功能區類別中的所有功能區項目。  
  
```  
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `arElements`  
 若要參考[CArray](../../mfc/reference/carray-class.md)的功能區項目。  
  
### <a name="remarks"></a>備註  
 陣列中包含專為快速存取工具列上的功能區項目。  
  
##  <a name="getelementsbyid"></a>CMFCRibbonCategory::GetElementsByID  
 擷取與指定的命令 ID 相關聯的所有功能區項目  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdID`  
 功能區項目相關聯的命令識別碼。  
  
 [in、out] `arElements`  
 若要參考[CArray](../../mfc/reference/carray-class.md)的功能區項目。  
  
### <a name="remarks"></a>備註  
 陣列中包含專為快速存取工具列上的功能區項目。  
  
##  <a name="getfirstvisibleelement"></a>CMFCRibbonCategory::GetFirstVisibleElement  
 擷取第一個可見項目屬於功能區分類。  
  
```  
CMFCRibbonBaseElement* GetFirstVisibleElement() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向第一個可見項目。可能是`NULL`如果類別沒有任何可見的項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getfocused"></a>CMFCRibbonCategory::GetFocused  
 傳回具有焦點的項目。  
  
```  
CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>傳回值  
 具有焦點的項目之指標或`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gethighlighted"></a>CMFCRibbonCategory::GetHighlighted  
 傳回反白顯示的項目。  
  
```  
CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>傳回值  
 反白顯示項目的指標或`NULL`如果沒有項目會反白顯示。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getimagecount"></a>CMFCRibbonCategory::GetImageCount  
 擷取指定的影像清單包含在功能區類別中的映像數目。  
  
```  
int GetImageCount(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsLargeImage`  
 `TRUE`大型影像清單中的映像數目`FALSE`的小型影像清單中的映像數目。  
  
### <a name="return-value"></a>傳回值  
 指定的影像清單中的映像數目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getimagesize"></a>CMFCRibbonCategory::GetImageSize  
 擷取指定的影像清單包含在功能區類別中的映像的大小。  
  
```  
CSize GetImageSize(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsLargeImage`  
 `TRUE`若為大型影像; 的大小`FALSE`小型影像的大小。  
  
### <a name="return-value"></a>傳回值  
 指定的影像清單中的映像的大小。  
  
### <a name="remarks"></a>備註  
 擷取大小包含全域影像縮放比例。  
  
##  <a name="getitemidslist"></a>CMFCRibbonCategory::GetItemIDsList  
 擷取功能區項目包含在功能區類別中的命令 Id。  
  
```  
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lstItems`  
 功能區項目在功能區類別中的命令 Id 的清單。  
  
 [in] `bHiddenOnly`  
 `TRUE`若要排除在功能區類別中，功能區面板上顯示的功能區項目`FALSE`在功能區類別中包含所有的功能區項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getlargeimages"></a>CMFCRibbonCategory::GetLargeImages  
 擷取包含在功能區類別中的大型影像清單。  
  
```  
CMFCToolBarImages& GetLargeImages();
```  
  
### <a name="return-value"></a>傳回值  
 包含在功能區類別中的大型影像清單。  
  
##  <a name="getlastvisibleelement"></a>CMFCRibbonCategory::GetLastVisibleElement  
 擷取功能區類別所屬的最後一個可見項目。  
  
```  
CMFCRibbonBaseElement* GetLastVisibleElement() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指向最後一個可見項目。可能是`NULL`如果類別沒有任何可見的項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getmaxheight"></a>CMFCRibbonCategory::GetMaxHeight  
 擷取包含在功能區類別的功能區面板的最大高度。  
  
```  
int GetMaxHeight(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區面板的裝置內容的指標。  
  
### <a name="return-value"></a>傳回值  
 功能區面板功能區類別中所包含的最大高度。  
  
### <a name="remarks"></a>備註  
 擷取的值包含功能區面板的上方和下方邊界的高度。  
  
##  <a name="getname"></a>CMFCRibbonCategory::GetName  
 擷取功能區類別的名稱。  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區類別目錄的名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getpanel"></a>CMFCRibbonCategory::GetPanel  
 傳回位於指定索引上的功能區面板的指標。  
  
```  
CMFCRibbonPanel* GetPanel(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 在功能區面板的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 功能區面板，位於指定索引處的指標。  
  
### <a name="remarks"></a>備註  
 如果擲回例外狀況`nIndex`超出範圍。  
  
##  <a name="getpanelcount"></a>CMFCRibbonCategory::GetPanelCount  
 在 功能區類別傳回功能區面板的數目。  
  
```  
int GetPanelCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在 功能區類別的功能區面板數目。  
  
##  <a name="getpanelfrompoint"></a>CMFCRibbonCategory::GetPanelFromPoint  
 如果指定的點位於，擷取功能區面板的指標。  
  
```  
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 在功能區面板的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 功能區類別中所包含的功能區面板為測試。  
  
##  <a name="getpanelindex"></a>CMFCRibbonCategory::GetPanelIndex  
 擷取指定的功能區面板的以零為起始的索引。  
  
```  
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pPanel`  
 在功能區面板的指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功; 指定的功能區面板的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 功能區類別中所包含的功能區面板會搜尋。  
  
##  <a name="getparentbutton"></a>CMFCRibbonCategory::GetParentButton  
 擷取功能區類別的父功能區項目。  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 讓指標回到父功能區項目，或`NULL`如果沒有父項目。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getparentmenubar"></a>CMFCRibbonCategory::GetParentMenuBar  
 將指標傳回至父功能表列的`CMFCRibbonCategory`物件。  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回的內容`m_pParentMenuBar`受保護的成員。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getparentribbonbar"></a>CMFCRibbonCategory::GetParentRibbonBar  
 擷取功能區類別的父功能區列。  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區類別的父功能區列的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getrect"></a>CMFCRibbonCategory::GetRect  
 擷取的功能區分類的顯示矩形。  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區類別顯示矩形。  
  
### <a name="remarks"></a>備註  
 功能區分類的顯示矩形不包括 [類別] 索引標籤。  
  
##  <a name="getsmallimages"></a>CMFCRibbonCategory::GetSmallImages  
 擷取包含在功能區類別中的小型影像清單。  
  
```  
CMFCToolBarImages& GetSmallImages();
```  
  
### <a name="return-value"></a>傳回值  
 包含在功能區類別中的小型影像清單。  
  
##  <a name="gettabcolor"></a>CMFCRibbonCategory::GetTabColor  
 傳回目前功能區類別目錄 索引標籤的色彩。  
  
```  
AFX_RibbonCategoryColor GetTabColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前功能區類別 索引標籤的色彩。  
  
### <a name="remarks"></a>備註  
 傳回的值可以是下列的列舉值之一︰  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="gettabrect"></a>CMFCRibbonCategory::GetTabRect  
 擷取功能區類別 索引標籤的顯示的矩形。  
  
```  
CRect GetTabRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 功能區類別 索引標籤顯示矩形。  
  
### <a name="remarks"></a>備註  
  
##  <a name="gettexttopline"></a>CMFCRibbonCategory::GetTextTopLine  
 擷取在功能區類別顯示為大型影像的功能區按鈕上的文字的垂直位置。  
  
```  
int GetTextTopLine() const;  
```  
  
### <a name="return-value"></a>傳回值  
 以像素為單位，顯示大型影像的功能區按鈕文字的垂直位置。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getvisibleelements"></a>CMFCRibbonCategory::GetVisibleElements  
 擷取所有可見的項目屬於功能區分類。  
  
```  
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,  
    CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>參數  
 `arElements`  
 所有可見項目的陣列。  
  
### <a name="remarks"></a>備註  
  
##  <a name="highlightpanel"></a>CMFCRibbonCategory::HighlightPanel  
 指定的功能區面板會反白顯示。  
  
```  
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `pHLPanel`  
 若要反白顯示功能區面板的指標。  
  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="return-value"></a>傳回值  
 指向先前反白顯示功能區面板。否則`NULL`如果叫用此方法時，會反白不顯示任何功能區面板。  
  
### <a name="remarks"></a>備註  
 如需反白顯示功能區面板的詳細資訊，請參閱[CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight)。  
  
##  <a name="hittest"></a>CMFCRibbonCategory::HitTest  
 如果指定的點位於，擷取功能區項目的指標。  
  
```  
CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckPanelCaption = FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 滑鼠指標，相對於視窗左上角的 x 和 y 座標。  
  
 [in] `bCheckPanelCaption`  
 `TRUE`若要測試的功能區面板標題中。`FALSE`排除功能區面板的標題。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 測試功能區類別中所包含的功能區項目。  
  
##  <a name="hittestex"></a>CMFCRibbonCategory::HitTestEx  
 如果指定的點位於，擷取的功能區項目以零為起始的索引。  
  
```  
int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 滑鼠指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，功能區項目之以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 測試功能區類別中所包含的功能區項目。  
  
##  <a name="hittestscrollbuttons"></a>CMFCRibbonCategory::HitTestScrollButtons  
 如果點落在功能區類別左或向右捲動按鈕，讓指標回到該按鈕。  
  
```  
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 要測試的點。  
  
### <a name="return-value"></a>傳回值  
 如果`point`落在左邊的周框矩形或向右捲動按鈕的功能區分類，讓指標回到該按鈕，或反之則傳回`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isactive"></a>CMFCRibbonCategory::IsActive  
 表示功能區類別是否在功能區列上使用中的類別。  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區類別是使用中的類別。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用中的功能區類別目錄會顯示其功能區面板。  
  
##  <a name="isvisible"></a>CMFCRibbonCategory::IsVisible  
 表示功能區類別是否為可見。  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區類別為可見的。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 顯示功能區類別目錄會顯示類別 索引標籤。  
  
##  <a name="iswindows7look"></a>CMFCRibbonCategory::IsWindows7Look  
 表示父功能區是否有 Windows 7 尋找 （矩形的小型應用程式按鈕）。  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果父功能區看起來; Windows 7否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="notifycontrolcommand"></a>CMFCRibbonCategory::NotifyControlCommand  
 WM_NOTIFY 命令訊息傳遞給所有`CMFCRibbonPanel`中的項目`CMFCRibbonCategory`之前處理訊息的。  
  
```  
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,  
    int nNotifyCode,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAccelerator`  
 `TRUE`如果此命令的快速鍵，來源或`FALSE`否則。  
  
 [in] `nNotifyCode`  
 通知程式碼。  
  
 [in] `wParam`  
 訊息的 WPARAM 欄位。  
  
 [in] `lParam`  
 訊息的 LPARAM 欄位。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`是否已處理訊息，或`FALSE`如果不是。  
  
### <a name="remarks"></a>備註  
  
##  <a name="oncancelmode"></a>CMFCRibbonCategory::OnCancelMode  
 叫用 [取消] 模式中所有`CMFCRibbonPanel`的項目`CMFCRibbonCategory`。  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondraw"></a>CMFCRibbonCategory::OnDraw  
 若要繪製功能區類別架構呼叫。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區類別的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawimage"></a>CMFCRibbonCategory::OnDrawImage  
 在功能區類別上繪製指定的映像的架構所呼叫。  
  
```  
virtual BOOL OnDrawImage(
    CDC* pDC,  
    CRect rect,  
    CMFCRibbonBaseElement* pElement,  
    BOOL bIsLargeImage,  
    BOOL nImageIndex,  
    BOOL bCenter);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 映像的裝置內容的指標。  
  
 [in] `rect`  
 顯示影像的矩形。  
  
 [in] `pElement`  
 包含影像的功能區元素的指標。  
  
 [in] `bIsLargeImage`  
 `TRUE`如果影像非常大。`FALSE`如果影像較小。  
  
 [in] `nImageIndex`  
 映像陣列，包含在功能區類別中的映像的以零為起始的索引。  
  
 [in] `bCenter`  
 `TRUE`若要置中的映像中的顯示矩形。`FALSE`繪製影像左上角的顯示矩形。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ondrawmenuborder"></a>CMFCRibbonCategory::OnDrawMenuBorder  
 若要繪製框線的快顯功能表架構呼叫。  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 不使用這個參數。  
  
 [in] `pMenuBar`  
 不使用這個參數。  
  
### <a name="remarks"></a>備註  
 依預設這個方法沒有作用。 覆寫這個方法，以繪製框線的快顯功能表。  
  
##  <a name="onkey"></a>CMFCRibbonCategory::OnKey  
 當使用者按下鍵盤 按鈕時，由架構呼叫。  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 `nChar`  
 使用者按下按鍵虛擬按鍵碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttondown"></a>CMFCRibbonCategory::OnLButtonDown  
 若要擷取在指定的點的功能區項目，當使用者按下滑鼠左鍵時架構呼叫。  
  
```  
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 滑鼠指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，功能區項目的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onlbuttonup"></a>CMFCRibbonCategory::OnLButtonUp  
 當使用者放開滑鼠左鍵並透過功能區類別的指標是由架構呼叫。  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onmousemove"></a>CMFCRibbonCategory::OnMouseMove  
 若要更新的功能區類別顯示移動功能區列上的指標時，由架構呼叫。  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>參數  
 [in] `point`  
 指標，相對於視窗左上角的 x 和 y 座標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onrtlchanged"></a>CMFCRibbonCategory::OnRTLChanged  
 版面配置變更方向時，由架構呼叫。  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsRTL`  
 `TRUE`如果版面配置是從右至左。`FALSE`如果版面配置是由左到右。  
  
### <a name="remarks"></a>備註  
 這個方法會調整所有功能區面板和功能區類別中所包含的功能區項目的版面的配置。  
  
##  <a name="onscrollhorz"></a>CMFCRibbonCategory::OnScrollHorz  
 將功能區分類，以水平方向的捲動。  
  
```  
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,  
    int nScrollOffset = 0);
```  
  
### <a name="parameters"></a>參數  
 [in] `bScrollLeft`  
 `TRUE`捲動至左。`FALSE`捲到右邊。  
  
 [in] `nScrollOffset`  
 捲軸的距離，單位為像素。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果功能區類別移以水平方向。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onupdatecmdui"></a>CMFCRibbonCategory::OnUpdateCmdUI  
 呼叫`OnUpdateCmdUI`成員函式中每個`CMFCRibbonPanel`的項目`CMFCRibbonCategory`啟用或停用使用者介面項目中的。  
  
```  
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,  
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>參數  
 [in] `pCmdUI`  
 指標`CMFCRibbonCmdUI`物件，指定要啟用的使用者介面項目、 哪些是要停用。  
  
 [in] `pTarget`  
 啟用或停用的使用者介面項目會控制視窗的指標。  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`若要停用的使用者介面項目，如果沒有處理常式中定義的訊息對應。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="recalclayout"></a>CMFCRibbonCategory::RecalcLayout  
 調整功能區類別上的所有控制項的版面配置。  
  
```  
virtual void RecalcLayout(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區類別的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removepanel"></a>CMFCRibbonCategory::RemovePanel  
 在功能區面板移除功能區分類。  
  
```cpp  
BOOL RemovePanel(
    int nIndex,  
    BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 若要移除面板的索引編號。 藉由呼叫取得[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)方法。  
  
 [in] `bDelete`  
 `TRUE`若要刪除面板物件從記憶體中。`FALSE`移除面板物件而非加以刪除。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功則為 `TRUE`；否則為 `FALSE`。  
  
##  <a name="repospanels"></a>CMFCRibbonCategory::ReposPanels  
 調整功能區類別中所包含的功能區面板上的所有控制項的版面配置。  
  
```  
virtual void ReposPanels(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 功能區類別中所包含的功能區面板的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setcollapseorder"></a>CMFCRibbonCategory::SetCollapseOrder  
 定義功能區類別的功能區面板摺疊的順序。  
  
```  
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```  
  
### <a name="parameters"></a>參數  
 [in] `arCollapseOrder`  
 指定的摺疊的順序。 陣列包含功能區面板的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 程式庫會定義摺疊的順序。 不過，您可以自訂此行為，藉由提供指定的摺疊順序的索引清單中的類別。  
  
 當類別偵測到它已摺疊在功能區面板時，它會尋找下一個項目，指定清單中。 如果清單是空的或您沒有指定足夠的元素，類別會使用內部演算法。  
  
 例如，類別具有三個功能區面板和可摺疊數次直到所有面板完全摺疊狀態。 您可以設定下列摺疊順序︰ 0、 0、 2、 2。 在此情況下，類別會摺疊面板 0 兩次，表 2 兩倍。 索引為 1 的面板會保持展開。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetCollapseOrder`方法中的`CMFCRibbonCategory`類別。 此範例示範如何建構的陣列，摺疊的順序，以及如何將摺疊順序設定為功能區類別。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&13;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]  
  
##  <a name="setdata"></a>CMFCRibbonCategory::SetData  
 設定與功能區類別相關聯的使用者定義資料。  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 [in] `dwData`  
 使用者定義的資料。  
  
##  <a name="setkeys"></a>CMFCRibbonCategory::SetKeys  
 將 keytip 指派給功能區分類。  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszKeys`  
 Keytip 的文字。  
  
### <a name="remarks"></a>備註  
 當使用者按下 Alt 或 F10 鍵，會顯示按鍵提示。  
  
##  <a name="setname"></a>CMFCRibbonCategory::SetName  
 將名稱和 keytip 指派給功能區分類。  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 名稱和 keytip 的功能區分類。  
  
### <a name="remarks"></a>備註  
 若要設定的功能區分類 keytip，附加新行逸出序列，後面接著 keytip 字元`lpszName`。  
  
##  <a name="settabcolor"></a>CMFCRibbonCategory::SetTabColor  
 設定的功能區分類的色彩。  
  
```  
void SetTabColor(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 指定功能區類別的新的色彩。  
  
### <a name="remarks"></a>備註  
 色彩可以是下列值之一︰  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)

