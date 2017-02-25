---
title: "ExitInstance 成員函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp::ExitInstance"
  - "CWinApp.ExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp 類別, ExitInstance"
  - "ExitInstance 方法"
  - "程式 [C++], 終止"
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ExitInstance 成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinApp](../mfc/reference/cwinapp-class.md) 類別的 [ExitInstance](../Topic/CWinApp::ExitInstance.md) 成員函式在每次您的應用程式複本終止時呼叫，因為通常由使用者結束應用程式。  
  
 如果您需要特別清除處理，例如釋放繪圖裝置介面 \(Graphics Device \(GDI\) 資源或在程式執行期間使用的解除配置記憶體，則覆寫 `ExitInstance` 。  例如文件和檢視，然而，架構會提供標準項目清除，其他可覆寫的函式為做特殊清除特定給這些物件。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)