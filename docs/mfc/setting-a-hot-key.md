---
title: "設定熱鍵 | Microsoft Docs"
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
  - "便捷鍵 [C++], 熱鍵"
  - "CHotKeyCtrl 類別, 設定熱鍵"
  - "鍵盤快速鍵 [C++], 熱鍵"
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 設定熱鍵
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的應用程式可以使用快速鍵控制項 \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) 提供的下列其中一種資訊的方式:  
  
-   要經由傳送 [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) 訊息設定啟動的 nonchild 視窗全域熱鍵到要啟動的視窗。  
  
-   藉由呼叫 Windows 函式設定一個執行緒特定熱鍵 [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309)。  
  
## 請參閱  
 [使用 CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [控制項](../mfc/controls-mfc.md)