---
title: "一般視窗建立順序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "框架視窗 [C++], 建立"
  - "序列 [C++]"
  - "序列 [C++], 視窗建立"
  - "視窗 [C++], 建立"
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般視窗建立順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立新視窗時本身，例如子視窗，架構會使用處理序和 [文件\/檢視建立](../mfc/document-view-creation.md)中說明的一樣。  
  
 MFC 提供的所有視窗類別使用 [兩個階段建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)。  也就是 C\+\+ **new** 運算子的引動過程時，建構函式配置並初始化 C \+\+. 物件，但不建立對應的 Windows 視窗。  該視窗上呼叫物件的 [建立](../Topic/CWnd::Create.md) 成員函式之後完成。  
  
 **Create** 成員函式的 C\+\+ 物件的公用資料成員 [m\_hWnd](../Topic/CWnd::m_hWnd.md)讓視窗視窗並儲存它的 `HWND` 。  **Create** 會建立參數的完整彈性。  在呼叫 **Create**前，您可能要向全域函式 [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) 的視窗類別才能設定框架的圖示和類別樣式。  
  
 如需框架視窗，您可以使用 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 成員函式來取代 **Create**。  使用較少的參數`LoadFrame` ，讓視窗視窗。  從資源取得許多預設值，包括框架的標題、圖示、快速鍵對應表和功能表。  
  
> [!NOTE]
>  您的圖示、快速鍵對應表和功能表資源必須有公用資源 ID，例如 **IDR\_MAINFRAME**， LoadFrame 要載入的。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [視窗物件](../mfc/window-objects.md)  
  
-   [註冊視窗「類別」](../mfc/registering-window-classes.md)  
  
-   [終結視窗物件](../mfc/destroying-window-objects.md)  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
## 請參閱  
 [建立視窗](../mfc/creating-windows.md)