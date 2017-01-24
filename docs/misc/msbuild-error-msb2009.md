---
title: "MSBuild 錯誤 MSB2009 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB2009
**項目 '\<element name\>' 的屬性 \(Attribute\) '\<attribute name\>' 無效。**  
  
 屬性名稱拼字不正確，或是 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 無法辨識這個名稱。  
  
### 若要更正這個錯誤  
  
-   檢查屬性名稱拼字是否正確。  
  
-   檢查專案檔是否已修改或毀損。  如果專案已經修改或損毀，請使用當初建立這個專案的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本開啟、儲存，然後嘗試再轉換一次。  
  
## 請參閱  
 [Project File Schema Reference](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)