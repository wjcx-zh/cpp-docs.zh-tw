---
title: "逐步解說：將 D2D 物件加入至 MFC 專案 | Microsoft Docs"
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
  - "D2D [MFC]"
  - "MFC, D2D"
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
caps.latest.revision: 20
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：將 D2D 物件加入至 MFC 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本逐步解說教導如何將基本 Direct2D \(D2D\) 物件加入至 Visual C\+\+ MFC 程式庫專案，然後將專案建置成為在漸層背景中列印 "Hello, world" 的應用程式。  
  
 逐步解說將示範如何完成這些工作：  
  
-   建立 MFC 應用程式。  
  
-   建立純色筆刷和線性漸層筆刷。  
  
-   修改漸層筆刷，讓它在視窗調整大小時適當變更。  
  
-   實作 D2D 繪圖處理常式。  
  
-   驗證結果。  
  
 [!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]  
  
## 必要條件  
 若要完成這個逐步解說中，您必須有 Visual Studio。  
  
### 若要建立 MFC 應用程式  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，展開左窗格中 \[**已安裝的範本**\] 底下的 \[**Visual C\+\+**\]，然後選取 \[**MFC**\]。  在中間窗格中選取 \[**MFC 應用程式**\]。  在 \[**名稱**\] 方塊中輸入 `MFCD2DWalkthrough`。  按一下 \[**確定**\]。  
  
3.  在 \[**MFC 應用程式精靈**\] 中，按一下 \[**完成**\]，而不要變更任何設定。  
  
### 若要建立純色筆刷和線性漸層筆刷  
  
1.  在 \[**方案總管**\] 中，在 **MFCD2DWalkthrough** 專案的 \[**標頭檔**\] 資料夾中開啟 MFCD2DWalkthroughView.h。  將下列程式碼加入至 `CMFCD2DWalkthroughView` 類別，以建立三個資料變數。  
  
    ```  
    CD2DTextFormat* m_pTextFormat;  
    CD2DSolidColorBrush* m_pBlackBrush;  
    CD2DLinearGradientBrush* m_pLinearGradientBrush;  
    ```  
  
     儲存並關閉檔案。  
  
2.  在 \[**原始程式檔**\] 資料夾中，開啟 MFCD2DWalkthroughView.cpp。  在 `CMFCD2DWalkthroughView` 類別的建構函式中加入下列程式碼。  
  
    ```  
    // Enable D2D support for this window:  
    EnableD2DSupport();  
  
    // Initialize D2D resources:  
    m_pBlackBrush = new CD2DSolidColorBrush(GetRenderTarget(), D2D1::ColorF(D2D1::ColorF::Black));  
  
    m_pTextFormat = new CD2DTextFormat(GetRenderTarget(), _T("Verdana"), 50);  
    m_pTextFormat->Get()->SetTextAlignment(DWRITE_TEXT_ALIGNMENT_CENTER);  
    m_pTextFormat->Get()->SetParagraphAlignment(DWRITE_PARAGRAPH_ALIGNMENT_CENTER);  
  
    D2D1_GRADIENT_STOP gradientStops[2];  
  
    gradientStops[0].color = D2D1::ColorF(D2D1::ColorF::White);  
    gradientStops[0].position = 0.f;  
    gradientStops[1].color = D2D1::ColorF(D2D1::ColorF::Indigo);  
    gradientStops[1].position = 1.f;  
  
    m_pLinearGradientBrush = new CD2DLinearGradientBrush(GetRenderTarget(),   
        gradientStops, ARRAYSIZE(gradientStops),  
        D2D1::LinearGradientBrushProperties(D2D1::Point2F(0, 0), D2D1::Point2F(0, 0)));  
    ```  
  
     儲存並關閉檔案。  
  
### 若要修改漸層筆刷，讓它在視窗調整大小時適當變更  
  
1.  在 \[**專案**\] 功能表上按一下 \[**類別精靈**\]。  
  
2.  在 \[**MFC 類別精靈**\] 中，選取 \[**類別名稱**\] 底下的 `CMFCD2DWalkthroughView`。  
  
3.  在 \[**訊息**\] 索引標籤的 \[**訊息**\] 方塊中，選取 `WM_SIZE`，然後按一下 \[**加入處理常式**\]。  這個動作會將 `OnSize` 訊息處理常式加入至 `CMFCD2DWalkthroughView` 類別。  
  
4.  在 \[**現有的處理常式**\] 方塊中選取 `OnSize`。  按一下 \[**編輯程式碼**\]，以顯示 `CMFCD2DWalkthroughView::OnSize` 方法。  在方法的結尾加入下列程式碼。  
  
    ```  
    m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));  
    ```  
  
     儲存並關閉檔案。  
  
### 若要實作 D2D 繪圖處理常式  
  
1.  在 \[**專案**\] 功能表上按一下 \[**類別精靈**\]。  
  
2.  在 \[**MFC 類別精靈**\] 中，選取 \[**類別名稱**\] 底下的 `CMFCD2DWalkthroughView`。  
  
3.  按一下 \[**訊息**\] 索引標籤上的 \[**加入自訂訊息**\]。  
  
4.  在 \[**加入自訂訊息**\] 對話方塊中，在 \[**自訂 Windows 訊息**\] 方塊內輸入 `AFX_WM_DRAW2D`。  在 \[**訊息處理常式名稱**\] 方塊中，輸入 `OnDraw2D`。  選取 \[**註冊訊息**\] 選項，然後按一下 \[**確定**\]。  這個動作會將 `AFX_WM_DRAW2D` 訊息的訊息處理常式加入至 `CMFCD2DWalkthroughView` 類別。  
  
5.  在 \[**現有的處理常式**\] 方塊中選取 `OnDraw2D`。  按一下 \[**編輯程式碼**\]，以顯示 `CMFCD2DWalkthroughView::OnDraw2D` 方法。  將下列程式碼用於 `CMFCD2DWalkthroughView::OnDrawD2D` 方法。  
  
    ```  
    afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(WPARAM wParam, LPARAM lParam)  
    {  
        CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;  
        ASSERT_VALID(pRenderTarget);  
  
        CRect rect;  
        GetClientRect(rect);  
  
        pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);  
        pRenderTarget->DrawText(_T("Hello, World!"), rect, m_pBlackBrush, m_pTextFormat);  
  
        return TRUE;  
    }  
    ```  
  
     儲存並關閉檔案。  
  
### 若要驗證結果  
  
1.  建置並執行應用程式。  其漸層矩形應該會在視窗調整大小時變更。"Hello World\!" 應該會顯示在矩形中心。  
  
## 請參閱  
 [逐步解說](../mfc/walkthroughs-mfc.md)