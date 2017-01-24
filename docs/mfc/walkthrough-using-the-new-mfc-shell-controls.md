---
title: "逐步解說：使用新的 MFC Shell 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shell 控制項 (MFC)"
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：使用新的 MFC Shell 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在此逐步解說中，您會建立類似 Windows 檔案總管的應用程式。  您會建立包含兩個窗格的視窗。  左側的窗格含有 [CMFCShellTreeCtrl](../mfc/reference/cmfcshelltreectrl-class.md) 物件，此物件能以階層式檢視顯示您的桌面。  右側的窗格含有 [CMFCShellListCtrl](../mfc/reference/cmfcshelllistctrl-class.md)，此物件能顯示在左側窗格中選取之資料夾內的檔案。  
  
## 必要條件  
 這個逐步解說假設您已設定 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 使用 \[**一般開發設定**\]。  如果您使用不同的開發設定，一些此逐步解說使用的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 視窗可能預設為無法顯示。  
  
### 若要使用 MFC 應用程式精靈建立新的 MFC 應用程式  
  
1.  使用 \[**MFC 應用程式精靈**\] 建立新的 MFC 應用程式  從 \[**檔案**\] 功能表中選取 \[**新增**\] 以執行精靈，，然後選取 \[**專案**\]。  \[**新增專案**\] 對話方塊隨即出現。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開 \[**Project types**\] 窗格的 \[**Visual C\+\+**\] 節點，並選取 \[**MFC**\]。  在 \[**範本**\] 窗格中選取 \[**MFC 應用程式**\]。  輸入專案名稱，例如 `MFCShellControls` 並按一下 \[**確定**\]。  \[**MFC 應用程式精靈**\] 隨即出現。  
  
3.  在 \[**MFC 應用程式精靈**\] 對話方塊中按 \[**下一步**\]。  \[**應用程式類型**\] 窗格隨即顯示。  
  
4.  在 \[**應用程式類型**\] 窗格中，在 \[**應用程式類型**\] 下，清除 \[**具有標籤的文件**\] 選項。  然後選取 \[**單一文件**\] 並選取 \[**文件\/檢視架構支援**\]。  在 \[**專案樣式**\] 下選取 \[**Visual Studio**\]，然後從 \[**視覺化樣式和色彩。**\] 下拉式清單選取 \[**Office 2007 \(藍色佈景主題\)**\]。  保留其他選項為原本的值。  按一下 \[**下一個**\] 以顯示 \[**複合文件支援**\] 窗格。  
  
5.  在 \[**複合文件支援**\] 窗格中，選取 \[**無**\]。  按一下 \[**下一個**\] 以顯示 \[**文件樣板字串**\] 窗格。  
  
6.  不要對 \[**文件樣板字串**\] 窗格作任何變更。  按一下 \[**下一個**\] 以顯示 \[**資料庫支援**\] 窗格。  
  
7.  在 \[**資料庫支援**\] 窗格中，請選取 \[**無**\] ，因為這個應用程式不使用資料庫。  按一下 \[**下一個**\] 以顯示 \[**使用者介面功能**\] 窗格。  
  
8.  在 \[**使用者介面功能**\] 窗格中，確定已選取 \[**使用功能表列和工具列**\] 選項。  保留其他選項為原本的值。  按一下 \[**下一個**\] 以顯示 \[**進階功能**\] 窗格。  
  
9. 在 \[**進階功能**\] 窗格中，在 \[**進階功能**\] 底下，只選取 \[**ActiveX 控制項**\] 和 \[**通用控制項資訊清單**\]。  在 \[**進階框架窗格**\] 底下，只選取 \[**巡覽窗格**\] 選項。  這會使精靈建立已內嵌 `CMFCShellTreeCtrl` 的視窗左側窗格。  按一下 \[**下一個**\] 以顯示 \[**產生的類別**\] 窗格。  
  
10. 我們不會對 \[**產生的類別**\] 窗格作任何變更。  因此，按一下 \[**結束**\] 以建立新的 MFC 專案。  
  
11. 建置並執行應用程式，以確認應用程式建立成功。  若要建置應用程式，請從 \[**建置**\] 功能表中選取 \[**建置方案**\]。  如果應用程式建置成功，請從 \[**偵錯**\] 功能表上選取 \[**開始偵錯**\] 以執行應用程式。  
  
     精靈會自動建立具有標準功能表列、標準工具列、一個標準狀態列和一個 Outlook 列在視窗左側並加上 \[**資料夾**\] 檢視和 \[**行事曆**\] 檢視的應用程式。  
  
### 若要將殼層清單控制項加入至文件檢視  
  
1.  在本章節中，您會將 `CMFCShellListCtrl` 執行個體加入至精靈所建立的檢視。  您可以按兩下 \[**方案總管**\] 中的 MFCShellControlsView.h 開啟檢視標頭檔。  
  
     在標頭檔頂端附近找出 `#pragma once` 指示詞。  在其正下方加入用以包含 `CMFCShellListCtrl`標頭檔的程式碼:  
  
    ```  
    #include <afxShellListCtrl.h>  
    ```  
  
     現在加入 `CMFCShellListCtrl` 型別的成員變數。  首先，請於標頭檔找出下列註解:  
  
    ```  
    // Generated message map functions  
    ```  
  
     於該註解之上加入這段程式碼:  
  
    ```  
    private:  
        CMFCShellListCtrl m_wndList;  
    ```  
  
2.  \[**MFC 應用程式精靈**\] 已建立 `CMainFrame` 類別的 `CMFCShellTreeCtrl` 物件，不過，它是一個受保護的成員。  我們稍後會存取這個物件。  因此，現在請建立其存取子。  您可以在 \[**方案總管**\] 按兩下 MainFrm.h 以開啟標頭檔。  尋找下列註解：  
  
    ```  
    // Attributes  
    ```  
  
     於正下方，加入下列方法宣告:  
  
    ```  
    public:  
        CMFCShellTreeCtrl& GetShellTreeCtrl();  
    ```  
  
     接著，您可以於 \[**方案總管**\] 按兩下 MainFrm.cpp 以開啟原始程式檔。  在該檔案中的下方，加入下列方法定義:  
  
    ```  
    CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()  
    {  
        return m_wndTree;  
    }  
    ```  
  
3.  現在我們更新 `CMFCShellControlsView` 類別以處理 **WM\_CREATE** 視窗訊息。  開啟 MFCShellControlsView.h 標頭檔並按一下這一行程式碼:  
  
    ```  
    class CMFCShellControlsView : public CView  
    ```  
  
     接下來，在 \[**屬性**\] 視窗中，按一下 \[**訊息**\] 圖示。  向下捲動，直到您找到 **WM\_CREATE** 訊息。  從 **WM\_CREATE**旁的下拉清單中，選取 \[**\<Add\> OnCreate**\]。  這會為我們建立訊息處理常式並自動更新 MFC 訊息對應。  
  
     在 `OnCreate` 方法我們現在會建立我們的 `CMFCShellListCtrl` 物件。  於 MFCShellControlsView.cpp 原始程式檔尋找 `OnCreate` 方法定義，並以下列程式碼取代它的實作:  
  
    ```  
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)  
    {  
        if (CView::OnCreate(lpCreateStruct) == -1)  
            return -1;  
  
        CRect rectDummy (0, 0, 0, 0);  
        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,  
            rectDummy, this, 1);  
  
        return 0;  
    }  
    ```  
  
4.  為 **WM\_SIZE** 訊息重複上述步驟。  這會導致您的應用程式每當使用者變更應用程式視窗的大小時重新繪製。  以下列程式碼取代 `OnSize` 方法定義：  
  
    ```  
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,  
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);  
    }  
    ```  
  
5.  最後一個步驟是使用 [CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md) 方法連接 `CMFCShellTreeCtrl` 和 `CMFCShellListCtrl` 物件。  在呼叫這個方法之後， `CMFCShellListCtrl` 會自動顯示在 `CMFCShellTreeCtrl`中選取之項目的內容。  我們將在覆寫自 [CView::OnActivateView](../Topic/CView::OnActivateView.md) 的 `OnActivateView` 方法中做這項動作。  
  
     在 MFCShellControlsView.h 標頭檔， `CMFCShellControlsView` 類別宣告中，加入下列方法宣告:  
  
    ```  
    protected:  
        virtual void OnActivateView(BOOL bActivate,  
            CView* pActivateView,  
            CView* pDeactiveView);  
    ```  
  
     接下來，將這個方法的定義加入 MFCShellControlsView.cpp 原始程式檔:  
  
    ```  
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,  
        CView* pActivateView,  
        CView* pDeactiveView)   
    {  
        if (bActivate && AfxGetMainWnd() != NULL)  
        {  
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);  
        }  
  
        CView::OnActivateView(bActivate, pActivateView, pDeactiveView);  
    }  
    ```  
  
     由於我們從 `CMainFrame` 呼叫方法，我們必須將 `#include` 指示詞加到 MFCShellControlsView.cpp 原始程式檔的上方:  
  
    ```  
    #include "MainFrm.h"  
    ```  
  
6.  建置並執行應用程式，以確認應用程式建立成功。  若要建置應用程式，請從 \[**建置**\] 功能表中選取 \[**建置方案**\]。  如果應用程式建置成功，請選擇 \[**偵錯**\] 功能表上的 \[**開始偵錯**\] 以執行應用程式。  
  
     您現在應該會在檢視窗格中的 `CMFCShellTreeCtrl` 查看所選取的項目的詳細資料。  當您按一下 `CMFCShellTreeCtrl`中的節點，便會自動更新 `CMFCShellListCtrl` 。  同樣地，如果您按兩下 `CMFCShellListCtrl`中的資料夾，應該會自動更新 `CMFCShellTreeCtrl` 。  
  
     以滑鼠右鍵按一下任何樹狀目錄控制項或清單控制項的項目。  請注意您會得到相同的內容功能表，就像您正在使用真正的檔案總管。  
  
## 後續步驟  
  
-   精靈會建立具有 \[**資料夾**\] 窗格和 \[**行事曆**\] 窗格中的 Outlook 功能區。  這可能沒有必要在總管視窗顯示 \[**行事曆**\] 窗格。  因此，現在請移除該窗格。  
  
-   `CMFCShellListCtrl` 支援以不同的方式檢視檔案，例如 \[**大圖示**\]、 \[**小圖示**\]、 \[**清單**\] 和 \[**詳細資料**\]。  更新您的應用程式以實作這項功能。  提示:請參閱 [Visual C\+\+ 範例](../top/visual-cpp-samples.md)。  
  
## 請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)