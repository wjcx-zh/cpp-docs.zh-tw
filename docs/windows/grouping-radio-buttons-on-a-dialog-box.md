---
title: "Grouping Radio Buttons on a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.grouping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "member variables, adding to radio button groups"
  - "variables, dialog box control member variables"
  - "dialog box controls, grouping radio buttons"
  - "grouping controls"
  - "radio buttons, grouping on dialog boxes"
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Grouping Radio Buttons on a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在對話方塊中加入選項按鈕時，請在 \[屬性\] 視窗中為群組的第一個按鈕設定 \[群組\] 屬性，把它們當成群組處理。 然後，這個選項按鈕的控制項識別碼就會出現在 [&#91;加入成員變數精靈&#93;](../ide/add-member-variable-wizard.md) 中，讓您為選項按鈕群組加入成員變數。  
  
 對話方塊中可以有多個選項按鈕群組，但加入每個群組時請一定要使用下列程序。  
  
### 在對話方塊中加入選項按鈕群組  
  
1.  在 [&#91;工具箱&#93; 視窗](../Topic/Toolbox.md)中選取選項按鈕控制項，然後在對話方塊中按一下要放置控制項的位置。  
  
2.  重複步驟 1 加入您需要的數量無限的選項按鈕。 請確定群組中的選項按鈕的定位順序是連續的 \(如需詳細資訊，請參閱[變更控制項的定位順序](../mfc/changing-the-tab-order-of-controls.md)\)。  
  
3.  在 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)中，請將定位順序*第一*之選項按鈕的 \[群組\] 屬性設為 **True**。  
  
     將 \[群組\] 屬性變更成 **True**，可在資源指令碼之對話方塊物件的按鈕項目中加入 WS\_GROUP 樣式，確保使用者在按鈕群組中一次只能選取一個選項按鈕 \(當使用者按一下某個選項按鈕時，就會清除群組中的其他按鈕\)。  
  
    > [!NOTE]
    >  群組中，應該只有第一個選項按鈕的 \[群組\] 屬性設為 **True**。 如果有不屬於按鈕群組的其他控制項，請將*群組之外*第一個控制項的 \[群組\] 屬性也設成 **True**。 按下 CTRL\+D 檢視定位順序，即可快速識別群組之外的第一個控制項。  
  
### 加入選項按鈕群組的成員變數  
  
1.  以滑鼠右鍵按一下定位順序第一的選項按鈕控制項 \(主控項和 \[群組\] 屬性設為 True 的控制項\)。  
  
2.  從快顯功能表選擇 \[加入變數\]。  
  
3.  在 [&#91;加入成員變數精靈&#93;](../ide/add-member-variable-wizard.md) 中，選取 \[控制項變數\] 核取方塊，然後選取 \[值\] 選項按鈕。  
  
4.  在 \[變數名稱\] 方塊中，輸入新成員變數的名稱。  
  
5.  在 \[變數類型\] 清單方塊中選取 \[int\] 或輸入 **int**。  
  
6.  您現在可以修改程式碼，指定應該顯示為已選取的按鈕。 例如，m\_radioBox1 \= 0; 會選取群組中的第一個選項按鈕。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Arrangement of Controls on Dialog Boxes](../mfc/arrangement-of-controls-on-dialog-boxes.md)   
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)