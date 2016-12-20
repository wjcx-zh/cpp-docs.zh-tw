---
title: "建立文件框架視窗 | Microsoft Docs"
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
  - "文件框架視窗, 建立"
  - "文件樣板, 和文件框架視窗"
  - "框架視窗 [C++], 建立"
  - "MFC [C++], 框架視窗"
  - "執行階段類別, 和文件框架視窗建立"
  - "執行階段, 類別資訊"
  - "視窗 [C++], 建立"
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立文件框架視窗
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[文件\/檢視建立](../mfc/document-view-creation.md) 會顯示 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) 物件如何組織建立框架視窗、文件和檢視和連接它們。  傳遞給 `CDocTemplate` 建構函式的三個 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 引數指定框架視窗，文件和動態文件範本以回應使用者命令 \(檔案功能表上的新命令或在 MDI 視窗功能表的新視窗命令的檢視類別。  在建立檢視和文件時，框架視窗文件範本儲存資訊以供日後使用。  
  
 若要正確運作 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) 的機制，必須宣告您的衍生的框架視窗 \(Frame Window\) 類別與 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 巨集。  這是因為，架構需要建立文件框架視窗使用類別 `CObject`動態建構機制。  
  
 當使用者選擇建立文件的命令時，這個架構要求文件樣板建立資料物件、檢視和將顯示檢視的框架視窗。  在建立文件框架視窗時，文件樣板建立適當的類別 \(衍生自 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) 的從 SDI 應用程式的 [CFrameWnd](../mfc/reference/cframewnd-class.md) 或類別的物件至 MDI 應用程式。  架構會呼叫框架視窗物件的 [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) 成員函式從資源取得建立資訊和建立視窗的視窗。  這個框架的視窗控制代碼框架視窗物件。  然後建立檢視，文件框架視窗的子視窗。  
  
 請注意在決定 [何時使用](../mfc/when-to-initialize-cwnd-objects.md) 的 `CWnd`衍生物件。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [從衍生類別 CObject \(其動態建立機制\)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [文件\/檢視建立 \(範本和框架視窗建立\)](../mfc/document-view-creation.md)  
  
-   [終結框架視窗](../mfc/destroying-frame-windows.md)  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)