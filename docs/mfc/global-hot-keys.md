---
title: "全域熱鍵 | Microsoft Docs"
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
  - "CHotKeyCtrl 類別, 全域熱鍵"
  - "全域熱鍵"
  - "鍵盤快速鍵 [C++], 熱鍵"
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 全域熱鍵
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

全域快速鍵與特定 nonchild 視窗。  它可讓使用者啟動從系統的任何部分的視窗。  應用程式會傳送 [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) 訊息設定特定視窗的全域熱鍵到該視窗。  例如，如果， `m_HotKeyCtrl` 是 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) 物件，而 `pMainWnd` 是指標到視窗中啟動，則快速鍵時，可以使用下列程式碼關聯控制項中指定的快速鍵與視窗所指向的 `pMainWnd`。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/CPP/global-hot-keys_1.cpp)]  
  
 當使用者按下全域快速鍵，視窗指定接收指定 **SC\_HOTKEY** 當做命令的 [WM\_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) 訊息。  這個訊息也會啟用接收到的視窗。  由於這個訊息未包含所按的按鍵的任何資訊，使用這個方法不允許差異可能附加至同一個視窗中的差異熱鍵之間。  快速鍵保持有效直到傳送 **WM\_SETHOTKEY** 匯出的應用程式。  
  
## 請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)