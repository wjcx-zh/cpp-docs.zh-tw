---
title: "Dialog Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.dialog"
  - "vc.editors.dialog.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resource editors, Dialog editor"
  - "editors, dialog boxes"
  - "Dialog editor"
  - "dialog boxes, editing"
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Dialog Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對話方塊編輯器可讓您建立或編輯對話方塊資源。 在 \[資源檢視\] 視窗 \(\[檢視 &#124; 資源檢視\]\)，按兩下對話方塊的 .rc 檔，即可開啟對話方塊編輯器。 請注意，\[資源檢視\] 在 Express 版中無法使用。  
  
 建立新對話方塊 \(或對話方塊範本\) 的前幾個步驟之一，是在對話方塊中加入控制項。 在對話方塊編輯器中，您可以安排控制項配合特定的大小、圖形或對齊方式，或者在對話方塊內隨意移動它們以便工作。 刪除控制項也很容易。  
  
 您可以將對話方塊儲存成範本，以便重複使用。 您也可以輕鬆地在設計對話方塊和編輯其實作程式碼之間來回切換。  
  
 在對話方塊編輯器中也可以編輯單一或多個控制項的屬性。 您可以變更定位順序，也就是按下 TAB 鍵時，取得焦點的控制項的順序，或者您可以定義便捷鍵 \(按鍵組合\)，讓使用者選擇使用鍵盤的控制項。 如需預設的便捷鍵清單，請參閱[對話方塊編輯器的快速鍵](../mfc/accelerator-keys-for-the-dialog-editor.md)。  
  
 對話方塊編輯器也讓您使用自訂控制項，包括 ActiveX 控制項。 此外，您可以編輯[表單檢視](../mfc/reference/cformview-class.md)、[資料錄檢視表](../data/record-views-mfc-data-access.md)或[對話方塊列](../mfc/dialog-bars.md)。  
  
 從 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 開始，您可以使用對話方塊編輯器定義動態的版面配置，在使用者調整對話方塊大小時，指定控制項移動和調整大小的方式。 如需詳細資訊，請參閱[動態版面配置](../mfc/dynamic-layout.md)。  
  
-   [建立新的對話方塊](../mfc/creating-a-new-dialog-box.md)  
  
-   [建立使用者在執行階段無法結束的對話方塊](../mfc/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [顯示或隱藏對話方塊編輯器工具列](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [切換對話方塊編輯器和程式碼](../mfc/switching-between-dialog-box-controls-and-code.md)  
  
-   [對話方塊中的控制項](../mfc/controls-in-dialog-boxes.md)  
  
-   [加入對話方塊控制項的事件處理常式](../mfc/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [測試對話方塊](../mfc/testing-a-dialog-box.md)  
  
-   [對話方塊編輯器的快速鍵](../mfc/accelerator-keys-for-the-dialog-editor.md)  
  
-   [對話方塊編輯器的疑難排解](../mfc/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  使用對話方塊編輯器時，在許多情況下，按一下滑鼠右鍵可以顯示常用命令的捷徑功能表。  
  
 如需將資源加入 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)   
 [控制項](../mfc/controls-mfc.md)   
 [控制項類別](../mfc/control-classes.md)   
 [對話方塊類別](../mfc/dialog-box-classes.md)   
 [對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)