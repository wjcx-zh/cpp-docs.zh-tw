---
title: "Predefined Symbol IDs | Microsoft Docs"
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
  - "symbols, predefined IDs"
  - "predefined symbol IDs"
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Predefined Symbol IDs
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您開始新的專案時，視專案類型而定，已預先定義一些符號 ID 供您使用。  這些符號 ID 支援各種程式庫和專案類型，例如 MFC。  它們代表通常包含在任何應用程式中的一般工作，或硬體項目 \(如滑鼠或印表機\) 的動作。  
  
 使用資源時，這些符號 ID 變得重要。  適用於當您編輯快速鍵對應表時；其中有些 ID 已與虛擬按鍵相關聯。  您也可透過[屬性視窗](../Topic/Properties%20Window.md)取用。  您可以將任何預先定義的符號 ID 指派給新的資源，也可以將快速鍵指派給它們，而與符號 ID 相關聯的功能會自動與該按鍵組合相關聯。  
  
 這些程式庫有預先定義的符號，將顯示為專案的一部分：  
  
-   [MFC 預先定義的符號](../windows/mfc-predefined-symbols.md)  
  
-   [ATL 預先定義的符號](../windows/atl-predefined-symbols.md)  
  
-   [Win32 預先定義的符號](../windows/win32-predefined-symbols.md)  
  
    > [!NOTE]
    >  預先定義的符號一律是唯讀的。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32、MFC 或 ATL  
  
## 請參閱  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)