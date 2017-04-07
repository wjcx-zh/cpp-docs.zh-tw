---
title: "CMFCOutlookBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar class
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ff58cf786e4979d64aa2b5d7ad4d1a32b96bec3d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 類別
具有 Microsoft Outlook 2000 或 Outlook 2003 [ **巡覽窗格** ] 視覺外觀的索引標籤式窗格。 `CMFCOutlookBar`物件包含[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)物件和一系列的索引標籤。 索引標籤可以是[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件或`CWnd`-衍生物件。 對於使用者，Outlook 功能區會顯示為一系列按鈕與一個顯示區域。 當使用者按一下按鈕時，對應的控制項或按鈕窗格隨即顯示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|預設建構函式。|  
|`CMFCOutlookBar::~CMFCOutlookBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以終結空白的索引標籤式的窗格。 (覆寫[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)。)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|判斷另一個窗格是否可停駐於 Outlook 功能區窗格。 （覆寫 CDockablePane::CanAcceptPane）。|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。 (覆寫[CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)。)|  
|[CMFCOutlookBar::Create](#create)|建立 Outlook 功能區控制項。|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|建立自訂的 Outlook 列 索引標籤。|  
|`CMFCOutlookBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|決定使用者是否可以停駐控制列在 outlook 功能區上緣。|  
|[CMFCOutlookBar::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。 (覆寫[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|傳回文字的字型，outlook 功能區按鈕上。|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Outlook 功能區上傳回的大小和位置 索引標籤區域。 (覆寫[CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。)|  
|`CMFCOutlookBar::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|決定是否 outlook 功能區的行為會模擬的 Microsoft Office Outlook 2003 （請參閱 < 備註 >）。|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)之後已設定使用中的索引標籤使用動畫。|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁面設定為使用中 索引標籤，並使用動畫。|  
|[CMFCOutlookBar::OnScroll](#onscroll)|如果可以使用向上或向下捲動 outlook 功能區，由架構呼叫。|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|移除自訂的 Outlook 列 索引標籤。|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Outlook 功能區按鈕上設定之文字的字型。|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|指定是否 outlook 功能區的行為會模擬，Outlook 2003 （請參閱 < 備註 >）。|  
  
## <a name="remarks"></a>備註  
 如需 outlook 功能區的範例，請參閱[OutlookDemo 範例︰ MFC OutlookDemo 應用程式](../../visual-cpp-samples.md)。  
  
## <a name="implementing-the-outlook-bar"></a>實作 outlook 功能區  
 若要在您的應用程式中使用 `CMFCOutlookBar` 控制項，請遵循下列步驟：  
  
1.  內嵌 `CMFCOutlookBar` 物件到主框架視窗類別。  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
2.  處理時`WM_CREATE`訊息在主框架中，呼叫[CMFCOutlookBar::Create](#create)方法來建立 Outlook 列 索引標籤控制項。  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
3.  取得基礎的指標`CMFCOutlookBarTabCtrl`使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  建立[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)包含按鈕的每個索引標籤的物件。  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
5.  呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)加入每個新的索引標籤。 設定`bDetachable`參數`FALSE`產生非分離的網頁。 或者，使用[CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)新增分離的頁面。  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  新增`CWnd`-衍生控制項 (例如， [CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)) 索引標籤中，建立控制項，然後呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)將它加入至 outlook 功能區。  
  
> [!NOTE]
>  您應該使用唯一的控制項 Id，每個[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件和每個`CWnd`-衍生物件。  
  
 若要以動態方式加入或刪除新的頁面，在執行階段，使用[CMFCOutlookBar::CreateCustomPage](#createcustompage)和[CMFCOutlookBar::RemoveCustomPage](#removecustompage)。  
  
## <a name="outlook-2003-mode"></a>Outlook 2003 模式  
 在 Outlook 2003 模式中，索引標籤按鈕位於 Outlook 功能區窗格的底部。 當沒有足夠的空間，以顯示按鈕時，沿著窗格底部的工具列類似的區域中的圖示會顯示它們。  
  
 使用[CMFCOutlookBar::SetMode2003](#setmode2003)來啟用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)設定包含會顯示在底部的 outlook 功能區的圖示的點陣圖。 必須以定位點索引來排序在點陣圖中的圖示。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxoutlookbar.h  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 指定是否可以終結空白的索引標籤式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以終結空白的索引標籤式的窗格。否則， `FALSE`。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 如果無法終結空白的索引標籤式的窗格，架構會隱藏它改為。  
  
##  <a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane  
 判斷另一個窗格是否可停駐於 Outlook 功能區窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 指標，另一個窗格，並停駐到這個窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 Outlook 功能區窗格; 停駐的另一個窗格，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果 outlook 功能區是 Outlook 2003 模式下，停駐並不支援，因此傳回值是`FALSE`。  
  
 如果`pBar`參數是`NULL`，這個方法會傳回`FALSE`。  
  
 否則，這個方法會做為基底方法運作[CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)，不過，即使未啟用停駐，outlook 功能區仍然可以啟用嗎停駐到另一個 outlook 功能區。  
  
##  <a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName  
 決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果視窗標題列 Outlook 會自動設為 [作用中] 索引標籤; 文字否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)啟用或停用這項功能。  
  
 在 Outlook 2003 模式中，一定會啟用此設定。  
  
##  <a name="create"></a>CMFCOutlookBar::Create  
 建立 Outlook 功能區控制項。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszCaption`  
 指定視窗標題。  
  
 [in] `pParentWnd`  
 指定的父視窗的指標。 它不得為 NULL。  
  
 [in] `rect`  
 指定的大小和位置單位為像素列 outlook。  
  
 [in] `nID`  
 指定控制項 id。 必須是不同於其他控制項的應用程式中使用的 Id。  
  
 [in] `dwStyle`  
 指定所要的控制項列樣式。 可能的值，請參閱[視窗樣式](../../mfc/reference/window-styles.md)。  
  
 [in] `dwControlBarStyle`  
 指定特殊的程式庫定義樣式。  
  
 [in] `pContext`  
 建立內容。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CMFCOutlookBar`兩個步驟中的物件。 第一次呼叫建構函式，然後再呼叫`Create`，其建立 outlook 功能區控制項，並將它附加`CMFCOutlookBar`物件。  
  
 請參閱[CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex)依指定的可用程式庫定義樣式清單`dwControlBarStyle`。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法`CMFCOutlookBar`類別。 此程式碼片段是一部分[Outlook 多重檢視範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews #&1;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews #&2;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage  
 建立自訂的 Outlook 列 索引標籤。  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszPageName`  
 頁面標籤。  
  
 [in] `bActivatePage`  
 如果`TRUE`，頁面就會成為作用時建立。  
  
 [in] `dwEnabledDocking`  
 卸離頁面時，指定已啟用的停駐邊 CBRS_ALIGN_ 旗標的組合。  
  
 [in] `bEnableTextLabels`  
 如果`TRUE`，啟用頁面上的按鈕文字標籤。  
  
### <a name="return-value"></a>傳回值  
 新建立的頁面上，指標或`NULL`如果建立失敗。  
  
### <a name="remarks"></a>備註  
 使用這個方法，讓使用者可以建立自訂 Outlook 列頁面。 您可以建立每個應用程式的最多 100 個頁面。 網頁控制項從 0xF000 啟動識別碼。 如果自訂 Outlook 列分頁的總數超過 100，建立將會失敗。  
  
 使用[CMFCOutlookBar::RemoveCustomPage](#removecustompage)刪除自訂頁面。  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore  
 指定使用者是否可以停駐窗格在 outlook 功能區上緣。  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`DoesAllowDynInsertBefore`方法時，它會尋找要停駐動態窗格的位置。 如果此函數會傳回`FALSE`，架構不允許在外部邊緣窗格的任何動態窗格的停駐。  
  
 通常，您可以建立 outlook 功能區做為靜態的非浮點控制。 您可以覆寫這個函式在衍生類別中的，並傳回`TRUE`來變更此行為。  
  
> [!NOTE]
>  由於動態窗格檢查靜態的停駐窗格的狀態停駐時，您應該盡可能靜態窗格之後固定動態窗格。  
  
##  <a name="floattab"></a>CMFCOutlookBar::FloatTab  
 浮動窗格。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 Float 窗格指標。  
  
 [in] `nTabID`  
 Float 索引標籤的以零為起始的索引。  
  
 [in] `dockMethod`  
 指定要用來進行的窗格中的浮點數的方法。  如需詳細資訊，請參閱[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。  
  
 [in] `bHide`  
 `TRUE`若要隱藏窗格之前浮點數。否則， `FALSE`。 不同於這個方法的基底類別版本，此參數沒有預設值。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果浮動窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法就像[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)不同之處在於它不會啟用為 float Outlook 功能區控制項上最後一個剩餘的索引標籤。  
  
##  <a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont  
 傳回文字的字型頁面上的 outlook 功能區按鈕索引標籤。  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用來在 Outlook 中顯示文字，頁面的按鈕索引標籤列字型物件的指標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來擷取用來在 Outlook 頁面按鈕索引標籤上顯示文字的字型。 您可以藉由呼叫上設定的字型[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)。  
  
##  <a name="gettabarea"></a>CMFCOutlookBar::GetTabArea  
 決定的大小和 outlook 功能區上的索引標籤區域位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 函式傳回時，包含大小和位置 （以工作區座標中） 上的索引標籤區域。  
  
 [輸出] `rectTabAreaBottom`  
 函式傳回時，包含大小和位置 （以工作區座標中） 下方的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以判斷停駐 [目標] 窗格中的型別。 當架構，以決定使用者拖曳窗格停駐 [目標] 窗格的索引標籤區域上時，它會嘗試將第一個窗格新增為新的索引標籤的 [目標] 窗格。 否則，則會停駐在 [目標] 窗格中適當的一端的第一個窗格。 架構會建立新的容器使用滑動軸來容納額外的停駐的窗格。  
  
 預設實作`GetTabArea`傳回整個工作區的 outlook 功能區，outlook 功能區是否為靜態; 也就是說，如果不能浮動 outlook 功能區。 否則，它會傳回 按鈕會在頂端和底部的 Outlook 功能區控制項的區域。  
  
 從衍生類別中的，這個方法會覆寫`CMFCOutlookBar`來變更此行為。  
  
##  <a name="ismode2003"></a>CMFCOutlookBar::IsMode2003  
 指定是否 outlook 功能區的行為會模擬的 Microsoft Office Outlook 2003。  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果 outlook 功能區以 Microsoft Office 2003 模式執行。否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以啟用這個模式使用[CMFCOutlookBar::SetMode2003](#setmode2003)。  
  
##  <a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)之後已設定使用中的索引標籤使用動畫。  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nPage`  
 已成為作用中 索引標籤頁面的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 設定作用中的索引標籤的視覺效果取決於您是否已啟用動畫。 如需詳細資訊，請參閱[CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。  
  
##  <a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁面設定為使用中 索引標籤，並使用動畫。  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nPage`  
 設定作用中的索引標籤頁面以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`如果動畫應用於設定新的作用中 索引標籤，或`FALSE`如果動畫應該停用。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onscroll"></a>CMFCOutlookBar::OnScroll  
 如果可以使用向上或向下捲動 outlook 功能區，由架構呼叫。  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>參數  
 [in] `bDown`  
 `TRUE`如果 outlook 功能區時，向下捲動或`FALSE`如果它向上捲動。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage  
 移除自訂的 Outlook 列 索引標籤頁面。  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiPage`  
 父 Outlook 視窗中頁面的以零為起始的索引。  
  
 [in] `pTargetWnd`  
 Pointerto 父 Outlook 視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功，已移除 [自訂] 頁面上，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來刪除自訂頁面。 當頁面已移除其控制項 ID 傳回到集區的可用的識別碼。  
  
 您必須提供一個指向[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)要移除目前頁面所在的物件。 請注意，使用者可以不同的 Outlook 橫條之間移動分離的頁面，但自訂頁面的詳細資訊位於 Outlook 列物件，您已經呼叫[CMFCOutlookBar::CreateCustomPage](#createcustompage)。  
  
 使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)取得 Outlook 視窗的指標。  
  
##  <a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont  
 Outlook 功能區按鈕上設定之文字的字型。  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pFont`  
 指定新的字型。  
  
 [in] `bRedraw`  
 如果`TRUE`，outlook 功能區將會重新繪製。  
  
### <a name="remarks"></a>備註  
 使用這個方法來設定 outlook 索引標籤 按鈕上顯示的文字字型。  
  
##  <a name="setmode2003"></a>CMFCOutlookBar::SetMode2003  
 指定是否 outlook 功能區的行為會模擬，Outlook 2003。  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMode2003`  
 如果為 TRUE，則會啟用 Office 2003 模式。  
  
### <a name="remarks"></a>備註  
 若要啟用或停用 Office 2003 模式使用此函式。 在此模式中，outlook 功能區會有額外的工具列，包含自訂按鈕。 Outlook 功能區的行為符合 Microsoft Office 2003 outlook 功能區的行為。  
  
 根據預設，這個模式會停用。  
  
> [!NOTE]
>  必須先呼叫此函式[CMFCOutlookBar::Create](#create)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)

