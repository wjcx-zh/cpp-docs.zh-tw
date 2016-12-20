---
title: "逐步解說：將動畫加入至 MFC 專案 | Microsoft Docs"
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
  - "動畫 [MFC]"
  - "MFC, 動畫"
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將動畫加入至 MFC 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本逐步解說教導如何將基本動畫物件加入至 Visual C\+\+ MFC 程式庫專案。  
  
 逐步解說將示範如何完成這些工作：  
  
-   建立 MFC 應用程式。  
  
-   加入功能表，然後加入命令以啟動及停止動畫。  
  
-   建立啟動及停止命令的處理常式。  
  
-   將動畫物件加入至專案。  
  
-   在視窗中將動畫物件置中。  
  
-   驗證結果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## 必要條件  
 若要完成這個逐步解說，您必須具有Visual Studio。  
  
### 若要建立 MFC 應用程式  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開左窗格中 \[**已安裝的範本**\] 底下的 \[**Visual C\+\+**\]，然後選取 \[**MFC**\]。  在中間窗格中選取 \[**MFC 應用程式**\]。  在 \[**名稱**\] 方塊中輸入 `MFCAnimationWalkthrough`。  按一下 \[**確定**\]。  
  
3.  在 \[**MFC 應用程式精靈**\] 對話方塊中，驗證 \[**應用程式類型**\] 是 \[**多份文件**\]、\[**專案樣式**\] 是 \[**Visual Studio**\]，而且 \[**支援文件\/檢視架構**\] 選項已選取。  按一下 \[**完成**\]。  
  
### 若要加入功能表，然後加入命令以啟動及停止動畫  
  
1.  指向 \[**檢視**\] 功能表上的 \[**其他視窗**\]，然後按一下 \[**資源檢視**\]。  
  
2.  在 \[**資源檢視**\] 中，巡覽至 \[**功能表**\] 資料夾並開啟它。  按兩下 `IDR_MFCAnimationWalTYPE` 資源，開啟它進行修改。  
  
3.  在功能表列的 \[**在這裡輸入**\] 的方塊中，輸入 `A&nimation` 以建立 \[Animation\] 功能表。  
  
4.  在 \[**Animation**\] 底下的 \[**在這裡輸入**\] 的方塊中，輸入 `Start &Forward` 以建立 \[Start Forward\] 命令。  
  
5.  在 \[**Start Forward**\] 底下的 \[**在這裡輸入**\] 的方塊中，輸入 `Start &Backward`。  
  
6.  在 \[**Start Backward**\] 底下的 \[**在這裡輸入**\] 的方塊中，輸入 `S&top` 以建立 \[Stop\] 命令。  
  
7.  儲存並關閉 MFCAnimationWalkthrough.rc。  
  
8.  按兩下 \[**方案總管**\] 中的 MainFrm.cpp，開啟它進行修改。  在 `CMainFrame::OnCreate` 方法中，尋找具有數個對 `lstBasicCommands.AddTail` 之呼叫的區段。  緊接在該區段之後，加入下列程式碼。  
  
    ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);  
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);  
    ```  
  
9. 儲存並關閉檔案。  
  
### 若要建立啟動及停止命令的處理常式  
  
1.  在 \[**專案**\] 功能表上按一下 \[**類別精靈**\]。  
  
2.  在 \[**MFC 類別精靈**\] 中，選取 \[**類別名稱**\] 底下的 `CMFCAnimationWalkthroughView`。  
  
3.  在 \[**命令**\] 索引標籤上，在 \[**物件 ID**\] 方塊中選取 `ID_ANIMATION_STARTFORWARD`，然後在 \[**訊息**\] 方塊中選取 `COMMAND`。  按一下 \[**加入處理常式**\]。  
  
4.  在 \[**新增成員函式**\] 對話方塊中，按一下 \[**確定**\]。  
  
5.  在 \[**物件 ID**\] 方塊中選取 `ID_ANIMATION_STARTBACKWARD`，然後在 \[**訊息**\] 方塊中選取 `COMMAND`。  按一下 \[**加入處理常式**\]。  
  
6.  在 \[**新增成員函式**\] 對話方塊中，按一下 \[**確定**\]。  
  
7.  在 \[**物件 ID**\] 方塊中選取 `ID_ANIMATION_STOP`，然後在 \[**訊息**\] 方塊中選取 `COMMAND`。  按一下 \[**加入處理常式**\]，然後按一下 \[**確定**\]。  
  
8.  在 \[**新增成員函式**\] 對話方塊中，按一下 \[**確定**\]。  
  
9. 在 \[**MFC 類別精靈**\] 中，按一下 \[**確定**\]。  
  
10. 儲存編輯器中開啟的 MFCAnimationWalkthroughView.cpp，但不要關閉它。  
  
### 若要將動畫物件加入至專案  
  
1.  在 \[方案總管\] 中按兩下 MFCAnimationWalkthroughView.h，開啟它進行修改。  在 `CMFCAnimationWalkthroughView` 類別定義之前，加入下列程式碼，以建立將處理動畫物件排程衝突的自訂動畫控制器。  
  
    ```  
    class CCustomAnimationController : public CAnimationController  
    {  
    public:  
        CCustomAnimationController()  
        {  
        }  
  
        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled, CAnimationGroup* pGroupNew, UI_ANIMATION_PRIORITY_EFFECT priorityEffect)  
        {  
            return TRUE;  
        }  
    };  
    ```  
  
2.  在 `CMFCAnimationWalkthroughView` 類別的結尾加入下列程式碼。  
  
    ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
    ```  
  
3.  在 `DECLARE_MESSAGE_MAP()` 程式碼行之後加入下列程式碼。  
  
    ```  
    void Animate(BOOL bDirection);  
    ```  
  
4.  儲存並關閉檔案。  
  
5.  在 MFCAnimationWalkthroughView.cpp 檔案頂端 `#include` 陳述式之後但在任何類別方法之前，加入下列程式碼。  
  
    ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
    ```  
  
6.  在 `CMFCAnimationWalkthroughView` 的建構函式結尾，加入下列程式碼。  
  
    ```  
    m_animationController.EnableAnimationTimerEventHandler();  
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);  
  
    m_animationColor = RGB(255, 255, 255);  
    m_animationRect = CRect(0, 0, 0, 0);  
  
    m_animationColor.SetID(-1, nAnimationGroup);  
    m_animationRect.SetID(-1, nAnimationGroup);  
  
    m_animationController.AddAnimationObject(&m_animationColor);  
    m_animationController.AddAnimationObject(&m_animationRect);  
    ```  
  
7.  找到 `CAnimationWalthroughView::PreCreateWindow` 方法，然後以下列程式碼取代。  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
    {  
        // TODO: Modify the Window class or styles here by modifying  
        //  the CREATESTRUCT cs  
  
        m_animationController.SetRelatedWnd(this);  
        return CView::PreCreateWindow(cs);  
    }  
    ```  
  
8.  找到 `CAnimationWalkthroughView::OnDraw` 方法，然後以下列程式碼取代。  
  
    ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
    {  
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();  
        ASSERT_VALID(pDoc);  
        if (!pDoc)  
            return;  
  
        // TODO: add draw code for native data here  
        CMemDC dcMem(*pDC, this);  
        CDC& dc = dcMem.GetDC();  
  
        CRect rect;  
        GetClientRect(rect);  
  
        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));  
  
        CString strRGB;  
        strRGB.Format(_T("Fill Color is: %d; %d; %d"), GetRValue(m_animationColor), GetGValue(m_animationColor), GetBValue(m_animationColor));  
  
        dc.DrawText(strRGB, rect, DT_CENTER);  
        rect.top += nInfoAreaHeight;  
  
        CBrush br;  
  
        br.CreateSolidBrush(m_animationColor);  
        CBrush* pBrushOld = dc.SelectObject(&br);  
  
        dc.Rectangle((CRect)m_animationRect);  
        dc.SelectObject(pBrushOld);  
    }  
    ```  
  
9. 在檔案結尾加入下列程式碼。  
  
    ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
    {  
        static UI_ANIMATION_SECONDS duration = 3;  
        static DOUBLE dblSpeed = 35.;  
        static BYTE nStartColor = 50;  
        static BYTE nEndColor = 255;  
  
        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;  
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;  
  
        CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);  
        CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);  
        CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);  
  
        m_animationColor.AddTransition(pRedTransition, pGreenTransition, pBlueTransition);  
  
        CRect rectClient;  
        GetClientRect(rectClient);  
        rectClient.top += nInfoAreaHeight;  
  
        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;  
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;  
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;  
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;  
  
        CLinearTransition* pLeftTransition = new CLinearTransition(duration, nLeftFinal);  
        CLinearTransition* pTopTransition = new CLinearTransition(duration, nTopFinal);  
        CLinearTransition* pRightTransition = new CLinearTransition(duration, nRightFinal);  
        CLinearTransition* pBottomTransition = new CLinearTransition(duration, nBottomFinal);  
  
        m_animationRect.AddTransition(pLeftTransition, pTopTransition, pRightTransition, pBottomTransition);  
  
        CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();  
        CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup, pBlueTransition);  
  
        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);  
  
        m_animationController.AnimateGroup(nAnimationGroup);  
    }  
    ```  
  
10. 在 \[**專案**\] 功能表上按一下 \[**類別精靈**\]。  
  
11. 在 \[**MFC 類別精靈**\] 中，選取 \[**類別名稱**\] 底下的 `CMFCAnimationWalkthroughView`。  
  
12. 在 \[**訊息**\] 索引標籤的 \[**訊息**\] 方塊中，選取 `WM_ERASEBKGND`，按一下 \[**加入處理常式**\]，然後按一下 \[**確定**\]。  
  
13. 在 MFCAnimationWalkthroughView.cpp 中，以下列程式碼取代 `OnEraseBkgnd` 的實作，減少重繪動畫物件時發生的閃動問題。  
  
    ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
    {  
        return TRUE;  
    }  
    ```  
  
14. 以下列程式碼取代 `CMFCAnimationWalkthroughView::OnAnimationStartforward`、`CMFCAnimationWalkthroughView::OnAnimationStartbackward` 和 `CMFCAnimationWalkthroughView::OnAnimationStop` 的實作。  
  
    ```  
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()  
    {  
        Animate(TRUE);  
    }  
  
    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()  
    {  
        Animate(FALSE);  
    }  
  
    void CMFCAnimationWalkthroughView::OnAnimationStop()  
    {  
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();  
        if (pManager != NULL)  
        {  
            pManager->AbandonAllStoryboards();  
        }  
    }  
  
    ```  
  
15. 儲存並關閉檔案。  
  
### 若要在視窗中將動畫物件置中  
  
1.  在 \[**方案總管**\] 中按兩下 MFCAnimationWalkthroughView.h，開啟它進行修改。  在 `CMFCAnimationWalkthroughView` 類別的結尾，`m_animationRect` 定義之後加入下列程式碼。  
  
    ```  
    BOOL m_bCurrentDirection;  
    ```  
  
2.  儲存並關閉檔案。  
  
3.  在 \[**專案**\] 功能表上按一下 \[**類別精靈**\]。  
  
4.  在 \[**MFC 類別精靈**\] 中，選取 \[**類別名稱**\] 底下的 `CMFCAnimationWalkthroughView`。  
  
5.  在 \[**訊息**\] 索引標籤的 \[**訊息**\] 方塊中，選取 `WM_SIZE`，按一下 \[**加入處理常式**\]，然後按一下 \[**確定**\]。  
  
6.  在 MFCAnimationWalkthroughView.cpp 中，以下列程式碼取代 `CMFCAnimationWalkthroughView::OnSize` 的程式碼。  
  
    ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)  
    {  
        CView::OnSize(nType, cx, cy);  
  
        CRect rect;  
        GetClientRect(rect);  
        rect.top += nInfoAreaHeight;  
  
        CRect rectAnim = m_animationRect;  
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,   
                                rect.CenterPoint().y - rectAnim.Height() / 2),   
                                rectAnim.Size());  
  
        if (m_animationController.IsAnimationInProgress())  
        {  
            Animate(m_bCurrentDirection);  
        }  
    }  
    ```  
  
7.  在 `CMFCAnimationWalkthroughView` 的建構函式開頭，加入下列程式碼。  
  
    ```  
    m_bCurrentDirection = TRUE;  
    ```  
  
8.  在 `CMFCAnimationWalkthroughView::Animate` 方法的開頭加入下列程式碼。  
  
    ```  
    m_bCurrentDirection = bDirection;  
    ```  
  
9. 儲存並關閉檔案。  
  
### 若要驗證結果  
  
1.  建置並執行應用程式。  在 \[**Animation**\] 功能表上，按一下 \[**Start Forward**\]。  矩形應該會出現，然後填滿中心區域。  當您按一下 \[**Start Backward**\] 時動畫應該會反轉，按一下 \[**Stop**\] 時動畫應該會停止。  矩形的填滿色彩應該會隨著動畫進展而變更，而且目前色彩應該會顯示在動畫視窗頂端。  
  
## 請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)