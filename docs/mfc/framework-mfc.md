---
title: "架構 (MFC) | Microsoft Docs"
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
  - "API [C++], MFC Win32 執行的封裝"
  - "應用程式架構 [C++], 關於 MFC 應用程式架構"
  - "封裝的 Win32 應用程式開發介面"
  - "封裝 [C++]"
  - "封裝 [C++], Win32 應用程式開發介面"
  - "MFC [C++], 應用程式架構"
  - "Win32 [C++], MFC 執行的應用程式開發介面封裝"
  - "Windows API [C++], MFC 執行的封裝"
  - "包裝函式類別, 解說"
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 架構 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

和 Microsoft Foundation Class \(MFC\) 程式庫架構一起使用的工作主要是根據一些主要類別和數個 Visual C\+\+ 工具。  某些類別會封裝 Win32 應用程式開發介面 \(API\) 的一個主要部分。  其他類別封裝應用程式概念 \(例如文件、檢視和應用程式本身\)。  而剩下其他封裝 OLE 功能、ODBC 和 DAO 資料存取功能。  
  
 例如，Windows 的 Win32 概念是由 MFC 類別 `CWnd` 封裝。  也就是，一個名為 `CWnd` 的 C\+\+ 類別封裝或包裝代表 Windows 視窗的 `HWND` 控制代碼。  同樣地，類別 `CDialog` 封裝 Win32 對話方塊。  
  
 封裝表示 C\+\+ 類別 \(例如 `CWnd`\) 包含型別 `HWND` 的成員變數，而類別的成員函式封裝對採用 `HWND` 做為參數的 Win32 函式。  類別成員函式通常與它們封裝的 Win32 函式有相同名稱。  
  
## 本章節內容  
 [SDI 和 MDI](../mfc/sdi-and-mdi.md)  
  
 [文件、檢視和架構](../mfc/documents-views-and-the-framework.md)  
  
 [精靈和資源編輯器](../mfc/wizards-and-the-resource-editors.md)  
  
## 相關章節  
 [在架構上建置](../mfc/building-on-the-framework.md)  
  
 [架構如何呼叫您的程式碼](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)  
  
 [文件範本和文件\/檢視建立流程](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
 [視窗物件](../mfc/window-objects.md)  
  
## 請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)