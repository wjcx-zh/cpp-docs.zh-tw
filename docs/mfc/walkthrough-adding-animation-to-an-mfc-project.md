---
title: 逐步解說： 將動畫加入至 MFC 專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8ae7496daf6827a6be7769d60af10bca45f7a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>逐步解說：將動畫加入至 MFC 專案
本逐步解說教導如何將基本的動畫的物件加入至 Visual c + +，Microsoft Foundation 類別庫 (MFC) 專案。  
  
 本逐步解說示範如何完成這些工作：  
  
-   建立 MFC 應用程式。  
  
-   加入 功能表，然後再加入 命令來啟動及停止動畫。  
  
-   建立啟動和停止的處理常式。  
  
-   將動畫的物件加入至專案。  
  
-   Center 視窗中的動畫物件。  
  
-   驗證結果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您必須具有 Visual Studio。  
  
### <a name="to-create-an-mfc-application"></a>若要建立 MFC 應用程式  
  
1.  在 [ **檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。  
  
2.  在**新專案**對話方塊中的，在左窗格中**已安裝的範本**，依序展開**Visual c + +** ，然後選取  **MFC**。 在中間窗格中，選取**MFC 應用程式**。 在 [名稱] 方塊中，輸入 `MFCAnimationWalkthrough`。 按一下 [確定 **Deploying Office Solutions**]。  
  
3.  在**MFC 應用程式精靈**對話方塊方塊中，確認**應用程式類型**是**多份文件**，**專案樣式**是**Visual Studio**，而**文件/檢視架構支援**選取選項。 按一下 [ **完成**]。  
  
### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>若要加入功能表，然後再加入命令來啟動及停止動畫  
  
1.  在**檢視**功能表上，指向**其他視窗**，然後按一下 **資源檢視**。  
  
2.  在**資源檢視**，瀏覽至**功能表**資料夾，然後開啟它。 按兩下`IDR_MFCAnimationWalTYPE`以開啟檔案進行修改的資源。  
  
3.  在功能表列上，在**在這裡輸入**方塊中，輸入`A&nimation`若要建立動畫功能表。  
  
4.  在下**動畫**，請在**在這裡輸入**方塊中，輸入`Start &Forward`建立 [Start Forward] 命令。  
  
5.  在下**Start Forward**，請在**在這裡輸入**方塊中，輸入`Start &Backward`。  
  
6.  在下**Start Backward**，請在**在這裡輸入**方塊中，輸入`S&top`建立停止命令。  
  
7.  儲存 MFCAnimationWalkthrough.rc 並關閉它。  
  
8.  在**方案總管 中**，連按兩下以開啟檔案進行修改的 MainFrm.cpp。 在`CMainFrame::OnCreate`方法中，找出區段具有數個呼叫`lstBasicCommands.AddTail`。 只在該區段中之後, 加入下列程式碼。  
  
 ```  
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);

 lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);

    lstBasicCommands.AddTail(ID_ANIMATION_STOP);

 ```  
  
9. 儲存檔案並關閉它。  
  
### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>建立處理常式的開始和停止命令  
  
1.  在**專案**功能表上，按一下 **類別精靈**。  
  
2.  在**MFC 類別精靈**下**類別名稱**，選取`CMFCAnimationWalkthroughView`。  
  
3.  在**命令**索引標籤的**物件識別碼**方塊中，選取`ID_ANIMATION_STARTFORWARD`，然後在**訊息**方塊中，選取`COMMAND`。 按一下**加入處理常式**。  
  
4.  在**加入成員函式**對話方塊中，按一下 **確定**。  
  
5.  在**物件識別碼**方塊中，選取`ID_ANIMATION_STARTBACKWARD`，然後在**訊息**方塊中，選取`COMMAND`。 按一下**加入處理常式**。  
  
6.  在**加入成員函式**對話方塊中，按一下 **確定**。  
  
7.  在**物件識別碼**方塊中，選取`ID_ANIMATION_STOP`，然後在**訊息**方塊中，選取`COMMAND`。 按一下**加入處理常式**，然後按一下 **確定**。  
  
8.  在**加入成員函式**對話方塊中，按一下 **確定**。  
  
9. 在**MFC 類別精靈**，按一下 **確定**。  
  
10. 儲存 MFCAnimationWalkthroughView.cpp，也就是在編輯器中開啟，但不是會將它關閉。  
  
### <a name="to-add-an-animated-object-to-the-project"></a>將動畫的物件加入至專案  
  
1.  在 [方案總管] 中，按兩下 MFCAnimationWalkthroughView.h 以開啟檔案進行修改。 之前的定義`CMFCAnimationWalkthroughView`類別中，加入下列程式碼中建立自訂動畫控制處理與動畫物件的排程衝突。  
  
 ```  
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
  
2.  在結尾`CMFCAnimationWalkthroughView`類別中，加入下列程式碼。  
  
 ```  
    CCustomAnimationController m_animationController;  
    CAnimationColor m_animationColor;   
    CAnimationRect m_animationRect;  
 ```  
  
3.  之後`DECLARE_MESSAGE_MAP()`行，加入下列程式碼。  
  
 ```  
    void Animate(BOOL bDirection);

 ```  
  
4.  儲存檔案並關閉它。  
  
5.  在 MFCAnimationWalkthroughView.cpp 後, 檔案頂端`#include`陳述式但任何類別方法之前, 加入下列程式碼。  
  
 ```  
    static int nAnimationGroup = 0;  
    static int nInfoAreaHeight = 40;  
 ```  
  
6.  建構函式的結尾`CMFCAnimationWalkthroughView`，加入下列程式碼。  
  
 ```  
    m_animationController.EnableAnimationTimerEventHandler();
m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);

 
    m_animationColor = RGB(255,
    255,
    255);

    m_animationRect = CRect(0,
    0,
    0,
    0);

 
    m_animationColor.SetID(-1,
    nAnimationGroup);

    m_animationRect.SetID(-1,
    nAnimationGroup);

 
    m_animationController.AddAnimationObject(&m_animationColor);

 m_animationController.AddAnimationObject(&m_animationRect);

 ```  
  
7.  找出`CAnimationWalthroughView::PreCreateWindow`方法，然後將它取代為下列程式碼。  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)  
 { *// TODO: Modify the Window class or styles here by modifying *//  the CREATESTRUCT cs  
 
    m_animationController.SetRelatedWnd(this);

 return CView::PreCreateWindow(cs);

 }  
 ```  
  
8.  找出`CAnimationWalkthroughView::OnDraw`方法，然後將它取代為下列程式碼。  
  
 ```  
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)  
 {  
    CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
ASSERT_VALID(pDoc);

 if (!pDoc)  
    return; 
 *// TODO: add draw code for native data here  
    CMemDC dcMem(*pDC,
    this);

    CDC& dc = dcMem.GetDC();

 
    CRect rect;  
    GetClientRect(rect);

 
    dc.FillSolidRect(rect,
    GetSysColor(COLOR_WINDOW));

 
    CString strRGB;  
    strRGB.Format(_T("Fill Color is: %d; %d; %d"),
    GetRValue(m_animationColor),
    GetGValue(m_animationColor),
    GetBValue(m_animationColor));

 
    dc.DrawText(strRGB,
    rect,
    DT_CENTER);

    rect.top += nInfoAreaHeight;  
 
    CBrush br;  
 
    br.CreateSolidBrush(m_animationColor);

 CBrush* pBrushOld = dc.SelectObject(&br);

 
    dc.Rectangle((CRect)m_animationRect);

 dc.SelectObject(pBrushOld);

 }  
 ```  
  
9. 在檔案結尾，加入下列程式碼。  
  
 ```  
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)  
 {  
    static UI_ANIMATION_SECONDS duration = 3;  
    static DOUBLE dblSpeed = 35.;  
    static BYTE nStartColor = 50;  
    static BYTE nEndColor = 255;  
 
    BYTE nRedColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nGreenColorFinal = bDirection  nStartColor : nEndColor;  
    BYTE nBlueColorFinal = bDirection  nStartColor : nEndColor;  
 
    CLinearTransition* pRedTransition = new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

    CSmoothStopTransition* pGreenTransition = new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

    CLinearTransitionFromSpeed* pBlueTransition = new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

 
    m_animationColor.AddTransition(pRedTransition,
    pGreenTransition,
    pBlueTransition);

 
    CRect rectClient;  
    GetClientRect(rectClient);

 rectClient.top += nInfoAreaHeight;  
 
    int nLeftFinal = bDirection  rectClient.left : rectClient.CenterPoint().x;  
    int nTopFinal = bDirection  rectClient.top : rectClient.CenterPoint().y;  
    int nRightFinal = bDirection  rectClient.right : rectClient.CenterPoint().x;  
    int nBottomFinal = bDirection  rectClient.bottom : rectClient.CenterPoint().y;  
 
    CLinearTransition* pLeftTransition = new CLinearTransition(duration,
    nLeftFinal);

    CLinearTransition* pTopTransition = new CLinearTransition(duration,
    nTopFinal);

    CLinearTransition* pRightTransition = new CLinearTransition(duration,
    nRightFinal);

    CLinearTransition* pBottomTransition = new CLinearTransition(duration,
    nBottomFinal);

 
    m_animationRect.AddTransition(pLeftTransition,
    pTopTransition,
    pRightTransition,
    pBottomTransition);

 
    CBaseKeyFrame* pKeyframeStart = CAnimationController::GetKeyframeStoryboardStart();
CKeyFrame* pKeyFrameEnd = m_animationController.CreateKeyframe(nAnimationGroup,
    pBlueTransition);

 
    pLeftTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pTopTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pRightTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

    pBottomTransition->SetKeyframes(pKeyframeStart,
    pKeyFrameEnd);

 
    m_animationController.AnimateGroup(nAnimationGroup);

 }  
 ```  
  
10. 在**專案**功能表上，按一下 **類別精靈**。  
  
11. 在**MFC 類別精靈**下**類別名稱**，選取`CMFCAnimationWalkthroughView`。  
  
12. 上**訊息**索引標籤**訊息**方塊中，選取`WM_ERASEBKGND`，按一下 **加入處理常式**，然後按一下**確定**。  
  
13. 程式碼取代的實作中 MFCAnimationWalkthroughView.cpp，`OnEraseBkgnd`下列的程式碼，以減少生於重繪時閃爍動畫物件中。  
  
 ```  
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)  
 {  
    return TRUE;  
 }  
 ```  
  
14. 取代的實作`CMFCAnimationWalkthroughView::OnAnimationStartforward`， `CMFCAnimationWalkthroughView::OnAnimationStartbackward`，和`CMFCAnimationWalkthroughView::OnAnimationStop`為下列程式碼。  
  
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
  
15. 儲存檔案並關閉它。  
  
### <a name="to-center-the-animated-object-in-the-window"></a>若要置視窗中的動畫的物件  
  
1.  在**方案總管 中**，按兩下 MFCAnimationWalkthroughView.h 以開啟檔案進行修改。 在結尾`CMFCAnimationWalkthroughView`類別，只要之後的定義`m_animationRect`，加入下列程式碼。  
  
 ```  
    BOOL m_bCurrentDirection;  
 ```  
  
2.  儲存檔案並關閉它。  
  
3.  在**專案**功能表上，按一下 **類別精靈**。  
  
4.  在**MFC 類別精靈**下**類別名稱**，選取`CMFCAnimationWalkthroughView`。  
  
5.  上**訊息**索引標籤**訊息**方塊中，選取`WM_SIZE`，按一下 **加入處理常式**，然後按一下**確定**。  
  
6.  MFCAnimationWalkthroughView.cpp，在程式碼取代`CMFCAnimationWalkthroughView::OnSize`為下列程式碼。  
  
 ```  
    void CMFCAnimationWalkthroughView::OnSize(UINT nType,
    int cx,
    int cy)  
 {  
    CView::OnSize(nType,
    cx,
    cy);

 
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
  
7.  建構函式的開頭`CMFCAnimationWalkthroughView`，加入下列程式碼。  
  
 ```  
    m_bCurrentDirection = TRUE;  
 ```  
  
8.  在開頭`CMFCAnimationWalkthroughView::Animate`方法，加入下列程式碼。  
  
 ```  
    m_bCurrentDirection = bDirection;  
 ```  
  
9. 儲存檔案並關閉它。  
  
### <a name="to-verify-the-results"></a>若要確認結果  
  
1.  建置並執行應用程式。 在**動畫**功能表上，按一下  **Start Forward**。 矩形應該會出現，然後填入 中間區域。 當您按一下**Start Backward**應該反轉動畫，且當您按一下**停止**，應該停止。 矩形的填滿色彩應該變更動畫隨著，而且目前的色彩應該會顯示 [動畫] 視窗的頂端。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)

