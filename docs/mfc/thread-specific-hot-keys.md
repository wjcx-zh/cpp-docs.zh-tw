---
title: "執行緒特定的熱鍵 | Microsoft Docs"
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
  - "便捷鍵 [C++], 熱鍵"
  - "CHotKeyCtrl 類別, 執行緒特定的熱鍵"
  - "鍵盤快速鍵 [C++], 熱鍵"
  - "執行緒 [C++], CHotKeyCtrl 中的熱鍵"
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 執行緒特定的熱鍵
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

應用程式設定一個執行緒特定的快速鍵 \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) 使用視窗 **RegisterHotKey** 函式。  當使用者按下某個執行緒特定的快速鍵時， Windows 會宣告 [WM\_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) 訊息至特定執行緒的訊息佇列的開頭。  **WM\_HOTKEY** 訊息包含已按下特定快速鍵的虛擬按鍵碼、傳輸狀態和使用者定義的 ID。  如需標準虛擬按鍵碼的清單，請參閱 Winuser.h。  如需這個方法的詳細資訊，請參閱 [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
 請注意在呼叫傳輸狀態旗標對 **RegisterHotKey** 與 [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) 成員函式傳回的項目;您必須在呼叫 **RegisterHotKey**目前轉譯這些旗標。  
  
## 請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)