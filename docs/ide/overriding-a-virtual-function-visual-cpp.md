---
title: "覆寫 Virtual 函式 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.virtualfunc.override"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基底類別, 覆寫定義的虛擬函式"
  - "屬性視窗, 覆寫虛擬函式"
  - "虛擬函式, 覆寫"
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 覆寫 Virtual 函式 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在 Visual Studio [屬性視窗](../Topic/Properties%20Window.md)中覆寫基底類別中定義的虛擬函式 \(Virtual Function\)。  
  
### 若要在屬性視窗中覆寫 Virtual 函式  
  
1.  在 \[類別檢視\] 中，按一下類別。  
  
2.  在 \[屬性\] 視窗中，按一下 \[**覆寫**\] 按鈕。  
  
    > [!NOTE]
    >  在 \[類別檢視\] 中選取類別名稱或在來源視窗內按一下時，\[**覆寫**\] 按鈕就可使用。  
  
     左欄列出 Virtual 函式。  如果 Virtual 函式名稱也出現在右欄中，則已經實作覆寫。  
  
3.  如果函式沒有覆寫，則按一下 \[屬性\] 視窗右欄中的儲存格，以顯示如 \[\<加入\> *FuncName*\] 的函式覆寫建議名稱。  
  
4.  按一下建議的名稱，加入函式的 Stub 程式碼。  
  
5.  若要編輯覆寫函式，按兩下 \[類別檢視\] 中的函式名稱，然後編輯來源視窗中的程式碼。  
  
 若要移除覆寫，請按一下右欄中的覆寫函式名稱並選取 \[\<刪除\> *FuncName*\]。  函式的程式碼將被轉為註解。  
  
## 請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)