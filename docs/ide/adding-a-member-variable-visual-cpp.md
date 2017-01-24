---
title: "加入成員變數 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.classes.member.variable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "成員變數"
  - "成員變數, 加入"
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入成員變數 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 \[類別檢視\] 將成員變數 \(Member Variable\) 加入至類別 \(Class\)。  成員變數可能是做為[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)之用，或只是一般用途。  資料成員變數精靈是特別設計來擷取相關資訊以在原始程式檔的適當位置插入某些項目。  您可以從[資源檢視](../windows/resource-view-window.md)內的[對話方塊編輯器](../mfc/dialog-editor.md)，或者從[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)加入成員變數。  
  
> [!NOTE]
>  設計和實作對話方塊時，您可以發現使用對話方塊編輯器加入對話方塊控制項，然後實作這些控制項的成員變數是較有效的方法。  
  
### 若要使用加入成員變數精靈在資源檢視加入對話方塊控制項的成員變數  
  
1.  在 \[資源檢視\] 中，展開專案節點和對話方塊節點以顯示該專案的對話方塊清單。  
  
2.  按兩下您想加入成員變數的對話方塊，以便在對話方塊編輯器中開啟。  
  
3.  在對話方塊編輯器內顯示的對話方塊中，以滑鼠右鍵按一下您要加入成員變數的控制項。  
  
4.  在捷徑功能表上，按一下 \[**加入變數**\] 以顯示[加入成員變數精靈](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  \[控制項 ID\] 中已提供預設值。  
  
5.  在適當的精靈方塊中提供資訊。  如需詳細資訊，請參閱[對話方塊控制項和變數型別](../ide/dialog-box-controls-and-variable-types.md)。  
  
6.  按一下 \[完成\] 將定義和實作程式碼加入專案並關閉精靈。  
  
### 若要使用加入成員變數精靈自類別檢視加入成員變數  
  
1.  在[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，將專案節點展開以顯示專案中的類別。  
  
2.  在您要加入變數的類別上按一下滑鼠右鍵。  
  
3.  在捷徑功能表上，按一下 \[加入\]，然後按 \[**加入變數\]** 以顯示 \[加入成員變數精靈\]。  
  
4.  在適當的精靈方塊中提供資訊。  如需詳細資訊，請參閱[加入成員變數精靈](../ide/add-member-variable-wizard.md)。  
  
5.  按一下 \[完成\] 將定義和實作程式碼加入專案並關閉精靈。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)