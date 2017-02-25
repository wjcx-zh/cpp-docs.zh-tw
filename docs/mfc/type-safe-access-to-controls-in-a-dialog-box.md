---
title: "對話方塊中之控制項的類型安全存取 | Microsoft Docs"
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
  - "通用控制項 [C++], 在對話方塊中"
  - "控制項 [MFC], 存取對話方塊中的"
  - "對話方塊 [C++], 控制項的類型安全存取"
  - "MFC 對話方塊, 控制項的類型安全存取"
  - "對話方塊控制項的安全存取"
  - "對話方塊控制項的類型安全存取"
  - "Windows 通用控制項 [C++], 在對話方塊中"
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 對話方塊中之控制項的類型安全存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對話方塊中的控制項可以使用 MFC 控制項類別的介面，例如 `CListBox` 和 `CEdit`。  您可以建立控制項物件，並將它附加至對話方塊控制項。  然後可以透過其類別介面來存取該控制項，呼叫成員函式以便在控制項上作業。  這裡所述的方法是專門設計來提供對控制項的型別安全存取。  這對於編輯方塊和清單方塊之類的控制項而言特別實用。  
  
 有兩個方法可以建立對話方塊中控制項和 `CDialog` 衍生類別中 C\+\+ 控制項成員變數之間的連接：  
  
-   [不使用程式碼精靈](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [使用程式碼精靈](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)