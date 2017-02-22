---
title: "使用 CHotKeyCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl 類別, 使用"
  - "熱鍵控制項"
  - "索引鍵, 熱鍵和 CHotKeyCtrl"
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用 CHotKeyCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

熱鍵控制項，由 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)類別，是顯示這個組合鍵文字表示使用者輸入到其中的視窗，例如 CTRL\+SHIFT\+Q。  它也會維護這個機碼中的一個內部表示以虛擬按鍵碼和表示傳輸狀態的旗標集的形式。  熱鍵控制項不會實際設定快速鍵—這麼做是程式碼所決定。\(標準虛擬按鍵碼的清單，請參閱 Winuser.h。\)  
  
 使用熱鍵控制項可讓使用者輸入以哪個快速鍵可以與視窗或執行緒。  當要求使用者指派熱鍵時，熱鍵控制項通常用在對話方塊中，就可能會顯示。  為您的程式會負責從熱鍵控制項擷取描述快速鍵的值和呼叫適當的函式使快速鍵與視窗或執行緒。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [使用熱鍵控制項](../mfc/using-a-hot-key-control.md)  
  
-   [設定熱鍵](../mfc/setting-a-hot-key.md)  
  
-   [全域熱鍵](../mfc/global-hot-keys.md)  
  
-   [執行緒特定的熱鍵](../mfc/thread-specific-hot-keys.md)  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)