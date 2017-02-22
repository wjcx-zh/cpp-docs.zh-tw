---
title: "處理標題控制項告知 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 處理通知"
  - "控制項 [MFC], 標題"
  - "標題控制項通知"
  - "標題控制項, 處理通知"
  - "告知, CHeaderCtrl 的處理"
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 處理標題控制項告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在您的檢視或對話方塊類別，請使用屬性視窗建立一個 switch 陳述式的 [OnChildNotify](../Topic/CWnd::OnChildNotify.md) 處理常式函式要處理的所有標題控制項 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 通知訊息的 \(請參閱 [out 此函式之對應訊息](../mfc/reference/mapping-messages-to-functions.md)\)。  通知傳送給視窗的父代，當使用者按一下或按兩下標題項目時，拖曳至功能表項目之間的分割線，依此類推。  
  
 通知訊息與標題控制項在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [標題控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb775239) 中。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)