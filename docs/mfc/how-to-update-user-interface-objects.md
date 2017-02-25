---
title: "如何：更新使用者介面物件 | Microsoft Docs"
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
  - "命令, 更新 UI"
  - "停用功能表"
  - "停用 UI 項目"
  - "啟用功能表"
  - "啟用 UI 項目"
  - "功能表, 更新為內容變更"
  - "更新處理常式"
  - "更新使用者介面物件"
  - "使用者介面物件"
  - "使用者介面物件, 更新"
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何：更新使用者介面物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通常，功能表項目和工具列按鈕有一種以上的狀態。  例如，功能表項目變成灰色 \(文件\)，則無法在目前的內容。  功能表項目也可以是已核取或未核取。  工具列按鈕也可以停用，否則無法使用，也可以是已核取。  
  
 當程式條件變更，了解更新這些項目狀態?  邏輯，則為，如果功能表項目產生文件所處理的命令，因此才會將文件更新功能表項目。  文件可能包含更新的資訊。  
  
 如果命令具有多使用者介面物件 \(可能是功能表項目和工具列按鈕\)，會傳送至相同處理函式。  這在單一位置封裝所有的使用者介面更新程式碼的使用者介面物件。  
  
 這個架構自動更新使用者介面物件提供方便的介面。  您可以選擇執行更新的其他方法，不過，提供的介面是有效率且容易使用的。  
  
 下列主題將說明使用更新處理常式:  
  
-   [呼叫更新處理常式的時機](../mfc/when-update-handlers-are-called.md)  
  
-   [ON\_UPDATE\_COMMAND\_UI 巨集](../mfc/on-update-command-ui-macro.md)  
  
-   [CCmdUI 類別](../mfc/the-ccmdui-class.md)  
  
## 請參閱  
 [Menus](../mfc/menus-mfc.md)