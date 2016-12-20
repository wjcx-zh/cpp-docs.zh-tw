---
title: "根據新控制項類別來宣告變數 | Microsoft Docs"
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
  - "vc.codewiz.classes.control.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], 宣告變數根據"
  - "控制項類別, 變數"
  - "變數, 控制項類別"
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 根據新控制項類別來宣告變數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立 MFC 控制項類別之後，您就可根據它來宣告變數。  若要提供新變數的內容，您必須開始對話方塊編輯器並編輯所要重複使用控制項的對話方塊。  而且，對話方塊必須具有與之關聯的類別。  如需使用對話方塊編輯器的詳細資訊，請參閱[對話方塊編輯器](../../mfc/dialog-editor.md)。  
  
### 若要根據您重複使用的類別來宣告變數  
  
1.  當編輯對話方塊時，將與您新控制項的基底類別同一型別的控制項從 \[控制項\] 工具列拖曳到對話方塊。  
  
2.  將滑鼠指標移至所拖曳的控制項上。  
  
3.  在按下 CTRL 按鍵的同時，按兩下控制項。  
  
     出現[加入成員變數](../../ide/add-member-variable-wizard.md)對話方塊。  
  
4.  在 \[存取\] 方塊中，選取控制項的正確存取。  
  
5.  按一下 \[控制項變數\] 核取方塊。  
  
6.  在 \[變數名稱\] 方塊中，輸入名稱。  
  
7.  在 \[類別\] 下，按一下 \[控制項\]。  
  
8.  在 \[控制項 ID\] 清單中，選取您加入的控制項。  \[變數型別\] 清單應顯示正確的變數型別，並且 \[控制項型別\] 應顯示正確的控制項型別。  
  
9. 在 \[註解\] 方塊中，加入您想要在程式碼中出現的任何註解。  
  
10. 按一下 \[**確定**\]。  
  
## 請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)