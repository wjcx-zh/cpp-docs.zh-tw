---
title: "Changing a Symbol or Symbol Name (ID) | Microsoft Docs"
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
  - "vc.editors.symbol.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing a Symbol or Symbol Name (ID)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立新的資源或資源物件時，開發環境會為其指派預設的符號名稱，例如 IDD\_DIALOG1。  您可以使用 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)來變更符號名稱，或變更已與資源關聯之任何符號的名稱。  
  
### 變更資源的符號名稱  
  
1.  在 \[[資源檢視](../windows/resource-view-window.md)\] 中，選取資源。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[**屬性**\] 視窗中，輸入新的符號名稱，或在 \[**ID**\] 方塊中，從現有的符號清單中選取。  
  
     如果您輸入新的符號名稱，它會自動指派值。  
  
 您可以使用 [&#91;資源符號&#93; 對話方塊](../windows/resource-symbols-dialog-box.md)來變更目前未指派給資源的符號名稱。  如需詳細資訊，請參閱[變更未指定的符號](../windows/changing-unassigned-symbols.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Symbol Name Restrictions](../windows/symbol-name-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)