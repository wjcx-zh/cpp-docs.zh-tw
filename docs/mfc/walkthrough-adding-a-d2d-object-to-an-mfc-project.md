---
title: 逐步解說： 將 D2D 物件加入至 MFC 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/19/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68a6d5a0cda8c4d7fd06cf7bb6b9c1b60e50374b
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36306004"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>逐步解說：將 D2D 物件加入至 MFC 專案

本逐步解說教導如何新增基本 Direct2D (D2D) Visual c + +，Microsoft Foundation 類別庫 (MFC) 專案物件，並接著建置專案所列印的應用程式"Hello，world"為漸層的背景。

本逐步解說示範如何完成這些工作：

- 建立 MFC 應用程式。

- 建立純色筆刷和線性漸層筆刷。

- 修改漸層筆刷，讓它將會變更適當地調整視窗的大小。

- 實作 D2D 繪製處理常式。

- 驗證結果。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須安裝與 Visual Studio**的 c + + 桌面應用程式開發**工作負載和選擇性**適用於 x86 和 x64 的 Visual c + + MFC**元件。

## <a name="to-create-an-mfc-application"></a>若要建立 MFC 應用程式

1. 在**檔案**功能表上，指向**新增**，然後選擇 **專案**。

2. 在**新專案**對話方塊中的，在左窗格中**已安裝的範本**，依序展開**Visual c + +** ，然後選取  **MFC**。 在中間窗格中，選取**MFC 應用程式**。 在 [名稱] 方塊中，輸入 `MFCD2DWalkthrough`。 選擇 [確定] 。

3. 在**MFC 應用程式精靈**，選擇**完成**不變更任何設定。

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>若要建立純色筆刷和線性漸層筆刷

1. 在**方案總管 中**，請在**MFCD2DWalkthrough**專案，在**標頭檔**資料夾中，開啟 MFCD2DWalkthroughView.h。 將此程式碼加入`CMFCD2DWalkthroughView`類別來建立資料的三個變數：

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   儲存檔案並關閉它。

2. 在**原始程式檔**資料夾中，開啟 MFCD2DWalkthroughView.cpp。 中的建構函式`CMFCD2DWalkthroughView`類別中，加入下列程式碼：

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   儲存檔案並關閉它。

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>修改漸層筆刷，使它將會變更適當地調整視窗的大小

1. 在**專案**功能表上，選擇**類別精靈**。

2. 在**MFC 類別精靈**下**類別名稱**，選取`CMFCD2DWalkthroughView`。

3. 在**訊息**索引標籤的**訊息**方塊中，選取`WM_SIZE`，然後選擇 **加入處理常式**。 這個動作會將`OnSize`訊息處理常式來`CMFCD2DWalkthroughView`類別。

4. 在**現有處理常式**方塊中，選取`OnSize`。 選擇**編輯程式碼**顯示`CMFCD2DWalkthroughView::OnSize`方法。 在方法的結尾，加入下列程式碼。

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   儲存檔案並關閉它。

## <a name="to-implement-a-d2d-drawing-handler"></a>若要實作 D2D 繪製處理常式

1. 在**專案**功能表上，選擇**類別精靈**。

2. 在**MFC 類別精靈**下**類別名稱**，選取`CMFCD2DWalkthroughView`。

3. 在**訊息**索引標籤上，選擇**加入自訂訊息**。

4. 在**加入自訂訊息**對話方塊中，於**自訂 Windows 訊息**方塊中，輸入`AFX_WM_DRAW2D`。 在**訊息處理常式名稱**方塊中，輸入`OnDraw2D`。 選取**登錄訊息**選項，然後選擇**確定**。 這個動作會將訊息處理常式`AFX_WM_DRAW2D`傳送訊息給`CMFCD2DWalkthroughView`類別。

5. 在**現有處理常式**方塊中，選取`OnDraw2D`。 選擇**編輯程式碼**顯示`CMFCD2DWalkthroughView::OnDraw2D`方法。 使用此程式碼`CMFCD2DWalkthroughView::OnDrawD2D`方法：

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   儲存檔案並關閉它。

## <a name="to-verify-the-results"></a>若要確認結果

- 建置並執行應用程式。 它應該有漸層變更時調整視窗大小的矩形。 "Hello World ！" 應該會顯示在矩形的中心。

## <a name="see-also"></a>另請參閱

- [逐步解說](../mfc/walkthroughs-mfc.md)
