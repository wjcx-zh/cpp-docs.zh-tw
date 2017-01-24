---
title: "管理目前的檢視 | Microsoft Docs"
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
  - "框架視窗中目前的檢視"
  - "停用檢視"
  - "框架視窗, 目前檢視"
  - "OnActivateView 方法"
  - "檢視, 啟動"
  - "檢視, 和 OnActivateView 方法"
  - "檢視, 目前的"
  - "檢視, 停用"
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 管理目前的檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

做為框架視窗的預設實作中，框架視窗記錄一個目前作用中的檢視。  如果框架視窗包含一個以上的檢視，例如在分隔視窗，目前檢視是這個最近檢視在使用中。  現用檢視表是使用中視窗的獨立在視窗或目前輸入焦點。  
  
 當現用檢視變更時，架構會呼叫它的 [OnActivateView](../Topic/CView::OnActivateView.md) 成員函式告知目前的檢視。  您可以判斷是否啟動或檢查 `OnActivateView` `bActivate` 參數停用檢視。  根據預設， `OnActivateView` 將焦點設定在啟動的目前檢視。  您可以覆寫 `OnActivateView` 執行任何特殊處理時停用檢視或重新啟動。  例如，您可能想要提供特殊視覺提示與其他差異現用檢視表，非現用檢視表。  
  
 框架視窗傳送命令給它的目前\(使用中 \) 做為標準命令路由中檢視，如 [命令路由](../mfc/command-routing.md)中所述。  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)