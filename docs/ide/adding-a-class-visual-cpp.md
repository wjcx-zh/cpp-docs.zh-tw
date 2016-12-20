---
title: "加入類別 (Visual C++) | Microsoft Docs"
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
  - "vc.codewiz.classes.adding"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入類別"
  - "類別 [C++], 加入"
  - "類別 [C++], 建立"
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入類別 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在 Visual C\+\+ 專案中加入類別，請在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，按一下 \[**加入**\]，然後按一下 \[**類別**\]。  這樣會開啟[加入類別對話方塊](../ide/add-class-dialog-box.md)對話方塊。  
  
 當加入類別時，您所指定的類別名稱必須不同於 MFC 或 ATL 中已存在的類別名稱。  如果您所指定的類別名稱已存在於任何這些類別庫，則 Visual C\+\+ 會顯示訊息，表示所指定的類別名稱是保留的名稱。  
  
 如果您的專案命名慣例要求使用現有名稱，則可只變更名稱中一個或多個字母的大小寫，因為 Visual C\+\+ 會區分大小寫。  例如，雖然無法將類別命名為 `CDocument`，但可以將類別命名為 `cdocument`。  
  
## 您要加入什麼類型的類別？  
 在 \[**加入類別**\] 對話方塊中，當您展開左窗格的 \[**Visual C\+\+**\] 節點時，會顯示數個已安裝範本群組。  這些群組包括 **CLR**、**ATL**、**MFC** 和 **C\+\+**。  當您選取群組時，中間窗格會列出該群組中的可用範本。  每個範本都包含某個類別所需的檔案和原始程式碼。  
  
 若要產生新類別，請在中間窗格選取某個範本，在 \[**名稱**\] 方塊中輸入類別名稱，然後按一下 \[**加入**\]。  這樣會開啟 **\[加入類別精靈\]** 對話方塊，讓您可以指定類別的選項。  
  
-   如需如何建立 MFC 類別的詳細資訊，請參閱[MFC 類別](../mfc/reference/adding-an-mfc-class.md)。  
  
-   如需如何建立 ATL 類別的詳細資訊，請參閱[ATL Simple Object](../atl/reference/adding-an-atl-simple-object.md)。  
  
> [!NOTE]
>  \[**將 ATL 支援加入至 MFC**\] 範本不會建立類別，而是設定專案使用 ATL。  如需詳細資訊，請參閱[MFC 專案中的 ATL 支援](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
 若要建立不使用 MFC、ATL 或 CLR 的 C\+\+ 類別，請使用 \[**C\+\+**\] 這個已安裝範本群組中的 \[**C\+\+ 類別**\] 範本。  如需詳細資訊，請參閱[加入泛型 C\+\+ 類別](../ide/adding-a-generic-cpp-class.md)。  
  
 有兩種表單架構 C\+\+ 類別可供使用。  第一個 [CFormView Class](../mfc/reference/cformview-class.md) 會建立 MFC 類別，  第二個會建立 CLR 類別 Windows Form 類別。  
  
## 請參閱  
 [建立表單架構的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [加入類別對話方塊](../ide/add-class-dialog-box.md)   
 [使用應用程式精靈建立桌面專案](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)