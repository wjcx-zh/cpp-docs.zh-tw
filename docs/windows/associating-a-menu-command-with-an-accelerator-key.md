---
title: "Associating a Menu Command with an Accelerator Key | Microsoft Docs"
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
  - "keyboard shortcuts, menu association"
  - "commands, associating menu commands with accelerator keys"
  - "menu commands, associating with keyboard shortcuts"
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Associating a Menu Command with an Accelerator Key
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

常常會有想讓功能表命令與快速鍵組合發出相同程式命令的時候。 若要達成這項目的，請使用功能表編輯器，將相同的資源識別項指派給功能表命令與應用程式快速鍵對應表中的項目。 您可以接著編輯功能表命令的[標題](../windows/menu-command-properties.md)，以顯示快速鍵的名稱。  
  
### 建立功能表命令和快速鍵的關聯  
  
1.  在**功能表**編輯器中，選取您想要的功能表命令。  
  
2.  在 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)中，將快速鍵的名稱加入 \[標題\] 屬性中：  
  
    -   在功能表標題後面輸入定位鍵 \(\\t\) 的逸出序列，讓所有的功能表快速鍵都靠左對齊。  
  
    -   輸入輔助按鍵 \(例如 **CTRL**、**ALT** 或 **SHIFT**\) 的名稱，後面接著加號 \(**\+**\) 和額外按鍵的名稱、字母或符號。  
  
         例如，若要將 **CTRL\+O** 指派給 \[檔案\] 功能表的 \[開啟舊檔\] 命令，您可以修改功能表命令的 \[標題\]，讓它變成：  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         功能表編輯器中的功能表命令將會更新，以反映您輸入的新標題。  
  
3.  在**快速鍵**編輯器中[建立快速鍵對應表項目](../windows/adding-an-entry-to-an-accelerator-table.md)，並為它指派與功能表命令相同的識別項。 請使用您認為容易記住的按鍵組合。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Adding Commands to a Menu](../windows/adding-commands-to-a-menu.md)   
 [Menu Editor](../mfc/menu-editor.md)