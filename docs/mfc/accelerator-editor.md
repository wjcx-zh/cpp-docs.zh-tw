---
title: "Accelerator Editor | Microsoft Docs"
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
  - "vc.editors.accelerator.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator tables [C++], editing"
  - "tables [Visual Studio], accelerator key"
  - "accelerator keys"
  - "resource editors, Accelerator editor"
  - "keyboard shortcuts [C++], Accelerator editor"
  - "Accelerator editor"
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Accelerator Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

快速鍵對應表是一種 Windows 資源，其中包含快速鍵清單 \(也稱為快速鍵\) 和與其相關聯的命令識別項。 程式可有多個快速鍵對應表。  
  
 一般而言，快速鍵是用作程式命令的鍵盤快速鍵，功能表或工具列也使用這些命令。 不過，您可以使用快速鍵對應表定義和使用者介面物件沒有關聯性的命令鍵組合。  
  
 您可以使用[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)連結快速鍵命令和程式碼。  
  
 使用快速鍵編輯器，您可以：  
  
-   [設定快速鍵屬性](../windows/setting-accelerator-properties.md)  
  
-   [建立快速鍵與功能表項目的關聯](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [編輯快速鍵對應表](../windows/editing-accelerator-tables.md)  
  
-   [使用預先定義的快速鍵](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  使用快速鍵編輯器時，您可以按一下滑鼠右鍵顯示常用命令的快顯功能表。 可用的命令取決於指標所指項目。  
  
    > [!NOTE]
    >  Windows 不允許建立空的快速鍵對應表。 如果建立了沒有任何項目的快速鍵對應表，當您儲存資料表時它會自動刪除。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)