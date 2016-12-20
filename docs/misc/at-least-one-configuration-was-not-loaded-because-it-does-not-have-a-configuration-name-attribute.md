---
title: "At least one configuration was not loaded because it does not have a configuration name attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_nameless_config"
ms.assetid: 711f7253-308b-44e0-b8bc-ca5c16536a2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one configuration was not loaded because it does not have a configuration name attribute
.csproj 或 .vbproj 檔案中的每個 `<Config>` 區段，都必須擁有定義該組態唯一名稱的 Name 屬性 \(Attribute\)。  這項診斷表示 Name 屬性 \(Attribute\) 遺失了。  如果組態上的 Name 屬性 \(Attribute\) 遺失了，則組態將不會載入專案中。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
 **若要更正這個錯誤**  
  
-   將組態名稱插入至專案檔中的 `<Config>`  行之後。  
  
    ```  
    Name = "someconfigname"  
    ```  
  
     典型的組態名稱為  `Debug`  或  `Release`。  
  
## 請參閱  
 [專案檔](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)