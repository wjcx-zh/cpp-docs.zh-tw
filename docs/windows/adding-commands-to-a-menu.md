---
title: "Adding Commands to a Menu | Microsoft Docs"
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
  - "vc.editors.menu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "menu items, adding to menus"
  - "menus, adding items"
  - "commands, adding to menus"
  - "commands"
  - "menu items"
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Commands to a Menu
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 將命令新增至功能表  
  
1.  [建立功能表](../windows/creating-a-menu.md)。  
  
2.  按一下功能表名稱，例如，File。  
  
     每個功能表會展開並公開命令的新項目方塊。  例如，您可以將 New、Open 和 Close 等命令新增至 \[檔案\] 功能表。  
  
3.  在新的項目方塊中，輸入新功能表命令的名稱。  
  
    > [!NOTE]
    >  您輸入的文字會出現在功能表編輯器和 \[[屬性](../Topic/Properties%20Window.md)\] 視窗中的 \[**標題**\] 方塊中。  您可以在任一位置編輯新功能表的屬性。  
  
    > [!TIP]
    >  您可以定義可讓使用者選取功能表命令的助憶鍵 \(熱鍵\)。  在字母前面輸入連字號 \(&\)，將其指定為助憶鍵。  使用者可以輸入該字母來選取功能表命令。  
  
4.  在 \[屬性\] 視窗中，選取要套用的功能表命令屬性。  如需詳細資訊，請參閱[功能表命令屬性](../windows/menu-command-properties.md)。  
  
5.  在 \[屬性\] 視窗的 \[**提示**\] 方塊中，輸入您想要在應用程式狀態列中顯示的提示字串。  
  
     這會在字串資料表中建立具有相同資源識別碼的項目，做為您建立的功能表命令。  
  
    > [!NOTE]
    >  提示只能套用至**快顯**屬性為 **True** 的功能表項目。  例如，如果最上層功能表項目有子功能表項目，就可以有提示。  提示的目的是指出當使用者按一下功能表項目時會發生什麼情況。  
  
6.  按下 **ENTER** 以完成功能表命令。  
  
     已選取新項目方塊，您就可以建立其他的功能表命令。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Menu Editor](../mfc/menu-editor.md)   
 [功能表](_win32_Menus)