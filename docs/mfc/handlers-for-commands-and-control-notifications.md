---
title: "命令和控制項告知的處理常式 | Microsoft Docs"
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
  - "命令, 的處理常式"
  - "控制項 [MFC], 告知"
  - "函式 [C++], 處理常式"
  - "處理常式"
  - "處理常式, 命令"
  - "處理常式, 控制項告知"
  - "告知, 控制項的處理常式"
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 命令和控制項告知的處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

沒有命令或控制項通知訊息的預設處理常式。  因此，您可以在將只依照慣例會繫結至您的訊息這些分類的處理常式名稱。  當您將命令或控制項通知給處理常式時，屬性視窗會根據命令 ID 或控制通知程式碼的名稱。  您可以接受建議的名稱，將它變更或取代它。  
  
 慣例建議您在使用者介面物件的兩個分類將它們所表示之處理常式的名稱。  因而 Cut 命令的處理常式在編輯功能表可能會被命名  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/CPP/handlers-for-commands-and-control-notifications_1.h)]  
  
 由於應用程式會與通常會實作 Cut 命令，框架預先定義 Cut 命令的命令 ID 做為 **ID\_EDIT\_CUT**。  如需所有預先定義的命令 ID 的清單，請參閱檔案 AFXRES.H。  如需詳細資訊，請參閱[標準命令](../mfc/standard-commands.md)。  
  
 此外，慣例建議 **BN\_CLICKED** 通知訊息的處理常式標示為「My 按鈕」的按鈕可能會被命名  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/CPP/handlers-for-commands-and-control-notifications_2.h)]  
  
 因為它與特定應用程式的使用者介面物件相同，相當於您可以將這個 `IDC_MY_BUTTON` 指派給命令 ID。  
  
 兩類訊息不接受任何引數而且不會傳回值。  
  
## 請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)