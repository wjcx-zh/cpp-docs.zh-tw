---
title: 逐步解說：將 D2D 物件加入至 MFC 專案
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304300"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>逐步解說：將 D2D 物件加入至 MFC 專案

本逐步解說將教您如何將基本 Direct2D （D2D）物件加入至C++視覺效果的 MFC 程式庫（MFC）專案，然後將專案建立到列印 "Hello，World！" 的應用程式中。 在漸層背景上。

本逐步解說會示範如何完成這些工作：

- 建立 MFC 應用程式。

- 建立純色筆刷和線性漸層筆刷。

- 修改漸層筆刷，使其在調整大小視窗時可以適當地變更。

- 執行 D2D 繪製處理常式。

- 驗證結果。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須在**使用C++** 工作負載的桌面開發和適用于**x86 C++和 x64 的選用 Visual MFC**元件中安裝 Visual Studio。

## <a name="to-create-an-mfc-application"></a>建立 MFC 應用程式

1. 使用**Mfc 應用程式精靈**來建立 mfc 應用程式。 如需如何為您的 Visual Studio 版本開啟嚮導的指示，請參閱[逐步解說：使用新的 MFC Shell 控制項](walkthrough-using-the-new-mfc-shell-controls.md)。

1. 在 [**名稱**] 方塊中，輸入*MFCD2DWalkthrough*。 選擇 [ **確定**]。

1. 在**MFC 應用程式精靈**中，選擇 **[完成]** 而不變更任何設定。

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>建立純色筆刷和線性漸層筆刷

1. 在**方案總管**中，在**MFCD2DWalkthrough**專案的 [**標頭檔**] 資料夾中，開啟 MFCD2DWalkthroughView。 將此程式碼新增至 `CMFCD2DWalkthroughView` 類別，以建立三個數據變數：

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   儲存檔案並加以關閉。

1. 在 [**來源**檔案] 資料夾中，開啟 MFCD2DWalkthroughView。 在 `CMFCD2DWalkthroughView` 類別的函式中，加入下列程式碼：

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

   儲存檔案並加以關閉。

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>修改漸層筆刷，使其在調整大小時會適當地變更

1. 在 [**專案**] 功能表上，選擇 [**類別 Wizard]** 。

1. 在**MFC 類別 Wizard**的 [**類別名稱**] 底下，選取 [`CMFCD2DWalkthroughView`]。

1. 在 [**訊息**] 索引標籤的 [**訊息**] 方塊中，選取 `WM_SIZE`，然後選擇 [**新增處理常式**]。 此動作會將 `OnSize` 訊息處理常式新增至 `CMFCD2DWalkthroughView` 類別。

1. 在 [**現有處理常式**] 方塊中，選取 [`OnSize`]。 選擇 [**編輯程式碼**] 以顯示 `CMFCD2DWalkthroughView::OnSize` 方法。 在方法的結尾，新增下列程式碼。

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   儲存檔案並加以關閉。

## <a name="to-implement-a-d2d-drawing-handler"></a>若要執行 D2D 繪製處理常式

1. 在 [**專案**] 功能表上，選擇 [**類別 Wizard]** 。

1. 在**MFC 類別 Wizard**的 [**類別名稱**] 底下，選取 [`CMFCD2DWalkthroughView`]。

1. 在 [**訊息**] 索引標籤上，選擇 [**新增自訂訊息**]。

1. 在 [**加入自訂訊息**] 對話方塊的 [**自訂 Windows] 消息**框中，輸入*AFX_WM_DRAW2D*。 在 [**訊息處理常式名稱**] 方塊中，輸入*OnDraw2D*。 選取 [**已註冊的訊息**] 選項，然後選擇 [**確定]** 。 此動作會將 AFX_WM_DRAW2D 訊息的訊息處理常式新增至 `CMFCD2DWalkthroughView` 類別。

1. 在 [**現有處理常式**] 方塊中，選取 [`OnDraw2D`]。 選擇 [**編輯程式碼**] 以顯示 `CMFCD2DWalkthroughView::OnDraw2D` 方法。 將此程式碼用於 `CMFCD2DWalkthroughView::OnDrawD2D` 方法：

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

   儲存檔案並加以關閉。

## <a name="to-verify-the-results"></a>驗證結果

建置並執行應用程式。 當您調整視窗大小時，它應該會有變更的漸層矩形。 "Hello World!" 應該顯示在矩形的中央。

## <a name="see-also"></a>另請參閱

[逐步解說](../mfc/walkthroughs-mfc.md)
