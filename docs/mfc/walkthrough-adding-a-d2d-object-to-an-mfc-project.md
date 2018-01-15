---
title: "逐步解說： 將 D2D 物件加入至 MFC 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98c14611bbca828f6264c3fcfa66462c02320432
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>逐步解說：將 D2D 物件加入至 MFC 專案
本逐步解說教導如何新增基本 Direct2D (D2D) Visual c + +，Microsoft Foundation 類別庫 (MFC) 專案物件，並接著建置專案所列印的應用程式"Hello，world"為漸層的背景。  
  
 本逐步解說示範如何完成這些工作：  
  
-   建立 MFC 應用程式。  
  
-   建立純色筆刷和線性漸層筆刷。  
  
-   修改漸層筆刷，讓它將會變更適當地調整視窗的大小。  
  
-   實作 D2D 繪製處理常式。  
  
-   驗證結果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您必須具有 Visual Studio。  
  
### <a name="to-create-an-mfc-application"></a>若要建立 MFC 應用程式  
  
1.  在 [ **檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。  
  
2.  在**新專案**對話方塊中的，在左窗格中**已安裝的範本**，依序展開**Visual c + +** ，然後選取  **MFC**。 在中間窗格中，選取**MFC 應用程式**。 在 [名稱] 方塊中，輸入 `MFCD2DWalkthrough`。 按一下 [確定 **Deploying Office Solutions**]。  
  
3.  在**MFC 應用程式精靈**，按一下 **完成**不變更任何設定。  
  
### <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>若要建立純色筆刷和線性漸層筆刷  
  
1.  在**方案總管 中**，請在**MFCD2DWalkthrough**專案，在**標頭檔**資料夾中，開啟 MFCD2DWalkthroughView.h。 將下列程式碼加入`CMFCD2DWalkthroughView`類別來建立三個資料變數。  
  
 ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
 ```  
  
     儲存檔案並關閉它。  
  
2.  在**原始程式檔**資料夾中，開啟 MFCD2DWalkthroughView.cpp。 中的建構函式`CMFCD2DWalkthroughView`類別中，加入下列程式碼。  
  
 '' * / / 啟用此視窗 D2D 支援：  
    EnableD2DSupport();

 * / 初始化 D2D 資源：  
    m_pBlackBrush = 新 CD2DSolidColorBrush(GetRenderTarget()，D2D1::ColorF(D2D1::ColorF::Black));

 
    m_pTextFormat = 新 CD2DTextFormat(GetRenderTarget()，_T("Verdana")，50)。

    m_pTextFormat]-> [get （)]-> [SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);

 m_pTextFormat]-> [get （)]-> [SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

 
    D2D1_GRADIENT_STOP gradientStops [2];  
 
    [0] gradientStops.color = D2D1::ColorF(D2D1::ColorF::White);

    [0] gradientStops.position = 0.f;  
    [1] gradientStops.color = D2D1::ColorF(D2D1::ColorF::Indigo);

    [1] gradientStops.position = 1.f 則;  
 
    m_pLinearGradientBrush = 新 CD2DLinearGradientBrush(GetRenderTarget()，   
    gradientStops，ARRAYSIZE(gradientStops)，  
    D2D1::LinearGradientBrushProperties （D2D1::Point2F （0，0）、 D2D1::Point2F （0，0））);

 ```  
  
     Save the file and close it.  
  
### To modify the gradient brush so that it will change appropriately when the window is resized  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, in the **Messages** box, select `WM_SIZE` and then click **Add Handler**. This action adds the `OnSize` message handler to the `CMFCD2DWalkthroughView` class.  
  
4.  In the **Existing handlers** box, select `OnSize`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnSize` method. At the end of the method, add the following code.  
  
 ```  
    m_pLinearGradientBrush]-> [SetEndPoint (CPoint （cx、 cy）);

 ```  
  
     Save the file and close it.  
  
### To implement a D2D drawing handler  
  
1.  On the **Project** menu, click **Class Wizard**.  
  
2.  In the **MFC Class Wizard**, under **Class name**, select `CMFCD2DWalkthroughView`.  
  
3.  On the **Messages** tab, click **Add Custom Message**.  
  
4.  In the **Add Custom Message** dialog box, in the **Custom Windows Message** box, type `AFX_WM_DRAW2D`. In the **Message handler name** box, type `OnDraw2D`. Select the **Registered Message** option and then click **OK**. This action adds a message handler for the `AFX_WM_DRAW2D` message to the `CMFCD2DWalkthroughView` class.  
  
5.  In the **Existing handlers** box, select `OnDraw2D`. Click **Edit Code** to display the `CMFCD2DWalkthroughView::OnDraw2D` method. Use the following code for the `CMFCD2DWalkthroughView::OnDrawD2D` method.  
  
 ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
 CHwndRenderTarget * pRenderTarget = （CHwndRenderTarget *） lParam;  
    ASSERT_VALID(pRenderTarget);

 
    CRect rect;  
    GetClientRect(rect);

 
    pRenderTarget]-> [FillRectangle rect (m_pLinearGradientBrush）;

    pRenderTarget]-> [DrawText _T （"Hello，World ！"）、 矩形、 m_pBlackBrush (m_pTextFormat）;

 
    傳回 TRUE;  
 }  
 ```  
  
     Save the file and close it.  
  
### To verify the results  
  
1.  Build and run the application. It should have a gradient rectangle that changes when you resize the window. “Hello World!” should be displayed in the center of the rectangle.  
  
## See Also  
 [Walkthroughs](../mfc/walkthroughs-mfc.md)

