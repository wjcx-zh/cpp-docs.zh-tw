---
title: "ON_UPDATE_COMMAND_UI 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_UPDATE_COMMAND_UI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令處理常式巨集"
  - "ON_UPDATE_COMMAND_UI 巨集"
  - "更新處理常式"
  - "更新使用者介面物件"
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ON_UPDATE_COMMAND_UI 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 \[**屬性**\] 視窗連接使用者介面物件至命令目標物件的更新命令處理常式。  它會自動連接使用者介面物件的 ID 至 `ON_UPDATE_COMMAND_UI` 巨集，並在將處理更新的物件中建立處理常式。  如需詳細資訊，請參閱 [將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)。  
  
 例如，若要更新程式的編輯功能表中的清除所有命令，請使用 \[**屬性**\] 視窗加入所選擇的類別之訊息對應項目、呼叫類別中更新命令處理常式的函式宣告 \(名稱為 `OnUpdateEditClearAll`\) 以及類別的實作檔中的空函式範本。  函式原型如下所示：  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/CPP/on-update-command-ui-macro_1.h)]  
  
 就像所有處理常式，這個函式會顯示 **afx\_msg** 關鍵字。  就像所有更新處理常式，它會採用一個引數，一個指向 `CCmdUI` 物件的指標。  
  
## 請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)