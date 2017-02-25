---
title: "變更 MFC 所建立之視窗的樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWnd 類別, 視窗樣式"
  - "子視窗, 樣式"
  - "CMainFrame 類別"
  - "CMDIChildWnd 類別, 變更視窗樣式"
  - "CREATESTRUCT 巨集"
  - "預設視窗樣式"
  - "預設值 [C++], 視窗樣式"
  - "MDI [C++], 視窗樣式"
  - "MFC [C++], 視窗"
  - "多文件介面樣式"
  - "PreCreateWindow 方法, 變更視窗樣式"
  - "PreCreateWindow 方法, 視窗樣式"
  - "單一文件介面 (SDI), 變更視窗屬性"
  - "單一文件介面 (SDI), 樣式"
  - "樣式, 視窗"
  - "視窗樣式 [C++]"
  - "視窗 [C++], MFC"
  - "WS_OVERLAPPEDWINDOW 巨集"
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 變更 MFC 所建立之視窗的樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在其 `WinMain` 函式的版本， MFC 註冊多個標準視窗類別。  由於您通常無法編輯 MFC 的 `WinMain`，該函式不讓您有機會變更 MFC 預設視窗樣式。  本文說明如何變更這類 preregistered 視窗的類別樣式在現有應用程式的。  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> 在新的 MFC 應用程式的變更樣式  
 當您建置應用程式時，如果您使用 Visual C\+\+ 2.0 \(含\) 以後版本，您可以變更應用程式精靈的預設視窗樣式。  在應用程式精靈的使用者介面功能頁面，您可以變更您的主框架視窗與 MDI 子視窗的樣式。  對於任一個視窗類型，您可以指定應用程式的架構粗細 \(粗或變更記事本\) 和下列任何一項:  
  
-   視窗是否具有最小化或最大化控制。  
  
-   視窗是否已最大化最初最小化，或兩者皆不是。  
  
 如需主框架視窗，您也可以指定視窗是否具有系統功能表。  對於 MDI 子視窗，您可以指定視窗是否支援分割窗格。  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> 在現有的應用程式中變更樣式  
 如果您變更現有的應用程式視窗的屬性，請遵循中的指示本文。  
  
 若要變更架構應用程式使用的預設視窗屬性以應用程式精靈，可覆寫視窗 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 的虛擬成員函式。  `PreCreateWindow` 可讓應用程式存取建立處理序由 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) 類別內部通常處置。  架構會在建立視窗之前呼叫 `PreCreateWindow` 。  藉由修改 [CREATESTRUCT](../mfc/reference/createstruct-structure.md) 結構會傳遞至 `PreCreateWindow`，您的應用程式可以變更此屬性可用來建立視窗。  例如，為了確保視窗不使用標題，請使用下列位元運算:  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 [CTRLBARS](../top/visual-cpp-samples.md) 應用程式會示範變更視窗屬性的技術。  根據您的應用程式在 `PreCreateWindow`變更時，呼叫函式的基底類別實作可能是必要的。  
  
 下列討論涵蓋 SDI 案例和 [MDI 案例](#_core_the_mdi_case)。  
  
##  <a name="_core_the_sdi_case"></a> SDI 案例  
 在單一文件介面 \(SDI\) \(SDI\) 應用程式，在這個框架的預設視窗樣式是 **WS\_OVERLAPPEDWINDOW** 和 **FWS\_ADDTOTITLE** 樣式的組合。  **FWS\_ADDTOTITLE** 是指示架構將文件標題到視窗標題的一個 MFC 的模式。  若要變更在 SDI 應用程式視窗的屬性，覆寫在應用程式精靈命名 `CMainFrame`\) 的 `CFrameWnd` 衍生的類別中 `PreCreateWindow` 函式 \(。  例如：  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 這個程式碼會建立一個主框架視窗，而不用最小化和最大化按鈕，但不會有相當大的框線。  視窗在螢幕的中央。  
  
##  <a name="_core_the_mdi_case"></a> MDI 案例  
 會要求更多工作變更的子視窗的視窗樣式在多重文件介面 \(MDI\) 應用程式。  根據預設， MDI 應用程式以應用程式精靈在 MFC 使用定義的預設的 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 類別。  若要變更 MDI 子視窗的視窗樣式，您必須從 `CMDIChildWnd` 衍生新類別和套用至新的類別的參考取代為 `CMDIChildWnd` 的所有參考都在您的專案。  很可能，對 `CMDIChildWnd` 的唯一參考應用程式位於應用程式的 `InitInstance` 成員函式。  
  
 用於 MDI 應用程式的預設視窗樣式是 **WS\_CHILD**和 **WS\_OVERLAPPEDWINDOW**和 **FWS\_ADDTOTITLE** 樣式的組合。  若要變更 MDI 應用程式的子視窗的視窗屬性，覆寫在衍生自 `CMDIChildWnd`的類別的 [PreCreateWindow](../Topic/CWnd::PreCreateWindow.md) 函式。  例如：  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/CPP/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 這個程式碼會建立 MDI 子視窗，而不用最大化按鈕。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [視窗樣式](../mfc/reference/window-styles.md)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
-   [\<caps:sentence id\="tgt44" sentenceid\="26254917059da4aba50f886a6c5db931" class\="tgtSentence"\>視窗樣式\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## 請參閱  
 [框架視窗樣式](../mfc/frame-window-styles-cpp.md)