---
title: CMFCOutlookBarPane 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd073dc7876a755a8dc309efc7e11fb63521ab5a
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037898"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane 類別
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 衍生控制項[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)，可插入 outlook 功能區 ( [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md))。 Outlook 功能區窗格包含一欄大型按鈕。 如果按鈕清單比窗格還要大，使用者可以上下捲動清單。 當使用者將 Outlook 功能區窗格從 Outlook 功能區卸離時，這個窗格可以在主框架視窗中停駐或浮動。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|預設建構函式。|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|將按鈕加入至 Outlook 功能區窗格。|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|決定是否窗格可以停駐於另一個窗格或框架視窗。 (覆寫[CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)。)|  
|`CMFCOutlookBarPane::CanBeRestored`|決定是否系統可以還原工具列到其原始狀態後自訂。 (覆寫[CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)。)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|釋出 Outlook 功能區窗格中的影像所使用的資源。|  
|[CMFCOutlookBarPane::Create](#create)|建立 Outlook 功能區窗格。|  
|`CMFCOutlookBarPane::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCOutlookBarPane::Dock`|由架構呼叫以將 Outlook 功能區窗格停駐。 (覆寫 `CPane::Dock`。)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|指定是否 Outlook 功能區窗格上的捲軸箭號 頁面上，或 按鈕前進按鈕的清單。|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|傳回 Outlook 功能區窗格的規則 （非選取） 的文字色彩。|  
|`CMFCOutlookBarPane::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|判斷是否載入 Outlook 功能區窗格的背景影像。|  
|`CMFCOutlookBarPane::IsChangeState`|判斷是否可能會停駐浮動窗格。 (覆寫 `CPane::IsChangeState`。)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|判斷當按鈕會反白顯示，並顯示背景影像時，是否加上陰影按鈕框線。|  
|`CMFCOutlookBarPane::OnBeforeFloat`|窗格即將 float 時由架構呼叫。 (覆寫[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|移除擁有指定的命令識別碼的按鈕|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|還原工具列的原始狀態。 (覆寫[CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)。)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|設定背景色彩。|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|設定背景影像。|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|將 Outlook 功能區窗格重設原始的按鈕集合。|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|設定周圍 Outlook 功能區窗格中的按鈕所使用的填補的像素數目。|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Outlook 功能區窗格中設定規則和反白顯示的文字的色彩。|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|設定 Outlook 功能區窗格的透明色彩。|  
|`CMFCOutlookBarPane::SmartUpdate`|內部用來更新 outlook 功能區。 (覆寫 `CMFCToolBar::SmartUpdate`。)|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|指定的快顯功能表項目會顯示在自訂模式。|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|從 Outlook 功能區窗格移除所有的按鈕。 (覆寫[CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)。)|  
  
## <a name="remarks"></a>備註  
 如需如何實作 outlook 功能區的資訊，請參閱[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 如需 outlook 功能區的範例，請參閱 OutlookDemo 範例專案。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法`CMFCOutlookBarPane`類別。 此範例示範如何建立 Outlook 功能區窗格，啟用頁面捲軸模式、 啟用停駐，以及設定 outlook 功能區的背景色彩。 此程式碼片段是部分[Outlook 多重檢視範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
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
 **標頭：** afxoutlookbarpane.h  
  
##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton  
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
 [in]*uiImage*  
 指定點陣圖的資源識別碼。  
  
 [in]*lpszLabel*  
 指定按鈕的文字。  
  
 [in]*iIdCommand*  
 指定按鈕控制項的 id。  
  
 [in]*iInsertAt*  
 要插入按鈕 outlook 功能區的頁面上指定的以零為起始的索引。  
  
 [in]*uiLabel*  
 字串資源 id。  
  
 [in]*szBmpFileName*  
 指定要載入之磁碟映像檔案名稱。  
  
 [in]*szLabel*  
 指定按鈕的文字。  
  
 [in]*hBmp*  
 點陣圖按鈕的控制代碼。  
  
 [in]*hIcon*  
 按鈕的圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果成功; 加入按鈕否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法，將新的按鈕插入 outlook 功能區的頁面。 可以載入按鈕的影像，從應用程式資源或磁碟檔案。  
  
 如果所指定的頁面識別碼*uiPageID*為-1，按鈕會插入第一頁。  
  
 如果指定的索引*iInsertAt*為-1，按鈕就會加入結尾的頁面。  
  
##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll  
 釋出 Outlook 功能區窗格上的映像所使用的資源。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會直接呼叫[CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)，Outlook 功能區窗格所使用的映像上呼叫它。  
  
##  <a name="create"></a>  CMFCOutlookBarPane::Create  
 建立 Outlook 功能區窗格。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>參數  
 [in]*pParentWnd*  
 指定 Outlook 狀態列窗格控制項的父視窗。 必須不是 `NULL`。  
  
 [in]*dwStyle*  
 視窗樣式。  如需視窗樣式的清單，請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 [in]*uiID*  
 控制項 id。 必須是唯一啟用儲存控制項的狀態。  
  
 [in]*dwControlBarStyle*  
 指定特殊從 outlook 功能區卸離時，定義行為的 Outlook 狀態列窗格控制項的樣式。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果該方法成功。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 若要建構`CMFCOutlookBarPane`物件、 第一次呼叫建構函式，並接著呼叫`Create`，建立的 Outlook 列窗格控制項，並將它附加至`CMFCOutlookBarPane`物件。  
  
 如需有關`dwControlBarStyle`看到[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)。  
  
##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems  
 指定的快顯功能表項目會顯示在自訂模式。  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>參數  
 [in]*pButton*  
 工具列按鈕，使用者按下指標。  
  
 [in]*pPopup*  
 指標的捷徑功能表。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果快顯功能表應該顯示，否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以修改 framework 顯示在自訂模式中的 framework 標準的捷徑功能表。  
  
 預設實作會檢查自訂模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))，如果設定為`TRUE`，停用所有的快顯功能表項目除外**刪除**。 然後，它只會傳遞的輸入的參數`CMFCToolBar::EnableContextMenuItems`。  
  
> [!NOTE]
> *內容功能表*是快顯功能表的同義字。  
  
##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode  
 指定捲軸上的箭號 Outlook 功能區窗格是否前進逐頁或按鈕的按鈕的按鈕的清單。  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bPageScroll*  
 如果`TRUE`，啟用頁面捲動模式。 如果`FALSE`，停用頁面捲動模式。  
  
##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor  
 一般會傳回 (也就是未選取) Outlook 功能區窗格的文字色彩。  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值為目前的文字色彩。  
  
### <a name="remarks"></a>備註  
 使用[CMFCOutlookBarPane::SetTextColor](#settextcolor)設定 outlook 功能區的目前 （規則並已選取） 的文字色彩。 您可以藉由呼叫取得預設文字色彩[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)函式與`COLOR_WINDOW`索引。  
  
##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture  
 判斷是否載入 Outlook 功能區窗格的背景影像。  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果沒有要顯示; 的背景影像否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 您可以加入背景影像，藉由呼叫[CMFCOutlookBarPane::SetBackImage](#setbackimage)函式。  
  
 如果沒有任何背景影像，以使用指定的色彩繪製背景[CMFCOutlookBarPane::SetBackColor](#setbackcolor)。  
  
##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight  
 判斷當按鈕會反白顯示，並顯示背景影像時，是否加上陰影按鈕框線。  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果按鈕的框線會呈現灰色。否則`FALSE`。  
  
##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons  
 從 Outlook 功能區窗格移除所有的按鈕。  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton  
 移除擁有指定的命令識別碼的按鈕  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>參數  
 [in]*iIdCommand*  
 指定要移除按鈕的命令識別碼。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果成功移除 按鈕。`FALSE`如果指定的命令 ID 無效。  
  
##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor  
 設定 outlook 功能區的背景色彩。  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in]*色彩*  
 指定新的背景色彩。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可設定 outlook 功能區目前的背景色彩。 只有在沒有任何背景影像，會使用背景色彩。  
  
##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage  
 設定背景影像。  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiImageID*  
 指定影像資源識別碼。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以設定 [Outlook] 列的背景影像。 受管理的背景影像清單是透過內嵌[CMFCToolBarImages 類別](../../mfc/reference/cmfctoolbarimages-class.md)物件。  
  
##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState  
 將 Outlook 功能區窗格重設原始的按鈕集合。  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>備註  
 這個方法會 Outlook 列按鈕還原原始的集合。 這個方法就像`CMFCOutlookBarPane::RestoreOriginalstate`，不同之處在於它不會觸發重新繪製的 Outlook 功能區窗格。  
  
##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace  
 設定周圍 Outlook 功能區窗格中的按鈕所使用的填補的像素數目。  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor  
 Outlook 功能區窗格中設定規則和反白顯示的文字的色彩。  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>參數  
 [in]*clrRegText*  
 指定新的未選取文字色彩。  
  
 [in]*clrSelText*  
 指定新的選取文字色彩。  
  
##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor  
 設定 Outlook 功能區窗格的透明色彩。  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 *色彩*  
 指定新的透明色彩。  
  
### <a name="remarks"></a>備註  
 顯示透明影像所需的透明色彩。 此色彩的映像中的任何項目而繪製以背景色彩。  沒有任何的混合，其背景和前景影像。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
