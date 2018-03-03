---
title: "CMFCOutlookBar 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 257b9157059f20d9023abee092c38ad8c1a57167
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 類別
具有 Microsoft Outlook 2000 或 Outlook 2003 [ **巡覽窗格** ] 視覺外觀的索引標籤式窗格。 `CMFCOutlookBar`物件包含[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)物件及一系列的索引標籤。 索引標籤可以是[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件或`CWnd`-衍生物件。 對於使用者，Outlook 功能區會顯示為一系列按鈕與一個顯示區域。 當使用者按一下按鈕時，對應的控制項或按鈕窗格隨即顯示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|預設建構函式。|  
|`CMFCOutlookBar::~CMFCOutlookBar`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以終結空的索引標籤式的窗格。 (覆寫[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)。)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|判斷另一個窗格是否可以固定到 Outlook 功能區窗格。 （覆寫 CDockablePane::CanAcceptPane）。|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。(覆寫[CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)。)|  
|[CMFCOutlookBar::Create](#create)|建立 Outlook 列控制項。|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|建立自訂的 Outlook 列索引標籤。|  
|`CMFCOutlookBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|決定使用者是否可以停駐控制列在 outlook 功能區上緣。|  
|[CMFCOutlookBar::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。(覆寫[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Outlook 功能區按鈕上傳回的文字字型。|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|傳回的大小和位置 索引標籤區域的 outlook 功能區。 (覆寫[CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。)|  
|`CMFCOutlookBar::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|決定是否 outlook 功能區的行為會模擬的 Microsoft Office Outlook 2003 （請參閱 < 備註 >）。|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)之後已設定使用中的索引標籤使用的動畫。|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁會設定為使用中的索引標籤使用的動畫。|  
|[CMFCOutlookBar::OnScroll](#onscroll)|如果向上或向下捲動 outlook 功能區，由架構呼叫。|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|移除自訂 Outlook 列索引標籤。|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|設定 outlook 功能區按鈕的文字字型。|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|指定是否 outlook 功能區的行為會模擬，Outlook 2003 （請參閱 < 備註 >）。|  
  
## <a name="remarks"></a>備註  
 如需 outlook 功能區的範例，請參閱[OutlookDemo 範例： MFC OutlookDemo 應用程式](../../visual-cpp-samples.md)。  
  
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
2.  處理時`WM_CREATE`主框架呼叫的訊息[CMFCOutlookBar::Create](#create)方法來建立索引標籤控制項列 Outlook。  
  
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
3.  取得基礎指標`CMFCOutlookBarTabCtrl`使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。  
  
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
5.  呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)新增每個新的索引標籤。設定`bDetachable`參數`FALSE`進行非中斷連結的頁面。 或者，使用[CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)新增中斷連結的頁面。  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  新增`CWnd`-衍生控制項 (例如， [CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)) 索引標籤上，建立控制項，然後呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)將它加入至 outlook 功能區。  
  
> [!NOTE]
>  您應該使用唯一的控制項 Id，每個[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件以及對於每個`CWnd`-衍生物件。  
  
 若要以動態方式加入或刪除新的頁面，在執行階段，請使用[CMFCOutlookBar::CreateCustomPage](#createcustompage)和[CMFCOutlookBar::RemoveCustomPage](#removecustompage)。  
  
## <a name="outlook-2003-mode"></a>Outlook 2003 模式  
 在 Outlook 2003 模式中，索引標籤按鈕位於 Outlook 功能區窗格的底部。 當沒有足夠空間來顯示按鈕時，它們會顯示為沿著底部窗格的工具列類似的區域中的圖示。  
  
 使用[CMFCOutlookBar::SetMode2003](#setmode2003)啟用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)設定點陣圖，其中包含會顯示在底部 outlook 功能區的圖示。 必須定位點索引來排序在點陣圖中的圖示。  
  
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
 **標頭：** afxoutlookbar.h  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 指定是否可以終結空的索引標籤式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以終結空的索引標籤式的窗格。否則， `FALSE`。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 如果無法終結空的索引標籤式的窗格，架構會隱藏它改為。  
  
##  <a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane  
 判斷另一個窗格是否可以固定到 Outlook 功能區窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 正在停駐此窗格的另一個窗格的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 Outlook 功能區窗格; 停駐的另一個窗格，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果 outlook 功能區，在 Outlook 2003 模式中停駐不支援，因此傳回值是`FALSE`。  
  
 如果`pBar`參數是`NULL`，這個方法會傳回`FALSE`。  
  
 否則，這個方法的行為如同基底方法[cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)，不過，即使未啟用停駐，outlook 功能區仍然可以啟用要透過它停駐的另一個 outlook 功能區。  
  
##  <a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName  
 決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 Outlook 視窗標題列會自動設定為使用中的索引標籤; 的文字否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用[CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)啟用或停用這項功能。  
  
 在 Outlook 2003 模式中，永遠會啟用此設定。  
  
##  <a name="create"></a>CMFCOutlookBar::Create  
 建立 Outlook 列控制項。  
  
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
 [輸入] `lpszCaption`  
 指定的視窗標題。  
  
 [輸入] `pParentWnd`  
 指定的父視窗的指標。 它不得為 NULL。  
  
 [輸入] `rect`  
 指定軸的大小和位置單位為像素 outlook。  
  
 [輸入] `nID`  
 指定控制項 id。 必須與其他控制項的應用程式中使用的 Id 不同。  
  
 [輸入] `dwStyle`  
 指定所要的控制項列樣式。 可能的值，請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 [輸入] `dwControlBarStyle`  
 指定特殊的程式庫定義樣式。  
  
 [輸入] `pContext`  
 建立內容。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 您建構`CMFCOutlookBar`兩個步驟中的物件。 第一次呼叫建構函式，然後再呼叫`Create`，建立 outlook 列控制項，並將它附加至`CMFCOutlookBar`物件。  
  
 請參閱[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)的清單，以指定可用程式庫定義樣式`dwControlBarStyle`。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法`CMFCOutlookBar`類別。 此程式碼片段是部分[Outlook 多重檢視範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage  
 建立自訂的 Outlook 列索引標籤。  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszPageName`  
 頁面的標籤。  
  
 [輸入] `bActivatePage`  
 如果`TRUE`，頁面會變成作用中，在建立時。  
  
 [輸入] `dwEnabledDocking`  
 卸離頁面時，指定已啟用的停駐邊 CBRS_ALIGN_ 旗標的組合。  
  
 [輸入] `bEnableTextLabels`  
 如果`TRUE`，啟用頁面上的按鈕文字標籤。  
  
### <a name="return-value"></a>傳回值  
 指標，新建的頁面上，或`NULL`如果建立失敗。  
  
### <a name="remarks"></a>備註  
 使用這個方法，讓使用者可以建立自訂 Outlook 列頁面。 您可以建立每個應用程式最多 100 個的頁面。 網頁控制項識別碼從 0xF000 啟動。 如果自訂 Outlook 列頁的總數超過 100，建立將會失敗。  
  
 使用[CMFCOutlookBar::RemoveCustomPage](#removecustompage)刪除自訂頁面。  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore  
 指定使用者是否可以停駐窗格中的，在 outlook 功能區上緣。  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回 `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`DoesAllowDynInsertBefore`方法尋找停駐動態窗格的位置時。 如果此函數會傳回`FALSE`，架構不允許在外部邊緣窗格的任何動態窗格的停駐。  
  
 通常，您可建立 outlook 功能區做為靜態的非浮點控制。 您可以覆寫這個函式在衍生類別中的，並傳回`TRUE`來變更此行為。  
  
> [!NOTE]
>  因為動態窗格停駐時，請檢查靜態的停駐窗格的狀態，應該將動態窗格停駐之後盡可能靜態窗格。  
  
##  <a name="floattab"></a>CMFCOutlookBar::FloatTab  
 讓窗格浮動。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 Float 窗格指標。  
  
 [輸入] `nTabID`  
 浮動索引標籤以零為起始的索引。  
  
 [輸入] `dockMethod`  
 指定要用來讓窗格浮動方法。  如需詳細資訊，請參閱[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。  
  
 [輸入] `bHide`  
 `TRUE`若要隱藏窗格之前浮點數;否則， `FALSE`。 不同於這個方法的基底類別版本，此參數沒有預設值。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格浮動;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法就像[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)不同之處在於它不會啟用為 float Outlook 控制項上最後一個剩餘的索引標籤。  
  
##  <a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont  
 傳回文字的字型頁面上的 outlook 功能區按鈕索引標籤。  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用來在 Outlook 中顯示文字，頁面按鈕索引標籤列字型物件的指標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來擷取用來在 Outlook 頁面按鈕索引標籤上顯示文字的字型。 您可以藉由呼叫上設定的字型[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)。  
  
##  <a name="gettabarea"></a>CMFCOutlookBar::GetTabArea  
 決定的大小和 outlook 功能區上的索引標籤區域的位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 包含此函數會傳回的大小和位置 （用戶端座標中） 的最上層索引標籤區域。  
  
 [輸出] `rectTabAreaBottom`  
 包含此函數會傳回的大小和位置 （用戶端座標中） 下方的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以判斷目標窗格停駐的型別。 當架構判斷使用者拖曳要透過索引標籤區域的 [目標] 窗格停駐窗格時，它會嘗試將第一個窗格新增為新的索引標籤的 [目標] 窗格。 否則，它會嘗試停駐在 [目標] 窗格中適當的一端的第一個窗格。 架構會建立新的容器，使用滑桿來容納額外的停駐的窗格。  
  
 預設實作`GetTabArea`傳回整個工作區的 outlook 功能區，outlook 功能區是否為靜態; 也就是說，如果不能浮動 outlook 功能區。 否則，它會傳回頁面按鈕採取頂端和底部的 Outlook 狀態列控制項的區域。  
  
 從衍生類別中置換此方法`CMFCOutlookBar`來變更此行為。  
  
##  <a name="ismode2003"></a>CMFCOutlookBar::IsMode2003  
 指定 outlook 功能區的行為與內容的 Microsoft Office Outlook 2003 相似。  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果 outlook 功能區以 Microsoft Office 2003 模式執行。否則便是 0。  
  
### <a name="remarks"></a>備註  
 您可以使用，以啟用此模式[CMFCOutlookBar::SetMode2003](#setmode2003)。  
  
##  <a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)之後已設定使用中的索引標籤使用的動畫。  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nPage`  
 索引標籤頁已成為作用中以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 設定作用中的索引標籤的視覺效果取決於您是否已啟用動畫。 如需詳細資訊，請參閱[CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。  
  
##  <a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁會設定為使用中的索引標籤使用的動畫。  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nPage`  
 設定作用中的索引標籤頁的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 傳回`TRUE`動畫應使用於設定新的使用中索引標籤中，如果或`FALSE`如果應該停用動畫。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onscroll"></a>CMFCOutlookBar::OnScroll  
 如果向上或向下捲動 outlook 功能區，由架構呼叫。  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bDown`  
 `TRUE`如果捲動 outlook 功能區，或`FALSE`如果它向上捲動。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage  
 移除自訂 Outlook 列索引標籤頁。  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiPage`  
 父 Outlook 視窗中頁面的以零為起始的索引。  
  
 [輸入] `pTargetWnd`  
 Pointerto 父 Outlook 視窗。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功; 移除自訂頁面否則便是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可刪除自訂頁面。 移除頁面時其控制項 ID 會傳回至集區的可用的識別碼。  
  
 您必須提供的指標[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)中要移除目前頁面所在的物件。 請注意，使用者可以不同的 Outlook 橫條之間移動中斷連結的頁面，但自訂頁面的相關資訊位於您所呼叫的 Outlook 列物件[CMFCOutlookBar::CreateCustomPage](#createcustompage)。  
  
 使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)取得 Outlook 視窗的指標。  
  
##  <a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont  
 設定 outlook 功能區按鈕的文字字型。  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pFont`  
 指定新的字型。  
  
 [輸入] `bRedraw`  
 如果`TRUE`，將會重繪 outlook 功能區。  
  
### <a name="remarks"></a>備註  
 使用這個方法來設定 outlook 索引標籤頁按鈕上顯示的文字字型。  
  
##  <a name="setmode2003"></a>CMFCOutlookBar::SetMode2003  
 指定是否 outlook 功能區的行為會模擬，Outlook 2003。  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bMode2003`  
 如果為 TRUE，則會啟用 Office 2003 模式。  
  
### <a name="remarks"></a>備註  
 若要啟用或停用 Office 2003 模式中使用此函式。 在此模式中，outlook 功能區會有額外的工具列具有自訂按鈕。 在 Microsoft Office 2003 outlook 功能區的行為符合 outlook 功能區的行為。  
  
 根據預設，此模式已停用。  
  
> [!NOTE]
>  之前必須先呼叫此函式[CMFCOutlookBar::Create](#create)。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)
