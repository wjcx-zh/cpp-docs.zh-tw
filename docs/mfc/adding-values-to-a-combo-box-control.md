---
title: "Adding Values to a Combo Box Control | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.dialog.combo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combo boxes [C++], Data property"
  - "controls [Visual Studio], testing values in combo boxes"
  - "combo boxes [C++], adding values"
  - "combo boxes [C++], previewing values"
  - "controls [C++], testing values in combo boxes"
  - "Data property"
  - "combo boxes [C++], testing values"
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Values to a Combo Box Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可將值加入至下拉式方塊控制項，只要您開啟對話方塊編輯器。  
  
> [!TIP]
>  在對話方塊編輯器中調整方塊的大小之前，先將所有值加入至下拉式方塊是比較好的作法，這樣可以避免截斷下拉式控制項中的文字。  
  
#### 若要在下拉式方塊控制項中輸入值  
  
1.  藉著按一下來選取下拉式方塊控制項。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)中，向下捲動到 \[資料\] 屬性。  
  
    > [!NOTE]
    >  如果您要根據型別編組來顯示屬性，\[資料\] 會顯示在 \[其他\] 屬性中。  
  
3.  按一下 \[資料\] 屬性的值區，然後輸入您的資料值，以分號分隔。  
  
    > [!NOTE]
    >  請勿在值與值之間使用空格，因為空格會干擾下拉式清單中的字母排序。  
  
4.  當您加入值之後，按一下 **Enter**。  
  
 如需放大下拉式方塊的下拉式清單部分的資訊，請參閱[設定下拉式方塊和下拉式清單的大小](../mfc/setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。  
  
> [!NOTE]
>  您不能使用這個程序將值加入至 Win32 專案 \(\[資料\] 屬性在 Win32 專案是灰色的\)。  因為 Win32 專案沒有加入這項功能的程式庫，您必須以 Win32 專案的程式設計將值加入至下拉式方塊。  
  
#### 若要測試下拉式方塊中值的外觀  
  
1.  在 \[資料\] 屬性中輸入值之後，按一下[對話方塊編輯器工具列](../mfc/showing-or-hiding-the-dialog-editor-toolbar.md)上的 \[測試\] 按鈕。  
  
     嘗試往下捲動以檢視整個清單中的值。  值的顯示方式就像它們在 \[屬性\] 視窗 \[資料\] 屬性中輸入的一樣。  測試時不會檢查拼字或大小寫。  
  
     按 ESC 回到對話方塊編輯器。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 Win32  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)