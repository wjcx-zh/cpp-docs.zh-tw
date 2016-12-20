---
title: "框架視窗類別 | Microsoft Docs"
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
  - "類別 [C++], 視窗"
  - "文件框架視窗, 類別"
  - "框架視窗類別"
  - "框架視窗類別, 關於框架視窗類別"
  - "MDI [C++], 框架視窗"
  - "MFC [C++], 框架視窗"
  - "單一文件介面 (SDI), 框架視窗"
  - "視窗類別, 框架"
  - "視窗 [C++], MDI"
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架視窗類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個應用程式具有主框架視窗，」通常有應用程式名稱在標題的桌面視窗。  每個文件通常具有文件框架視窗」。文件框架視窗至少包含一個檢視，顯示文件中的資料。  
  
## 在 SDI、MDI 應用程式框架視窗  
 如果是 SDI 應用程式，有衍生自框架視窗 [CFrameWnd](../mfc/reference/cframewnd-class.md)。  這個視窗是主框架視窗與文件框架視窗。  對於 MDI 應用程式中，主框架視窗從類別衍生自 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)，，且文件框架視窗，是 MDI 子視窗，請從類別衍生自 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。  
  
## 使用框架視窗類別或衍生自它?  
 這些類別提供您為應用程式所需的大部分框架視窗功能。  在一般情況下，它們所提供的預設行為和外觀符合您的需要。  如果您需要其他功能，從這些類別衍生。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [應用程式精靈建立框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架視窗樣式。](../mfc/frame-window-styles-cpp.md)  
  
-   [變更視窗的樣式由 MFC 建立](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## 請參閱  
 [框架視窗](../mfc/frame-windows.md)