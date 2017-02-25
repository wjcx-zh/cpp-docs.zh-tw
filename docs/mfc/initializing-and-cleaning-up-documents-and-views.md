---
title: "初始化及清除文件和檢視 | Microsoft Docs"
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
  - "文件物件, 的生命週期"
  - "文件, 清除"
  - "文件, 初始化"
  - "初始化文件"
  - "初始化物件, 文件物件"
  - "初始化檢視"
  - "檢視, 清除"
  - "檢視, 初始化"
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 初始化及清除文件和檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用於初始化和清除使用下列方針，在文件和檢視之後:  
  
-   MFC 架構使用文件和檢視;在初始化所有資料加入至它們。  
  
-   架構清除文件和檢視關閉;您必須解除配置在堆積上配置從這些文件和檢視的成員函式內的所有記憶體。  
  
> [!NOTE]
>  前面說過整個應用程式的初始化最適合在您的類別 `CWinApp`的 [InitInstance](../Topic/CWinApp::InitInstance.md) 成員函式的覆寫完成，因此，整個應用程式的清除最適合在您的 `CWinApp` 成員函式 [ExitInstance](../Topic/CWinApp::ExitInstance.md)的覆寫完成。  
  
 一個文件的生命週期 \(及其框架視窗檢視或檢視\) 在 MDI 應用程式如下:  
  
1.  在動態建立時，文件會呼叫建構函式。  
  
2.  對於每個新文件，文件中的 [OnNewDocument](../Topic/CDocument::OnNewDocument.md) 或 [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) 呼叫。  
  
3.  使用者與文件互動在其存留期。  通常，當使用者在文件資料會透過這個檢視中，選取和編輯資料，就會發生這種情況。  這個檢視傳遞變更儲存和更新的其他檢視文件。  在這個階段文件和檢視可處理命令。  
  
4.  這個框架呼叫 [DeleteContents](../Topic/CDocument::DeleteContents.md) 刪除資料特有的資料。  
  
5.  文件的解構函式。  
  
 在 SDI 應用程式，，當文件在第一次建立時，步驟 1 執行一次。  然後，每次開啟，步驟 2 至 4 會重複執行一個新的文件。  新文件重複使用現有的資料物件。  最後，，當應用程式結束時，第 5 步驟執行。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [初始化文件和檢視](../mfc/initializing-documents-and-views.md)  
  
-   [清除文件和檢視](../mfc/cleaning-up-documents-and-views.md)  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)