---
title: "CMFCOutlookBar 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCOutlookBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCOutlookBar 類別"
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCOutlookBar 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 \[**巡覽窗格**\] 的視覺外觀的相關的索引窗格在 Microsoft Outlook 2000 或 Outlook 2003 的年份。  `CMFCOutlookBar` 物件包含一個 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) 物件和一系列的選項。  選項可以是 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 物件或 `CWnd`衍生物件。  提供給使用者， Outlook 顯示為一系列按鈕和顯示區域。  當使用者按一下按鈕時，對應的控制項或按鈕窗格隨即顯示。  
  
## 語法  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCOutlookBar::CMFCOutlookBar`|預設建構函式。|  
|`CMFCOutlookBar::~CMFCOutlookBar`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](../Topic/CMFCOutlookBar::AllowDestroyEmptyTabbedPane.md)|指定是否可以終結空的索引窗格。  覆寫 \( [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../Topic/CBaseTabbedPane::AllowDestroyEmptyTabbedPane.md)\)。|  
|[CMFCOutlookBar::CanAcceptPane](../Topic/CMFCOutlookBar::CanAcceptPane.md)|判斷其他窗格是否可以停駐在 Outlook 功能窗格。  \(覆寫 CDockablePane::CanAcceptPane\)。|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](../Topic/CMFCOutlookBar::CanSetCaptionTextToTabName.md)|判斷索引標籤式窗格標題是否顯示文字和作用中的索引標籤相同。  覆寫 \( [CBaseTabbedPane::CanSetCaptionTextToTabName](../Topic/CBaseTabbedPane::CanSetCaptionTextToTabName.md)\)。|  
|[CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md)|建立 Outlook 功能區控制項。|  
|[CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md)|建立自訂 Outlook 功能區索引標籤。|  
|`CMFCOutlookBar::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](../Topic/CMFCOutlookBar::DoesAllowDynInsertBefore.md)|判斷使用者是否可以停駐的控制項列在 Outlook 功能區的外框。|  
|[CMFCOutlookBar::FloatTab](../Topic/CMFCOutlookBar::FloatTab.md)|只有當窗格目前位於一個可拆的選項，浮動窗格，不過，。  覆寫 \( [CBaseTabbedPane::FloatTab](../Topic/CBaseTabbedPane::FloatTab.md)\)。|  
|[CMFCOutlookBar::GetButtonsFont](../Topic/CMFCOutlookBar::GetButtonsFont.md)|傳回文字的字型在 Outlook 功能區按鈕的。|  
|[CMFCOutlookBar::GetTabArea](../Topic/CMFCOutlookBar::GetTabArea.md)|傳回索引標籤區域的大小和位置在 Outlook 功能區。  覆寫 \( [CBaseTabbedPane::GetTabArea](../Topic/CBaseTabbedPane::GetTabArea.md)\)。|  
|`CMFCOutlookBar::GetThisClass`|由框架取得指標與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCOutlookBar::IsMode2003](../Topic/CMFCOutlookBar::IsMode2003.md)|判斷是否在 Microsoft Office Outlook 2003 中 Outlook 功能區仿造物的行為 \(請參閱 \<備註\>\)。|  
|[CMFCOutlookBar::OnAfterAnimation](../Topic/CMFCOutlookBar::OnAfterAnimation.md)|使用動畫，由 [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) 在作用中的索引標籤之後設定。|  
|[CMFCOutlookBar::OnBeforeAnimation](../Topic/CMFCOutlookBar::OnBeforeAnimation.md)|使用動畫，由 [CMFCOutlookBarTabCtrl::SetActiveTab](../Topic/CMFCOutlookBarTabCtrl::SetActiveTab.md) 索引標籤頁上的設定為作用中的索引標籤。|  
|[CMFCOutlookBar::OnScroll](../Topic/CMFCOutlookBar::OnScroll.md)|由架構呼叫，如果 Outlook 中上下移動。|  
|[CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md)|移除自訂 Outlook 功能區索引標籤。|  
|[CMFCOutlookBar::SetButtonsFont](../Topic/CMFCOutlookBar::SetButtonsFont.md)|設定文字的字型在 Outlook 功能區按鈕的。|  
|[CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md)|指定是否要在 Outlook 2003 中 Outlook 功能區仿造物的行為 \(請參閱 \<備註\>\)。|  
  
## 備註  
 如需 Outlook 功能的範例，請參閱 [OutlookDemo 範例:MFC OutlookDemo 應用程式](../../top/visual-cpp-samples.md)。  
  
## 實作 Outlook 功能區  
 若要使用 `CMFCOutlookBar` 控制項在應用程式中，依照下列步驟執行:  
  
1.  內嵌的 `CMFCOutlookBar` 物件插入主框架視窗類別。  
  
    ```  
    class CMainFrame : public CMDIFrameWnd  
     { ...  
         CMFCOutlookBar         m_wndOutlookBar;  
         CMFCOutlookBarPane     m_wndOutlookPane;  
    ... };  
    ```  
  
2.  當處理主框架時的 `WM_CREATE` 訊息，請呼叫 [CMFCOutlookBar::Create](../Topic/CMFCOutlookBar::Create.md) 方法建立 Outlook 功能區索引標籤控制項。  
  
    ```  
    m_wndOutlookBar.Create (_T("Shortcuts"), this, CRect (0, 0, 100, 100), ID_VIEW_OUTLOOKBAR, WS_CHILD | WS_VISIBLE | CBRS_LEFT);  
    ```  
  
3.  使用 [CBaseTabbedPane::GetUnderlyingWindow](../Topic/CBaseTabbedPane::GetUnderlyingWindow.md)，以取得指標至基礎 `CMFCOutlookBarTabCtrl` 。  
  
    ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();  
    ```  
  
4.  建立每個選項的 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 物件中按鈕。  
  
    ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar, AFX_DEFAULT_TOOLBAR_STYLE, ID_OUTLOOK_PANE_GENERAL, AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);  
    // make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);  
    // add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About", ID_APP_ABOUT);  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open", ID_FILE_OPEN);  
    ```  
  
5.  呼叫 [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) 加入每個新的索引標籤。  將 `bDetachable` 參數設定為 `FALSE` 可讓非可拆頁面。  或者，使用 [CMFCOutlookBarTabCtrl::AddControl](../Topic/CMFCOutlookBarTabCtrl::AddControl.md) 將可拆的頁面。  
  
    ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);   
    ```  
  
6.  將 `CWnd`衍生控制項 \(例如， [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)\) 做為選項，建立控制項並呼叫 [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) 加入至 Outlook 功能區。  
  
> [!NOTE]
>  您應該使用唯一的控制項 ID 為每個 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md) 物件並對每個 `CWnd`衍生物件。  
  
 動態加入或刪除新頁面在執行階段、使用 [CMFCOutlookBar::CreateCustomPage](../Topic/CMFCOutlookBar::CreateCustomPage.md) 和 [CMFCOutlookBar::RemoveCustomPage](../Topic/CMFCOutlookBar::RemoveCustomPage.md)。  
  
## Outlook 2003 年模式  
 在 Outlook 2003 年模式下，選項按鈕位於 Outlook 功能窗格的下方。  當沒有足夠的空間顯示按鈕時，它們會顯示為類似工具列區域的圖示顯示窗格的下方。  
  
 使用 [CMFCOutlookBar::SetMode2003](../Topic/CMFCOutlookBar::SetMode2003.md) 啟動 Outlook 2003 年模式。  使用 [CMFCOutlookBarTabCtrl::SetToolbarImageList](../Topic/CMFCOutlookBarTabCtrl::SetToolbarImageList.md) 設定包含圖示會出現在 Outlook 的底端顯示的點陣圖。  必須以定位點索引以點陣圖的圖示。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## 需求  
 **標題:** afxoutlookbar.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane 類別](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane Class](../../mfc/reference/cmfcoutlookbarpane-class.md)