---
title: "加入事件處理常式 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件處理常式, 加入"
  - "MSBuild, 屬性"
  - "屬性 [Visual Studio], MSBuild"
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入事件處理常式 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可在資源編輯器中，為使用[事件處理常式精靈](../ide/event-handler-wizard.md)的對話方塊控制項，加入新的事件處理常式或編輯現有的事件處理常式。  
  
 您可以使用[屬性視窗](../Topic/Properties%20Window.md)，將事件加入至實作對話方塊的類別。  如果您想要將事件加入至對話方塊類別以外的類別，請使用事件處理常式精靈。  
  
### 若要將事件處理常式加入至對話方塊控制項  
  
1.  在[資源檢視](../windows/resource-view-window.md)裡按兩下對話方塊資源，將包含控制項的對話方塊資源開啟於[對話方塊編輯器](../mfc/dialog-editor.md)中。  
  
2.  在您要處理通知事件的控制項上按一下滑鼠右鍵。  
  
3.  在捷徑功能表上按一下 \[**加入事件處理常式**\] 來顯示事件處理常式精靈。  
  
4.  在 \[訊息類型\] 方塊中選取要加入至 \[類別清單\] 方塊內選取類別的事件。  
  
5.  接受 \[函式處理常式名稱\] 方塊裡的預設名稱，或者提供您選擇的名稱。  
  
6.  按一下 \[加入並編輯\]，將事件處理函式加入至專案中，並將新增的函式以文字編輯器開啟，以加入適當的事件處理常式程式碼。  
  
     如果選取的訊息類型對於所選的類別已有事件處理常式，就只能使用 \[編輯程式碼\] 而無法使用 \[加入並編輯\]。  按一下 \[編輯程式碼\] 將現有的函式於文字編輯器開啟。  
  
 除此之外，您可以由[屬性視窗](../Topic/Properties%20Window.md)加入事件處理常式。  如需詳細資訊，請參閱[加入對話方塊控制項的事件處理常式](../mfc/adding-event-handlers-for-dialog-box-controls.md)。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)