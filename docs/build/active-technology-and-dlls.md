---
title: "Active 技術和 DLL | Microsoft Docs"
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
  - "Active 技術 [C++]"
  - "Automation [C++], DLL"
  - "DLL [C++], Active 技術"
  - "同處理序伺服器 DLL"
  - "MFC DLL [C++], Active 技術"
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Active 技術和 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Active 技術可以讓物件伺服程式完整地實作於 DLL 內。  這類型的伺服程式稱為同處理序伺服程式 \(In\-Process Server\)。  MFC 之所以沒有對所有的視覺編輯功能完整地支援同處理序伺服程式，主要是因為 Active 技術沒有提供讓伺服程式攔截 \(Hook\) 容器 \(Container\) 主訊息迴圈的方式。  MFC 需要存取容器應用程式 \(Container Application\) 的訊息迴圈以處理快速鍵 \(Accelerator Key\) 和閒置時間處理。  
  
 然而，如果您正在撰寫 Automation 伺服程式，且您的伺服程式沒有使用者介面，您可以將您的伺服程式製作成為一個同處理序伺服程式，並將其完整地置入 DLL 裡。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [Automation 伺服程式](../mfc/automation-servers.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)