---
title: "類別庫概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別庫"
  - "類別庫, MFC"
  - "類別 [C++], MFC"
  - "將 MFC 類別分組"
  - "MFC, 類別庫"
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 類別庫概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本概觀會將 Microsoft Foundation Class \(MFC\) 程式庫 9.0 版中的類別分類並進行說明。  MFC 中的類別共同構成應用程式架構 \-\- 針對 Windows 應用程式開發介面撰寫之應用程式的架構。  您的程式設計工作就是填入專屬於您應用程式的程式碼。  
  
 程式庫的類別依下列分類顯示如下：  
  
-   [根類別：CObject](../mfc/root-class-cobject.md)  
  
-   [MFC 應用程式架構類別](../mfc/mfc-application-architecture-classes.md)  
  
    -   [應用程式和執行緒支援類別](../mfc/application-and-thread-support-classes.md)  
  
    -   [命令路由類別](../mfc/command-routing-classes.md)  
  
    -   [文件類別](../mfc/document-classes.md)  
  
    -   [檢視類別 \(架構\)](../mfc/view-classes-architecture.md)  
  
    -   [框架視窗類別 \(架構\)](../mfc/frame-window-classes-architecture.md)  
  
    -   [文件範本類別](../mfc/document-template-classes.md)  
  
-   [視窗、對話方塊和控制項類別](../mfc/window-dialog-and-control-classes.md)  
  
    -   [框架視窗類別 \(視窗\)](../mfc/frame-window-classes-windows.md)  
  
    -   [檢視類別 \(Windows\)](../mfc/view-classes-windows.md)  
  
    -   [對話方塊類別](../mfc/dialog-box-classes.md)  
  
    -   [控制項類別](../mfc/control-classes.md)  
  
    -   [控制列類別](../mfc/control-bar-classes.md)  
  
-   [繪圖和列印類別](../mfc/drawing-and-printing-classes.md)  
  
    -   [輸出 \(裝置內容\) 類別](../mfc/output-device-context-classes.md)  
  
    -   [繪圖工具類別](../mfc/drawing-tool-classes.md)  
  
-   [簡單資料類型類別](../mfc/simple-data-type-classes.md)  
  
-   [陣列、清單和對應類別](../mfc/array-list-and-map-classes.md)  
  
    -   [陣列、清單和對應的樣板類別](../mfc/template-classes-for-arrays-lists-and-maps.md)  
  
    -   [立即可用的陣列類別](../mfc/ready-to-use-array-classes.md)  
  
    -   [立即可用的清單類別](../mfc/ready-to-use-list-classes.md)  
  
    -   [立即可用的對應類別](../mfc/ready-to-use-map-classes.md)  
  
-   [檔案和資料庫類別](../mfc/file-and-database-classes.md)  
  
    -   [檔案 I\/O 類別](../mfc/file-i-o-classes.md)  
  
    -   [DAO 類別](../mfc/dao-classes.md)  
  
    -   [ODBC 類別](../mfc/odbc-classes.md)  
  
    -   [OLE DB 類別](../mfc/ole-db-classes.md)  
  
-   [網際網路和網路類別](../mfc/internet-and-networking-classes.md)  
  
    -   [Windows Sockets 類別](../mfc/windows-sockets-classes.md)  
  
    -   [Win32 網際網路類別](../mfc/win32-internet-classes.md)  
  
-   [OLE 類別](../mfc/ole-classes.md)  
  
    -   [OLE 容器類別](../mfc/ole-container-classes.md)  
  
    -   [OLE 伺服器類別](../mfc/ole-server-classes.md)  
  
    -   [OLE 拖放和資料傳輸類別](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)  
  
    -   [OLE 通用對話方塊類別](../mfc/ole-common-dialog-classes.md)  
  
    -   [OLE Automation 類別](../mfc/ole-automation-classes.md)  
  
    -   [OLE 控制項類別](../mfc/ole-control-classes.md)  
  
    -   [主動式文件類別](../mfc/active-document-classes.md)  
  
    -   [OLE 相關類別](../mfc/ole-related-classes.md)  
  
-   [偵錯和例外狀況類別](../mfc/debugging-and-exception-classes.md)  
  
    -   [偵錯支援類別](../mfc/debugging-support-classes.md)  
  
    -   [例外狀況類別](../mfc/exception-classes.md)  
  
 [一般類別設計原則](../mfc/general-class-design-philosophy.md)一節說明 MFC 程式庫是如何設計的。  
  
 如需架構的概觀，請參閱[使用類別撰寫 Windows 的應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)。  以上所列的部分類別是通用類別，可在架構之外使用，並提供有用的抽象，例如集合、例外狀況、檔案和字串。  
  
 若要查看類別的繼承，請使用[類別階層架構圖表](../mfc/hierarchy-chart.md)。  
  
 除了本概觀中列出的類別之外，MFC 程式庫還包含許多全域函式、全域變數和巨集。  在 [MFC 巨集和全域](../mfc/reference/mfc-macros-and-globals.md)主題中有概觀和詳細清單，這些內容是依照 MFC 類別的字母參考順序編排。  
  
## 請參閱  
 [MFC 桌面應用程式](../mfc/mfc-desktop-applications.md)