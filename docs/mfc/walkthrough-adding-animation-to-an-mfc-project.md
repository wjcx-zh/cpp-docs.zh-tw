---
title: 逐步解說：將動畫加入至 MFC 專案
ms.date: 04/25/2019
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
ms.openlocfilehash: 07b0c5f712cd645246ecfb4e8c93543377a340a3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558194"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>逐步解說：將動畫加入至 MFC 專案

本逐步解說將說明如何將基本的動畫的物件新增至視覺效果C++，Microsoft Foundation Class 程式庫 (MFC) 專案。

本逐步解說示範如何完成這些工作：

- 建立 MFC 應用程式。

- 加入功能表，然後新增命令以啟動和停止動畫。

- 建立用於啟動和停止命令處理常式。

- 將動畫的物件加入至專案。

- 置中視窗中動畫的物件。

- 驗證結果。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

### <a name="to-create-an-mfc-application"></a>若要建立 MFC 應用程式

1. 使用**MFC 應用程式精靈**建立 MFC 應用程式。 請參閱[逐步解說：使用新的 MFC Shell 控制項](walkthrough-using-the-new-mfc-shell-controls.md)如需有關如何開啟您的 Visual Studio 版本的精靈。

1. 在 **名稱**方塊中，輸入*MFCAnimationWalkthrough*。 按一下 [確定] 。

1. 在  **MFC 應用程式精靈**對話方塊方塊中，確認**應用程式類型**會**多份文件**，**專案樣式**是**Visual Studio**，而**文件/檢視架構支援**選項。 按一下 [ **完成**]。

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>若要新增的功能表，然後新增命令來啟動和停止的動畫

1. 在 **檢視**功能表上，指向**其他 Windows** ，然後按一下 **資源檢視**。

1. 在 **資源檢視**，瀏覽至**功能表**資料夾並將它開啟。 按兩下**IDR_MFCAnimationWalkthroughTYPE**以開啟它進行修改的資源。

1. 在功能表列上，在**在這裡輸入**方塊中，輸入*a&nimation*建立 [動畫] 功能表。

1. 底下**動畫**，請在**這裡輸入**方塊中，輸入*開始，& 轉送*建立 Start Forward 命令。

1. 底下**Start Forward**，請在**這裡輸入**方塊中，輸入*開始] 與 [向後*。

1. 底下**Start Backward**，請在**這裡輸入**方塊中，輸入*s&top*建立停止命令。

1. 儲存 MFCAnimationWalkthrough.rc 並關閉它。

1. 在 [**方案總管] 中**，連按兩下以開啟它進行修改的 MainFrm.cpp。 在 `CMainFrame::OnCreate`方法中，找出具有數個呼叫的區段`lstBasicCommands.AddTail`。 只在該區段中之後, 新增下列程式碼。

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. 儲存檔案，並將它關閉。

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>建立處理常式的開始和停止命令

1. 在 **專案**功能表上，按一下**類別精靈**。

1. 在  **MFC 類別精靈**下方**類別名稱**，選取**CMFCAnimationWalkthroughView**。

1. 在上**命令**索引標籤**物件識別碼**方塊中，選取**ID_ANIMATION_STARTFORWARD**，然後在**訊息**方塊中，選取**命令**。 按一下 **加入處理常式**。

1. 在 [**加入成員函式**] 對話方塊中，按一下**確定**。

1. 在 **的物件識別碼**方塊中，選取**ID_ANIMATION_STARTBACKWARD**，然後在**訊息**方塊中，選取**命令**。 按一下 **加入處理常式**。

1. 在 [**加入成員函式**] 對話方塊中，按一下**確定**。

1. 在 **的物件識別碼**方塊中，選取**ID_ANIMATION_STOP**，然後在**訊息**方塊中，選取**命令**。 按一下 **加入處理常式**，然後按一下**確定**。

1. 在 [**加入成員函式**] 對話方塊中，按一下**確定**。

1. 在  **MFC 類別精靈**，按一下**確定**。

1. 儲存 MFCAnimationWalkthroughView.cpp，也就是在編輯器中開啟，但請不要關閉它。

### <a name="to-add-an-animated-object-to-the-project"></a>將動畫的物件加入至專案

1. 在 [**方案總管] 中**，連按兩下以開啟它進行修改的 MFCAnimationWalkthroughView.h。 之前的定義`CMFCAnimationWalkthroughView`類別中，新增下列程式碼，建立自訂動畫控制器會處理與動畫物件的排程衝突。

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. 在結尾`CMFCAnimationWalkthroughView`類別中，新增下列程式碼。

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. 之後`DECLARE_MESSAGE_MAP()`行，加入下列程式碼。

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. 儲存檔案，並將它關閉。

1. 在 MFCAnimationWalkthroughView.cpp，在後檔案的頂端`#include`陳述式但任何類別方法，才會加入下列程式碼。

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. 建構函式的結尾`CMFCAnimationWalkthroughView`，新增下列程式碼。

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. 找出`CAnimationWalthroughView::PreCreateWindow`方法，然後將其取代為下列程式碼。

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. 找出`CAnimationWalkthroughView::OnDraw`方法，然後將其取代為下列程式碼。

    ```cpp
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
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. 在檔案結尾，加入下列程式碼。

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. 在 **專案**功能表上，按一下**類別精靈**。

1. 在  **MFC 類別精靈**下方**類別名稱**，選取**CMFCAnimationWalkthroughView**。

1. 在上**訊息**索引標籤**訊息**方塊中，選取**WM_ERASEBKGND**，按一下 **加入處理常式**，然後按一下  **確定**.

1. 在 MFCAnimationWalkthroughView.cpp，取代的實作`OnEraseBkgnd`下列的程式碼，以減少閃爍動畫的物件中，會重繪時。

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. 取代的實作`CMFCAnimationWalkthroughView::OnAnimationStartforward`， `CMFCAnimationWalkthroughView::OnAnimationStartbackward`，和`CMFCAnimationWalkthroughView::OnAnimationStop`為下列程式碼。

    ```cpp
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

1. 儲存檔案，並將它關閉。

### <a name="to-center-the-animated-object-in-the-window"></a>若要置 視窗中動畫的物件

1. 在 [**方案總管] 中**，連按兩下以開啟它進行修改的 MFCAnimationWalkthroughView.h。 在結尾`CMFCAnimationWalkthroughView`類別的定義之後，只要`m_animationRect`，新增下列程式碼。

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. 儲存檔案，並將它關閉。

1. 在 **專案**功能表上，按一下**類別精靈**。

1. 在  **MFC 類別精靈**下方**類別名稱**，選取**CMFCAnimationWalkthroughView**。

1. 在上**訊息**索引標籤**訊息**方塊中，選取**WM_SIZE**，按一下 **加入處理常式**，然後按一下  **確定**.

1. 在 MFCAnimationWalkthroughView.cpp，取代的程式碼`CMFCAnimationWalkthroughView::OnSize`為下列程式碼。

    ```cpp
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

1. 建構函式的開頭`CMFCAnimationWalkthroughView`，新增下列程式碼。

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. 在開頭`CMFCAnimationWalkthroughView::Animate`方法中，新增下列程式碼。

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. 儲存檔案，並將它關閉。

### <a name="to-verify-the-results"></a>若要確認結果

1. 建置並執行應用程式。 在 **動畫**功能表上，按一下**Start Forward**。 矩形應該會出現，然後填入 中間區域。 當您按一下  **Start Backward**，都應該反轉動畫，當您按一下**停止**，應該會停止。 填滿矩形的色彩應該變更動畫進行時，和目前色彩應顯示在 [動畫] 視窗的頂端。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)
