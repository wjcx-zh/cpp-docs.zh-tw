---
title: "CMFCOutlookBarPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
dev_langs:
- C++
helpviewer_keywords:
- Dock method
- IsChangeState method
- SmartUpdate method
- OnBeforeFloat method
- RestoreOriginalstate method
- CMFCOutlookBarPane class
- CanBeRestored method
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: da4fab1a6d94e962090f21414062dc2da0c9482c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 類別
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 控制項是衍生自[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)可插入至 Outlook 功能區 ( [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 功能區窗格包含一欄大型按鈕。 如果按鈕清單比窗格還要大，使用者可以上下捲動清單。 當使用者將 Outlook 功能區窗格從 Outlook 功能區卸離時，這個窗格可以在主框架視窗中停駐或浮動。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|預設建構函式。|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|將按鈕加入至 Outlook 功能區窗格。|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|判斷是否可以到另一個窗格或框架視窗停駐窗格。 (覆寫[CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|  
|`CMFCOutlookBarPane::CanBeRestored`|決定是否系統可以工具列後還原到其原始狀態的自訂。 (覆寫[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Outlook 功能區窗格中的映像所使用的資源會釋出。|  
|[CMFCOutlookBarPane::Create](#create)|建立 Outlook 功能區窗格。|  
|`CMFCOutlookBarPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCOutlookBarPane::Dock`|若要停駐 Outlook 功能區窗格架構呼叫。 (覆寫 `CPane::Dock`。)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定是否在 Outlook 功能區窗格捲動箭號 頁面上，或按鈕前進按鈕的清單。|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|傳回 Outlook 功能區窗格的一般 （非選取） 的文字的色彩。|  
|`CMFCOutlookBarPane::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|判斷是否載入 Outlook 功能區窗格的背景影像。|  
|`CMFCOutlookBarPane::IsChangeState`|判斷是否可能會停駐浮動窗格。 (覆寫 `CPane::IsChangeState`。)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|決定按鈕框線為灰色時按鈕會反白顯示，並顯示背景影像。|  
|`CMFCOutlookBarPane::OnBeforeFloat`|窗格即將浮點數時，由架構呼叫。 (覆寫[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|移除具有指定的命令 ID 的按鈕|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。 (覆寫[CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|設定背景色彩。|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|設定背景影像。|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|將 Outlook 功能區窗格重設為原始組按鈕。|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|設定 Outlook 功能區窗格中的按鈕周圍使用邊框距離的像素數目。|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|設定 Outlook 功能區窗格中的規則和反白顯示文字的色彩。|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|設定 Outlook 功能區窗格的透明色彩。|  
|`CMFCOutlookBarPane::SmartUpdate`|更新 outlook 功能區內部使用。 (覆寫 `CMFCToolBar::SmartUpdate`。)|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定的快顯功能表項目會顯示在自訂模式。|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|從 Outlook 功能區窗格中移除所有的按鈕。 (覆寫[CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|  
  
## <a name="remarks"></a>備註  
 如需如何實作 outlook 功能區的資訊，請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 例如 outlook 功能區中，請參閱 OutlookDemo 範例專案。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法`CMFCOutlookBarPane`類別。 此範例示範如何建立 Outlook 功能區窗格中，啟用頁面捲動模式、 啟用停駐，以及設定 outlook 功能區的背景色彩。 此程式碼片段是一部分[Outlook 多重檢視範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews #&3;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews #&4;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxoutlookbarpane.h  
  
##  <a name="a-nameaddbuttona--cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton  
 將按鈕加入至 Outlook 功能區窗格。  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiImage`  
 指定點陣圖的資源識別碼。  
  
 [in] `lpszLabel`  
 指定按鈕的文字。  
  
 [in] `iIdCommand`  
 指定按鈕控制項的 id。  
  
 [in] `iInsertAt`  
 在 outlook 功能區 頁面上的 插入 按鈕，指定以零為起始的索引。  
  
 [in] `uiLabel`  
 字串資源識別碼。  
  
 [in] `szBmpFileName`  
 指定要載入之磁碟映像檔案名稱。  
  
 [in] `szLabel`  
 指定按鈕的文字。  
  
 [in] `hBmp`  
 按鈕的點陣圖控制代碼。  
  
 [in] `hIcon`  
 按鈕的圖示控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功，加入按鈕否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用此方法的 outlook 功能區 頁面中插入新的按鈕。 從應用程式資源，或從磁碟檔案可以載入按鈕的影像。  
  
 如果所指定的頁面識別碼`uiPageID`為-1，按鈕會插入第一頁。  
  
 如果指定的索引`iInsertAt`為-1，按鈕就會加入頁面的結尾。  
  
##  <a name="a-namecanbeattacheda--cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameclearalla--cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll  
 Outlook 功能區窗格上的映像所使用的資源會釋出。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會直接呼叫[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，Outlook 功能區窗格所使用的映像上呼叫它。  
  
##  <a name="a-namecreatea--cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Create  
 建立 Outlook 功能區窗格。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParentWnd`  
 指定 Outlook 功能區窗格控制項的父視窗。 必須不是 `NULL`。  
  
 [in] `dwStyle`  
 視窗樣式。  視窗樣式的清單，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `uiID`  
 控制項 id。 必須是唯一啟用的控制項狀態儲存。  
  
 [in] `dwControlBarStyle`  
 指定定義 Outlook 功能區窗格控制項的行為，從 outlook 功能區卸離時的特殊樣式。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果此方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 若要建構`CMFCOutlookBarPane`物件，第一次呼叫建構函式，然後呼叫`Create`，其中建立列窗格控制項 Outlook，並將它附加`CMFCOutlookBarPane`物件。  
  
 如需詳細資訊`dwControlBarStyle`看到[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)。  
  
##  <a name="a-nameenablecontextmenuitemsa--cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems  
 指定的快顯功能表項目會顯示在自訂模式。  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>參數  
 [in] `pButton`  
 使用者按下工具列按鈕指標。  
  
 [in] `pPopup`  
 指標的捷徑功能表。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果快顯功能表應該顯示，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以修改架構的標準快顯功能表，架構會顯示在自訂模式。  
  
 預設實作會檢查自訂模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))，如果設定為`TRUE`，會停用所有的快顯功能表項目除外**刪除**。 然後，它只會傳遞的輸入的參數`CMFCToolBar::EnableContextMenuItems`。  
  
> [!NOTE]
> *內容功能表*是快顯功能表的同義字。  
  
##  <a name="a-nameenablepagescrollmodea--cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode  
 指定是否在 Outlook 功能區窗格捲動箭號前進頁面或由按鈕的按鈕的清單。  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bPageScroll`  
 如果`TRUE`，啟用頁面捲動模式。 如果`FALSE`，停用頁面捲動模式。  
  
##  <a name="a-namegetregularcolora--cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor  
 一般會傳回 (也就是未選取) 的 Outlook 功能區窗格的文字色彩。  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值為目前的文字色彩。  
  
### <a name="remarks"></a>備註  
 使用[CMFCOutlookBarPane::SetTextColor](#settextcolor)設定 outlook 功能區的目前 （一般和所選） 的文字色彩。 您可以藉由呼叫取得預設文字色彩[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)函式與`COLOR_WINDOW`索引。  
  
##  <a name="a-nameisbackgroundtexturea--cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture  
 判斷是否載入 Outlook 功能區窗格的背景影像。  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果沒有顯示，背景影像否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以加入背景影像，藉由呼叫[CMFCOutlookBarPane::SetBackImage](#setbackimage)函式。  
  
 如果沒有任何背景影像，以使用指定的色彩繪製背景[CMFCOutlookBarPane::SetBackColor](#setbackcolor)。  
  
##  <a name="a-nameisdrawshadedhighlighta--cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight  
 決定按鈕框線為灰色時按鈕會反白顯示，並顯示背景影像。  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕的框線呈現灰色。否則`FALSE`。  
  
##  <a name="a-nameremoveallbuttonsa--cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons  
 從 Outlook 功能區窗格中移除所有的按鈕。  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="a-nameremovebuttona--cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton  
 移除具有指定的命令 ID 的按鈕  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>參數  
 [in] `iIdCommand`  
 指定要移除按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功移除 按鈕。`FALSE`如果指定的命令 ID 無效。  
  
##  <a name="a-namesetbackcolora--cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor  
 設定 outlook 功能區的背景色彩。  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 指定新的背景色彩。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定目前的 outlook 功能區的背景色彩。 只有在沒有任何背景影像，會使用背景色彩。  
  
##  <a name="a-namesetbackimagea--cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage  
 設定背景影像。  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiImageID`  
 指定影像的資源 id。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來設定 Outlook 狀態列的背景影像。 受管理的背景影像清單是由內嵌[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件。  
  
##  <a name="a-namesetdefaultstatea--cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState  
 將 Outlook 功能區窗格重設為原始組按鈕。  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>備註  
 這個方法會將 Outlook 列按鈕還原至原始集合。 這個方法就像`CMFCOutlookBarPane::RestoreOriginalstate`，但不會觸發重新繪製 Outlook 功能區窗格。  
  
##  <a name="a-namesetextraspacea--cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace  
 設定 Outlook 功能區窗格中的按鈕周圍使用邊框距離的像素數目。  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="a-namesettextcolora--cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor  
 設定 Outlook 功能區窗格中的規則和反白顯示文字的色彩。  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrRegText`  
 指定所選文字的新色彩。  
  
 [in] `clrSelText`  
 指定所選文字的新色彩。  
  
##  <a name="a-namesettransparentcolora--cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor  
 設定 Outlook 功能區窗格的透明色彩。  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 指定新的透明色彩。  
  
### <a name="remarks"></a>備註  
 顯示透明影像所需的透明色彩。 是改為使用的背景色彩繪製此色彩的映像中的任何項目。  沒有任何混合的背景和前景影像。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

