---
title: "框架視窗 | Microsoft Docs"
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
  - "CFrameWnd 類別, 框架視窗"
  - "文件框架視窗"
  - "框架視窗 [C++]"
  - "框架視窗 [C++], 關於框架視窗"
  - "MDI [C++], 框架視窗"
  - "MFC [C++], 框架視窗"
  - "單一文件介面 (SDI)"
  - "單一文件介面 (SDI), 框架視窗"
  - "分隔視窗, 和框架視窗"
  - "檢視 [C++], 和框架視窗"
  - "視窗類別 [C++], 框架"
  - "視窗 [C++], MDI"
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 框架視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當應用程式在 Windows 下執行時，使用者與框架視窗中顯示的文件互動。  文件框架視窗有兩個主要元件：框架和框架的內容。  文件框架視窗可以是 [單一文件介面](../mfc/sdi-and-mdi.md) \(SDI\) 框架視窗，或 [多重文件介面](../mfc/sdi-and-mdi.md) \(MDI\) 子視窗。   Windows 大部分以框架視窗處理使用者的互動：移動和調整視窗大小，關閉、最小化和最大化。  您可以管理框架內的內容。  
  
## 框架視窗和檢視  
 MFC 架構使用框架視窗來包含檢視。  兩個元件—框架和內容—由 MFC 中的兩個不同的類別代表及處理。  框架視窗類別處理架構，而檢視類別處理內容。  檢視視窗是框架視窗的子系。  繪圖與其他使用者互動會發生在檢視的工作區，而不是框架視窗的工作區中。  框架視窗在檢視周圍提供可見的框架，標題列和標準 Windows 控制項 \(例如控制功能表，最小化和最大化視窗的按鈕，以及調整視窗大小的控制項\)。  「內容」包括視窗的工作區，由子視窗—檢視完全佔用。  下圖顯示框架視窗和檢視的關聯性。  
  
 ![框架視窗檢視](../mfc/media/vc37fx1.png "vc37FX1")  
框架視窗與檢視  
  
## 框架視窗和分隔視窗  
 另一種常見的框架視窗安排是框架多個檢視，通常是使用 [分隔視窗](../mfc/multiple-document-types-views-and-frame-windows.md)。  在分隔視窗中，框架視窗的工作區由分隔視窗佔用，其中又有多個子視窗，稱為窗格 \(是檢視\)。  
  
### 您還想知道關於哪些方面的詳細資訊？  
 **一般框架視窗主題**  
  
-   [視窗物件](../mfc/window-objects.md)  
  
-   [框架視窗類別](../mfc/frame-window-classes.md)  
  
-   [應用程式精靈所建立的框架視窗類別](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [框架視窗樣式](../mfc/frame-window-styles-cpp.md)  
  
-   [框架視窗可以做什麼](../mfc/what-frame-windows-do.md)  
  
 **使用框架視窗的主題**  
  
-   [使用框架視窗](../mfc/using-frame-windows.md)  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
-   [管理 MDI 子視窗](../mfc/managing-mdi-child-windows.md)  
  
-   在包含多個檢視的框架視窗內 [管理目前的檢視](../mfc/managing-the-current-view.md)  
  
-   [管理功能表、控制列和快速鍵 \(其他物件共用框架視窗空間的物件\)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **特殊框架視窗功能的主題**  
  
-   從檔案總管或文件管理員 [拖放檔案](../mfc/dragging-and-dropping-files-in-a-frame-window.md) 到框架視窗  
  
-   [回應動態資料交換 \(DDE\)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Semimodal 狀態：即時線上 Windows 說明 \(組織其他視窗動作\)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Semimodal 狀態：列印和預覽 \(組織其他視窗動作\)](../mfc/orchestrating-other-window-actions.md)  
  
 **其他類型視窗的主題**  
  
-   [使用檢視](../mfc/using-views.md)  
  
-   [對話方塊](../mfc/dialog-boxes.md)  
  
-   [控制項](../mfc/controls-mfc.md)  
  
## 請參閱  
 [Windows](../mfc/windows.md)