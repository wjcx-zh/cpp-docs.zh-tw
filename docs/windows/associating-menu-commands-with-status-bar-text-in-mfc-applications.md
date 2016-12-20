---
title: "Associating Menu Commands with Status Bar Text in MFC Applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "status bars, associating menu items"
  - "menus, status bar text"
ms.assetid: 757c0e02-bc97-493f-bccd-6cc6887ebc64
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associating Menu Commands with Status Bar Text in MFC Applications
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的應用程式可以針對使用者可能選取的每一個功能表命令顯示描述性文字。 做法是使用 \[屬性\] 視窗中的 \[**提示**\] 屬性，將文字字串指派給每一個功能表命令。 如果您在[字串表](../mfc/string-editor.md)中具有其識別碼與命令相同的字串，則當使用者將滑鼠停留在功能表項目時，MFC 應用程式將在執行中應用程式的狀態列中自動顯示此字串資源。  
  
### 若要建立功能表命令與狀態列文字字串的關聯  
  
1.  在 \[**功能表**\] 編輯器中，選取功能表命令。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)的 \[**提示**\] 方塊中，輸入相關聯的狀態列文字。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 MFC  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [Adding Commands to a Menu](../windows/adding-commands-to-a-menu.md)   
 [Menu Editor](../mfc/menu-editor.md)