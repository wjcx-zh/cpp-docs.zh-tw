---
title: "使用工具列控制項 | Microsoft Docs"
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
  - "CToolBarCtrl 類別, 存取工具列"
  - "GetToolBarCtrl 方法"
  - "工具列控制項 [MFC], 存取"
  - "工具列 [C++], 存取通用控制項"
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 使用工具列控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何存取 [CToolBar](../mfc/reference/ctoolbar-class.md) 下的 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件以進一步控制工具列。  這是進階主題。  
  
## 程序  
  
#### 若要存取您的 CToolBar 物件之下的工具列通用控制項  
  
1.  呼叫 [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md)。  
  
 `GetToolBarCtrl` 傳回至 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件的參考。  您可以使用對呼叫工具列控制項類別的成員函式的參考。  
  
> [!CAUTION]
>  雖然在呼叫 `CToolBarCtrl` 函式**Get** 是安全的，如果您呼叫 **Set** 函式要特別小心。  這是進階主題。  通常您不需要存取基礎工具列控制項。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [控制 \(Windows 通用控制項\)](../mfc/controls-mfc.md)  
  
-   [工具列基本概念](../mfc/toolbar-fundamentals.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [動態調整工具列大小](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具列工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [Flyby 狀態列更新](../mfc/toolbar-tool-tips.md)  
  
-   [處理工具提示告知](../mfc/handling-tool-tip-notifications.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 類別  
  
-   [處理自訂告知](../mfc/handling-customization-notifications.md)  
  
-   [多個工具列](../mfc/toolbar-fundamentals.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
-   [控制列](../mfc/control-bars.md)  
  
 如需使用 Windows 通用控制項的一般資訊，請參閱 [通用控制項](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
## 請參閱  
 [MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)