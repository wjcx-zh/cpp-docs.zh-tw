---
title: "Defining Member Variables for Dialog Controls | Microsoft Docs"
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
  - "member variables, defining for controls"
  - "variables, dialog box control member variables"
  - "controls [C++], member variables"
  - "Dialog editor, defining member variables for controls"
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Defining Member Variables for Dialog Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要定義任何對話方塊控制項 \(按鈕除外\) 的成員變數，您可以使用下列方法。  
  
> [!NOTE]
>  本文只適用於 MFC 專案內的對話方塊控制項。  ATL 專案應使用 \[**新增 Windows 訊息和事件處理常式**\] 對話方塊。  
  
### 定義對話方塊控制項的成員變數 \(非按鈕\)  
  
1.  在 \[[對話方塊編輯器](../mfc/dialog-editor.md)\] 中，選取控制項。  
  
2.  按 **CTRL** 鍵時，請按兩下對話方塊控制項。  
  
     [加入成員變數精靈](../ide/add-member-variable-wizard.md)隨即出現。  
  
3.  在 \[**加入成員變數**\] 精靈中輸入適當的資訊。  如需詳細資訊，請參閱[對話資料交換](../mfc/dialog-data-exchange.md)。  
  
4.  按一下 \[**確定**\] 返回對話方塊編輯器。  
  
    > [!TIP]
    >  若要從任何對話方塊控制項跳至其現有的處理常式，請按兩下控制項。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 您也可以使用 \[**MFC 類別精靈**\] 中的 \[**成員變數**\] 索引標籤，加入指定類別的新成員變數，並檢視已經定義的成員變數。  
  
 需求  
  
 MFC  
  
## 請參閱  
 [將訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [MFC 類別精靈](../mfc/reference/mfc-class-wizard.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)