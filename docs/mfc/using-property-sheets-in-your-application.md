---
title: "在應用程式中使用屬性工作表 | Microsoft Docs"
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
  - "AddPage 方法"
  - "CPropertyPage 類別, 樣式"
  - "Create 方法 [C++], 屬性工作表"
  - "對話方塊資源"
  - "對話方塊範本, 屬性工作表"
  - "DoModal 方法屬性工作表"
  - "屬性頁, 屬性工作表"
  - "屬性工作表, 關於屬性工作表"
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在應用程式中使用屬性工作表
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用屬性工作表在您的應用程式，請完成下列步驟:  
  
1.  建立每個屬性頁的對話方塊範本資源。  記住使用者可能轉換一頁到另一個，因此，盡可能相同一致地規劃每頁。  
  
     所有頁面的對話方塊範本不需要有相同的大小。  架構會使用最大頁面的大小決定配置多少空間屬性上的屬性工作表呼叫。  
  
     當您建立屬性頁時對話方塊樣板資源，您必須在對話方塊屬性屬性工作表指定下列模式:  
  
    -   設定 **General** 頁面的 **Caption** 編輯方塊對您希望出現在頁面上的選項的文字。  
  
    -   設定在 **Styles** 頁面的 **Style** 清單方塊對 **Child**。  
  
    -   設定在 **Styles** 頁面的 **Border** 清單方塊對 **Thin**。  
  
    -   確定選取在 **Styles** 頁面的 **Titlebar** 核取方塊。  
  
    -   確定選取在 **More Styles** 頁面的 **Disabled** 核取方塊。  
  
2.  建立 [CPropertyPage](../mfc/reference/cpropertypage-class.md) 衍生類別與每個屬性頁對話方塊範本對應。  請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md)。  選取 `CPropertyPage` 做為基底類別。  
  
3.  建立成員變數來保存這個屬性頁的值。  因為屬性頁是特定對話方塊，加入成員變數傳入屬性頁完全相同。將成員變數加入至對話方塊。  如需詳細資訊，請參閱 [定義對話方塊控制項的成員變數](../mfc/defining-member-variables-for-dialog-controls.md)。  
  
4.  建構一個 [CPropertySheet](../mfc/reference/cpropertysheet-class.md) 物件在原始程式碼。  通常，您可以在處理常式的 `CPropertySheet` 物件顯示屬性工作表的命令。  這個物件代表整個屬性工作表。  如果您使用 [DoModal](../Topic/CPropertySheet::DoModal.md) 建立函式的強制回應屬性工作表，根據預設架構提供三個命令按鈕: 好、移除和同意。  架構不建立非強制回應屬性工作表的按鈕會使用 [建立](../Topic/CPropertySheet::Create.md) 函式。  您不需要衍生自 `CPropertySheet` 的類別，除非您要加入其他控制項 \(例如預覽視窗\) 或顯示非強制回應的屬性工作表。  此步驟為非強制回應的屬性工作表是必要的，因為它們不包含可以用來關閉屬性工作表的任何預設控制項。  
  
5.  對於每個頁面加入至屬性工作表，請執行下列步驟:  
  
    -   在這個程序建立之前建構 `CPropertyPage`衍生類別的每一個物件。  
  
    -   在每個網頁上呼叫 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md) 。  
  
     通常，建立 `CPropertySheet` 的物件會在這個步驟建立 `CPropertyPage` 物件。  不過，如果您實作 `CPropertySheet`衍生類別，您可以在 `CPropertySheet` 物件上的 `CPropertyPage` 物件和呼叫每個頁面的 `AddPage` 從 `CPropertySheet`衍生類別的建構函式。  `AddPage` 中加入頁面屬性工作表清單的 `CPropertyPage` 物件，但實際上不會建立該頁面的視窗。  因此，等候直到屬性工作表視窗的建立 `AddPage`呼叫是不必要的;您可以從屬性工作表的建構函式的 `AddPage` 呼叫。  
  
     根據預設，如果屬性工作表會符合屬性工作表中有更多選項單行，選項在多行將堆疊。  若要停用堆疊，請呼叫 [CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md) 將參數設定為 **FALSE**。  在建立屬性工作表時，您必須呼叫 `EnableStackedTabs` 。  
  
6.  呼叫 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 或 [建立](../Topic/CPropertySheet::Create.md) 顯示屬性工作表。  呼叫 `DoModal` 來建立屬性工作表為強制回應對話方塊。  呼叫 **Create** 建立屬性工作表為非強制回應對話方塊。  
  
7.  在屬性頁和屬性工作表的擁有人之間交換資料。  這在文件 [交換資料](../mfc/exchanging-data.md)中說明。  
  
 如需如何使用屬性工作表，請參閱 MFC 一般 [PROPDLG](../top/visual-cpp-samples.md)範例。  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)