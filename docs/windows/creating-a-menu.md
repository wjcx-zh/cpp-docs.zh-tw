---
title: "Creating a Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.menu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mnemonics, associating menu items"
  - "menus, associating commands with mnemonic keys"
  - "menus, creating"
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Creating a Menu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  資源視窗在 Express 版中無法使用。  
  
### 建立標準功能表  
  
1.  按一下 \[**檢視**\] 功能表上的 \[**資源檢視**\]，然後以滑鼠右鍵按一下 \[**功能表**\] 標題並選擇 \[**加入資源**\]。 選擇 \[**功能表**\]。  
  
2.  在功能表列上選取 \[新增項目\] 方塊 \(有「在這裡輸入」的矩形\)。  
  
     ![功能表編輯器中的新增項目方塊](../windows/media/vcmenueditornewitembox.png "vcMenuEditorNewItemBox")  
新增項目方塊  
  
3.  輸入新功能表的名稱，例如「檔案」。  
  
     您輸入的文字會出現在**功能表**編輯器和 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)中的 \[標題\] 方塊中。 您可以在任一位置編輯新功能表的屬性。  
  
     一旦在功能表列上指定了新的功能表名稱，\[新增項目\] 方塊就會右移 \(讓您加入另一個功能表\)，並在第一個功能表底下開啟另一個 \[新增項目\] 方塊，讓您加入功能表命令。  
  
     ![展開的新增項目方塊](../windows/media/vcmenueditornewitemboxexpanded.png "vcMenuEditorNewItemBoxExpanded")  
輸入功能表名稱之後，\[新增項目\] 方塊的焦點會移位  
  
    > [!NOTE]
    >  若要在功能表列上建立單一項目的功能表，請將快顯視窗屬性設定為 False。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Menu Editor](../mfc/menu-editor.md)