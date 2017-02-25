---
title: "Windows | Microsoft Docs"
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
  - "MFC [C++], 視窗"
  - "物件 [C++], 視窗"
  - "視窗物件 [C++], MFC 架構"
  - "視窗 [C++]"
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文章系列涵蓋在 MFC 框架視窗物件。  所有 MFC Windows 從包含框架視窗、檢視、對話方塊和控制項的類別衍生自 [CWnd](../mfc/reference/cwnd-class.md)，。  
  
 文件的第一個群組的一般描述 [視窗物件](../mfc/window-objects.md) 。  請參閱這個群組有關 C\+\+ 視窗物件的一般資訊，以及如何封裝 HWND，，以及如何使用它們，當建立自己的視窗，例如子視窗時。  
  
 文件的第二個群組特別說明內容周圍放置—框架的 [框架視窗](../mfc/frame-windows.md)—視窗。  請參閱這個群組如需 MFC 架構如何處理這些框架的框架視窗和內容，包括控制列和檢視。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 *在視窗物件的一般主題*  
  
-   [視窗物件](../mfc/window-objects.md)  
  
-   [C \+\+. 視窗之間的關聯性與 HWND 控制代碼](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [衍生的視窗類別](../mfc/derived-window-classes.md)  
  
-   [建立視窗物件](../mfc/creating-windows.md)  
  
-   [要終結的視窗物件](../mfc/destroying-window-objects.md)  
  
-   [註冊 Windows 「分類」](../mfc/registering-window-classes.md)  
  
-   [與視窗物件一起使用](../mfc/working-with-window-objects.md)  
  
-   [裝置內容。](../mfc/device-contexts.md):可讓視窗繪製與裝置無關的物件  
  
-   [圖形物件](../mfc/graphic-objects.md):筆刷，，字型，點陣圖，調色盤，區域  
  
 *框架視窗主題*  
  
-   [框架視窗](../mfc/frame-windows.md):提供框架視窗物件  
  
-   [框架視窗和檢視](../mfc/frame-windows.md)  
  
-   [框架視窗類別](../mfc/frame-window-classes.md)  
  
-   [框架視窗樣式。](../mfc/frame-window-styles-cpp.md)  
  
-   [變更視窗的樣式由 MFC 建立](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [哪些框架視窗](../mfc/what-frame-windows-do.md)  
  
-   [使用框架視窗](../mfc/using-frame-windows.md)  
  
-   [處理的 MD\/Child 視窗 \(MDICLIENT 視窗\)](../mfc/managing-mdi-child-windows.md)  
  
-   [處理功能表、控制列和快速鍵](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [CFrameWnd](../mfc/reference/cframewnd-class.md)  
  
-   [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
  
-   [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
  
-   [使用檢視](../mfc/using-views.md)  
  
-   [許多資料型別、檢視和框架視窗 \(分隔視窗\)](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [訊息 \(對應和處理函式\)](../mfc/messages.md)  
  
 *建立和終結視窗*  
  
-   [一般視窗建立序列](../mfc/general-window-creation-sequence.md)  
  
-   [終結視窗物件](../mfc/destroying-window-objects.md)  
  
-   [建立文件框架視窗。](../mfc/creating-document-frame-windows.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
 *建立分隔視窗*  
  
-   [建立分隔視窗](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
 *處理子視窗與目前檢視*  
  
-   [處理 MDI 子視窗](../mfc/managing-mdi-child-windows.md)  
  
-   [處理目前的檢視](../mfc/managing-the-current-view.md)  
  
-   [處理功能表、控制列和快速鍵](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 *與裝置內容和視窗樣式一起使用*  
  
-   [在裝置內容使用畫筆及其他圖形物件](../mfc/graphic-objects.md)  
  
-   [變更 MFC 建立之視窗的樣式。](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [對話方塊](../mfc/dialog-boxes.md)   
 [工具列](../mfc/toolbars.md)   
 [狀態列](../mfc/status-bars.md)   
 [對話方塊列](../mfc/dialog-bars.md)