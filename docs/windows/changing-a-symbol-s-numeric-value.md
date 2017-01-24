---
title: "Changing a Symbol&#39;s Numeric Value | Microsoft Docs"
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
  - "vc.editors.symbol.changing.value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric values"
  - "symbols, numeric values"
  - "numeric values, changing symbols"
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing a Symbol&#39;s Numeric Value
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於單一資源相關聯的符號，您可以使用 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md)來變更符號值。  您可以使用 [&#91;資源符號&#93; 對話方塊](../windows/resource-symbols-dialog-box.md)來變更目前未指派給資源的符號值。  如需詳細資訊，請參閱[變更未指定的符號](../windows/changing-unassigned-symbols.md)。  
  
### 變更指派給單一資源或物件的符號值  
  
1.  在 \[[資源檢視](../windows/resource-view-window.md)\] 中，選取資源。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[**屬性**\] 視窗中，輸入符號名稱，後面接著 \[**ID**\] 方塊中的等號和一個整數，例如：  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 下一次儲存專案時，會在符號標頭檔中儲存新值。  在 \[ID\] 方塊中，只有符號名稱保持可見狀態；在驗證之後，將不會顯示等號和值。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Symbol Value Restrictions](../windows/symbol-value-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)