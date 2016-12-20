---
title: "建立主動式文件容器應用程式 | Microsoft Docs"
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
  - "主動式文件容器 [C++], 建立"
  - "主動式文件 [C++], 容器"
  - "應用程式 [MFC], 主動式文件容器"
  - "容器 [C++], 主動式文件"
  - "MFC COM [C++], 主動式文件內含項目"
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立主動式文件容器應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

最簡單和建議的方式建立主動式文件容器應用程式會建立 MFC EXE 容器應用程式使用 MFC 應用程式精靈，然後修改應用程式支援主動式文件內含項目。  
  
#### 建立主動式文件容器應用程式  
  
1.  從 \[**檔案**\] 功能表中，從 \[**新增**\] 子功能表中按一下 \[**專案**\]。  
  
2.  從左窗格中，按一下 \[**Visual C\+\+**\] 專案類型。  
  
3.  選取 \[**MFC 應用程式**\] 從右窗格。  
  
4.  將專案 `MyProj`，按一下 \[**好**\]。  
  
5.  選取 \[**複合文件支援**\] 頁面。  
  
6.  選取 \[**容器**\] 或 \[**容器\/全伺服器**\] 索引標籤。  
  
7.  選取 \[**主動式文件容器**\] 核取方塊。  
  
8.  按一下 \[**完成**\]。  
  
9. 在 MFC 應用程式精靈完成產生應用程式時，使用方案總管中，開啟下列檔案:  
  
    -   MyProjview.cpp  
  
10. 在 MyProjview.cpp，進行下列變更:  
  
    -   以下面程式碼取代 `CMyProjView::OnPreparePrinting` 區段中的程式碼：  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/CPP/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting` 提供列印支援。  這個程式碼取代 `DoPreparePrinting`，這是預設的列印準備。  
  
     現用文件內含項目提供一份增強列印的配置:  
  
    -   您可以透過其 `IPrint`介面可以先呼叫現用文件和告知列印。  這是與上一個 OLE 內含項目不同，必須裝載在容器中呈現包含項目影像在印表機 `CDC`物件上的。  
  
    -   如果失敗，請呼叫包含項目透過其 `IOleCommandTarget`介面列印  
  
    -   如果失敗，請進行轉換項目。  
  
     靜態成員函式 `COleDocObjectItem::OnPrint` 和 `COleDocObjectItem::OnPreparePrinting`，以實作上一個程式碼，處理這個增強列印的計劃。  
  
11. 將所有實作加入並建立應用程式。  
  
## 請參閱  
 [主動式文件內含項目](../mfc/active-document-containment.md)