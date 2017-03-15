---
title: "Creating New Symbols | Microsoft Docs"
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
  - "vc.editors.symbol.creating"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "New Symbol dialog box"
  - "symbols, creating"
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating New Symbols
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您開始新的專案時，您可能會發現先對應符號名稱，再建立將指派到的資源很方便。  
  
### 使用資源符號對話方塊建立新符號  
  
1.  在 [&#91;資源符號&#93; 對話方塊](../windows/resource-symbols-dialog-box.md)中，選擇 \[**新增**\]。  
  
2.  在 \[**名稱**\] 方塊中，輸入符號名稱。  
  
3.  接受指派的符號值。  
  
     \-或\-  
  
     在 \[**值**\] 方塊中輸入新值。  
  
4.  按一下 \[**確定**\]，將新符號加入至符號清單。  
  
 如果您輸入的符號名稱已經存在，此時會出現訊息方塊，說明已定義使用該名稱的符號。  您不能定義兩個或多個具有相同名稱的符號，但您可以定義具有相同數值的不同符號。  如需詳細資訊，請參閱[符號名稱限制](../windows/symbol-name-restrictions.md)和[符號值限制](../windows/symbol-value-restrictions.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Viewing Resource Symbols](../windows/viewing-resource-symbols.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)