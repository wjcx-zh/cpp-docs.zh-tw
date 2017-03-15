---
title: "命令路由說明 | Microsoft Docs"
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
  - "命令處理, 傳送命令"
  - "命令傳送, OnCmdMsg 處理常式"
  - "MFC, 命令傳送"
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 命令路由說明
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了說明，請將從清除的命令訊息在 MDI 應用程式的編輯功能表的功能表項目。  假設這個命令的處理常式函式正好是應用程式的文件類別的成員函式。  這個命令的方式到達其處理常式，在使用者選取功能表項目之後:  
  
1.  主框架視窗第一次收到的命令訊息。  
  
2.  主要 MDI 框架視窗給目前現用 MDI 子視窗有機會處理命令。  
  
3.  MDI 子框架視窗的標準傳送給其檢視有機會在命令在檢查它的訊息對應之前。  
  
4.  這個檢視會先檢查它的訊息對應，在未尋找到處理常式時，下達傳送命令給相關的資料。  
  
5.  文件檢查它的訊息對應並尋找處理常式。  文件成員函式呼叫和路由中止。  
  
 如果文件沒有處理常式，它會下載路由命令到它的資料範本。  然後命令會回到檢視然後框架視窗。  最後，框架視窗中檢查它的訊息對應。  如果該檢查失敗，命令將會傳送回主要 MDI 框架視窗會對應用程式物件—未處理命令的最終目的地。  
  
## 請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)