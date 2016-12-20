---
title: "處理 Rebar 控制項中的通知訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CReBarCtrl 類別, 由其所傳送的通知訊息"
  - "告知, CReBarCtrl"
  - "RBN_ 通知訊息"
  - "RBN_ 通知訊息, 的描述"
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理 Rebar 控制項中的通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Rebar 控制項的父類別，請為任何一個您要處理的 Rebar 控制項 \(`CReBarCtrl`\) 通知訊息建立一個 switch 陳述式的 `OnChildNotify` 處理常式函式。  當使用者拖曳到 Rebar 控制項的物件、變更 Rebar 群組列的配置、刪除 Rebar 控制項的群組列等等時，就會傳送告知父視窗。  
  
 下列通知訊息可以由 Rebar 控制項物件傳送：  
  
-   **RBN\_AUTOSIZE** 當 Rebar 自動調整大小時，由 Rebar 控制項傳送 \(以 **RBS\_AUTOSIZE** 樣式建立\)。  
  
-   **RBN\_BEGINDRAG** 當使用者開始拖曳群組列時，由 Rebar 控制項傳送。  
  
-   **RBN\_CHILDSIZE** 當群組列的子視窗調整大小時，由 Rebar 控制項傳送。  
  
-   **RBN\_DELETEDBAND** 在群組列被刪除後，由 Rebar 控制項傳送。  
  
-   **RBN\_DELETINGBAND** 當群組列將要被刪除時，由 Rebar 控制項傳送。  
  
-   **RBN\_ENDDRAG** 當使用者停止拖曳群組列時，由 Rebar 控制項傳送。  
  
-   **RBN\_GETOBJECT** 當一個物件拖曳至控制項的群組列時，由 Rebar 控制項傳送 \(以 **RBS\_REGISTERDROP** 樣式建立\)。  
  
-   **RBN\_HEIGHTCHANGE** 當它的高度變更時，由 Rebar 控制項傳送。  
  
-   **RBN\_LAYOUTCHANGED** 當使用者變更控制項範圍的設定時，由Rebar 控制項傳送。  
  
 如需這些通知訊息的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 [Rebar 控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb774375) 。  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)