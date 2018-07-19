---
title: CMFCOutlookBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b9de076f4682bd3649f62940a0dd492eb801e28
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850179"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar 類別
具有 Microsoft Outlook 2000 或 Outlook 2003 [ **巡覽窗格** ] 視覺外觀的索引標籤式窗格。 `CMFCOutlookBar`物件包含[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)物件和一系列索引標籤。 索引標籤可以是[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件或`CWnd`-衍生物件。 對於使用者，Outlook 功能區會顯示為一系列按鈕與一個顯示區域。 當使用者按一下按鈕時，對應的控制項或按鈕窗格隨即顯示。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定空的索引標籤式的窗格是否可以終結。 (覆寫[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane)。)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|判斷另一個窗格是否可以固定到 Outlook 功能區窗格。 （覆寫 CDockablePane::CanAcceptPane）。|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。(覆寫[CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname)。)|  
|[CMFCOutlookBar::Create](#create)|建立 Outlook 功能區控制項。|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|建立自訂的 Outlook 列 索引標籤。|  
|`CMFCOutlookBar::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|判斷使用者是否可以停駐控制列在 Outlook 功能區的外邊緣。|  
|[CMFCOutlookBar::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。(覆寫[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|傳回的 Outlook 功能區按鈕的文字的字型。|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|在 Outlook 功能區上傳回的大小和位置 索引標籤區域。 (覆寫[CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea)。)|  
|`CMFCOutlookBar::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|決定是否 Outlook 功能區的行為是模擬的 Microsoft Office Outlook 2003 （請參閱 < 備註 >）。|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)作用中的索引標籤設定使用動畫之後。|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁面設定為使用中 索引標籤，並使用動畫。|  
|[CMFCOutlookBar::OnScroll](#onscroll)|如果 Outlook 功能區可在向上或向下捲動，由架構呼叫。|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|移除自訂的 Outlook 列索引標籤。|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Outlook 功能區按鈕上設定之文字的字型。|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|指定是否 Outlook 功能區的行為是模擬的 Outlook 2003 （請參閱 < 備註 >）。|  
  
## <a name="remarks"></a>備註  
 如需 Outlook 功能區的範例，請參閱 < [OutlookDemo 範例： MFC OutlookDemo 應用程式](../../visual-cpp-samples.md)。  
  
## <a name="implementing-the-outlook-bar"></a>實作 Outlook 功能區  
 若要在您的應用程式中使用 `CMFCOutlookBar` 控制項，請遵循下列步驟：  
  
1.  內嵌 `CMFCOutlookBar` 物件到主框架視窗類別。  
  
    ```cpp
    class CMainFrame : public CMDIFrameWnd  
    { 
        // ...  
        CMFCOutlookBar m_wndOutlookBar;  
        CMFCOutlookBarPane m_wndOutlookPane;  
        // ...
    };  
    ```

2.  當處理主框架內的 WM_CREATE 訊息，呼叫[CMFCOutlookBar::Create](#create)方法用來建立的 Outlook 列的索引標籤控制項。  
  
    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

3.  取得基礎的指標`CMFCOutlookBarTabCtrl`利用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)。  
  
    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```
    
4.  建立[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)包含按鈕的每個索引標籤的物件。  
  
    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);  

    // make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons  
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

5.  呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)加入每個新的索引標籤。設定*bDetachable*參數設為 FALSE 可進行不可中斷連結的頁面。 或者，您也可以使用[CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)將中斷連結的頁面。  
  
    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```  

6.  新增`CWnd`-衍生控制項 (例如[CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)) 索引標籤上，建立控制項並呼叫[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)將它新增至 Outlook 功能區。  
  
> [!NOTE]
>  您應該使用唯一的控制項 Id，每個[CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)物件和每個`CWnd`-衍生物件。  
  
 若要以動態方式新增或刪除新的頁面，在執行階段，請使用[CMFCOutlookBar::CreateCustomPage](#createcustompage)並[CMFCOutlookBar::RemoveCustomPage](#removecustompage)。  
  
## <a name="outlook-2003-mode"></a>Outlook 2003 模式  
 在 Outlook 2003 模式中，索引標籤按鈕位於 Outlook 功能區窗格底部。 當沒有足夠的空間，以顯示按鈕時，它們會顯示為窗格的底端類似工具列的區域中的圖示。  
  
 使用[CMFCOutlookBar::SetMode2003](#setmode2003)來啟用 Outlook 2003 模式。 使用[CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist)設定點陣圖，其中包含會顯示在底部的 outlook 功能區的圖示。 點陣圖中的圖示必須按照定位點索引。  
  
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
  
##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 指定空的索引標籤式的窗格是否可以終結。  
  
```cpp  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果空白，則為 TRUE 才能終結索引標籤式的窗格;否則為 FALSE。 預設實作永遠傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如果無法終結空白的索引標籤式的窗格，架構會隱藏它改為。  
  
##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane  
 判斷另一個窗格是否可以固定到 Outlook 功能區窗格。  
  
```cpp  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*pBar*  
 指標，會停駐此窗格的另一個窗格。  
  
### <a name="return-value"></a>傳回值  
 如果另一個窗格可以固定到 Outlook 功能區窗格;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如果不支援的橫條圖是在 Outlook 2003 模式中，停駐的 Outlook，因此傳回的值為 FALSE。  
  
 如果*pBar*參數為 NULL，這個方法會傳回 FALSE。  
  
 此方法做為基底方法的行為，否則為[cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)，不過，即使未啟用停駐，Outlook 功能區仍然可以啟用以停駐於上方的另一個 outlook 功能區。  
  
##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName  
 決定索引標籤式窗格的標題是否顯示為 [作用中] 索引標籤相同的文字。  
  
```cpp  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果 Outlook 視窗標題列會自動設為 [作用中] 索引標籤; 的文字，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 使用[CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)啟用或停用這項功能。  
  
 在 Outlook 2003 模式中，一律會啟用此設定。  
  
##  <a name="create"></a>  CMFCOutlookBar::Create  
 建立 Outlook 功能區控制項。  
  
```cpp  
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
 [in]*lpszCaption*  
 指定視窗的標題。  
  
 [in]*pParentWnd*  
 指定父視窗的指標。 它必須不是 NULL。  
  
 [in]*rect*  
 指定的大小和位置單位為像素列的 outlook。  
  
 [in]*nID*  
 指定控制項 id。 必須是不同於其他控制項的應用程式中使用的 Id。  
  
 [in]*cheaderctrl:: Create*  
 指定所要的控制項列樣式。 如需可能的值，請參閱[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。  
  
 [in]*dwControlBarStyle*  
 指定特殊的程式庫定義樣式。  
  
 [in]*pContext*  
 建立內容。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CMFCOutlookBar`兩個步驟中的物件。 第一次呼叫建構函式，然後再呼叫`Create`，這會建立 outlook 功能區控制項，並將它附加至`CMFCOutlookBar`物件。  
  
 請參閱[cbasepane:: Createex](../../mfc/reference/cbasepane-class.md#createex)如需可用程式庫定義的樣式所指定的清單*dwControlBarStyle*。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Create`方法的`CMFCOutlookBar`類別。 此程式碼片段是一部分[Outlook 多重檢視範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage  
 建立自訂的 Outlook 列 索引標籤。  
  
```cpp  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszPageName*  
 頁面的標籤。  
  
 [in]*bActivatePage*  
 如果為 TRUE，頁面就會變成作用中，在建立時。  
  
 [in]*dwEnabledDocking*  
 卸離頁面時，請指定已啟用的停駐側邊 CBRS_ALIGN_ 旗標的組合。  
  
 [in]*bEnableTextLabels*  
 如果為 TRUE，會啟用頁面上的按鈕文字標籤。  
  
### <a name="return-value"></a>傳回值  
 新建立的頁面上或如果建立失敗，則為 NULL 指標。  
  
### <a name="remarks"></a>備註  
 使用這個方法，讓使用者可以建立自訂的 Outlook 列頁面。 您可以建立最多 100 個的頁面，每個應用程式。 網頁控制項從 0xF000 識別碼開頭。 如果自訂的 Outlook 列頁面總數超過 100，建立將會失敗。  
  
 使用[CMFCOutlookBar::RemoveCustomPage](#removecustompage)刪除自訂頁面。  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore  
 指定使用者是否可以停駐之外部邊緣的 Outlook 功能區窗格。  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>傳回值  
 預設實作會傳回 FALSE。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`DoesAllowDynInsertBefore`方法尋找要停駐動態窗格的位置時。 如果函式會傳回 FALSE，此架構不允許外部邊緣窗格的任何動態窗格的停駐。  
  
 通常，您可以建立 Outlook 功能區作為靜態非浮動的控制項。 您可以覆寫衍生類別中的此函式，並傳回 TRUE，若要變更此行為。  
  
> [!NOTE]
>  因為動態窗格停駐時，檢查靜態的停駐窗格的狀態，您應該固定動態窗格盡可能的靜態窗格之後。  
  
##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab  
 讓窗格浮動。  
  
```cpp  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>參數  
 [in]*pBar*  
 Float 窗格指標。  
  
 [in]*nTabID*  
 Float 索引標籤的以零為起始的索引。  
  
 [in]*dockMethod*  
 指定要用來讓窗格浮動方法。  如需詳細資訊，請參閱 < [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。  
  
 [in]*bHide*  
 若要隱藏窗格浮動; 之前，則為 TRUE否則為 FALSE。 不同於這個方法的基底類別版本，此參數沒有預設值。  
  
### <a name="return-value"></a>傳回值  
 如果窗格浮動;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 這個方法就像是[cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)不同之處在於它不會啟用最後一個剩餘的索引標籤，在 Outlook 功能區控制項為 float。  
  
##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont  
 傳回文字的字型頁面上的 Outlook 功能區的按鈕索引標籤。  
  
```cpp  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所列的頁面按鈕索引標籤，然後在 Outlook 中顯示文字的字型物件的指標。  
  
### <a name="remarks"></a>備註  
 您可以使用此函式來擷取用來在 Outlook 的頁面按鈕索引標籤上顯示文字的字型。 您可以藉由呼叫上設定的字型[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)。  
  
##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea  
 決定的大小和位置的 Outlook 功能區上的索引標籤區域。  
  
```cpp  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>參數  
 [out]*rectTabAreaTop*  
 函式傳回時，請包含大小和位置 （以工作區座標中） 的最上層索引標籤區域。  
  
 [out]*rectTabAreaBottom*  
 函式傳回時，請包含大小和位置 （以工作區座標中） 下方的索引標籤區域。  
  
### <a name="remarks"></a>備註  
 架構會呼叫這個方法，以判斷停駐到 [目標] 窗格的型別。 當架構判斷使用者拖曳窗格停駐索引標籤區域的 [目標] 窗格時，它會嘗試將第一個窗格新增為新的索引標籤的 [目標] 窗格。 否則，它會嘗試停駐在 [目標] 窗格中適當的一端的第一個窗格。 此架構會建立新的容器，使用滑桿，以容納額外的停駐的窗格。  
  
 預設實作`GetTabArea`傳回整個工作區的 Outlook 功能區，如果 Outlook 功能區是為靜態; 也就是說，如果不能浮動 Outlook 功能區。 否則，它會傳回頁面] 按鈕會取得在頂端和底部的 [Outlook 功能區控制項的區域。  
  
 從衍生類別中置換此方法`CMFCOutlookBar`來變更此行為。  
  
##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003  
 指定是否 Outlook 功能區的行為是模擬的 Microsoft Office Outlook 2003。  
  
```cpp  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Outlook 功能區在 Microsoft Office 2003 模式下執行; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以使用，以啟用此模式[CMFCOutlookBar::SetMode2003](#setmode2003)。  
  
##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)作用中的索引標籤設定使用動畫之後。  
  
```cpp  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [in]*n 版面*  
 已成為作用中的索引標籤頁之以零起始的索引。  
  
### <a name="remarks"></a>備註  
 設定作用中的索引標籤的視覺效果取決於您是否已啟用動畫。 如需詳細資訊，請參閱 < [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)。  
  
##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation  
 由呼叫[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)前一個索引標籤頁面設定為使用中 索引標籤，並使用動畫。  
  
```cpp  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>參數  
 [in]*n 版面*  
 即將設定作用中的索引標籤頁之以零起始的索引。  
  
### <a name="return-value"></a>傳回值  
 傳回如果動畫應使用於設定 [新的作用中] 索引標籤，則為 TRUE 或 FALSE，如果應停用動畫。  
  
### <a name="remarks"></a>備註  
  
##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll  
 如果 Outlook 功能區可在向上或向下捲動，由架構呼叫。  
  
```cpp  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>參數  
 [in]*bDown*  
 如果 Outlook 功能區捲動清單，或如果它向上捲動，則為 FALSE，則為 TRUE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage  
 移除自訂的 Outlook 狀態列 索引標籤頁面。  
  
```cpp  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>參數  
 [in]*之 uiPage*  
 父 Outlook 視窗中頁面的以零為起始的索引。  
  
 [in]*pTargetWnd*  
 Pointerto 父 Outlook 視窗。  
  
### <a name="return-value"></a>傳回值  
 如果已順利移除自訂頁面，非零值。否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式來刪除自訂的頁面。 移除頁面時它的控制項 ID 會傳回至集區的可用的識別碼。  
  
 您必須提供的指標[CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)要移除目前頁面所在的物件。 請注意，使用者可以不同的 Outlook 列之間移動，可以中斷連結的頁面，但自訂頁面的相關資訊位於 Outlook 列物件，您必須呼叫[CMFCOutlookBar::CreateCustomPage](#createcustompage)。  
  
 使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)取得 Outlook 視窗的指標。  
  
##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont  
 Outlook 功能區按鈕上設定之文字的字型。  
  
```cpp  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*pFont*  
 指定新的字型。  
  
 [in]*bRedraw*  
 如果為 TRUE，Outlook 功能區會重新繪製。  
  
### <a name="remarks"></a>備註  
 這個方法可用於設定 [outlook] 索引標籤頁按鈕顯示的文字字型。  
  
##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003  
 指定是否 Outlook 功能區的行為是模擬的 Outlook 2003。  
  
```cpp  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bMode2003*  
 如果為 TRUE，則會啟用 Office 2003 模式。  
  
### <a name="remarks"></a>備註  
 若要啟用或停用 Office 2003 模式中使用此函式。 在此模式中，Outlook 功能區會有額外的工具列具有自訂按鈕。 Outlook 功能區的行為符合在 Microsoft Office 2003 Outlook 功能區的行為。  
  
 根據預設，此模式已停用。  
  
> [!NOTE]
>  此函式必須先呼叫才能[CMFCOutlookBar::Create](#create)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl 類別](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane 類別](../../mfc/reference/cmfcoutlookbarpane-class.md)
