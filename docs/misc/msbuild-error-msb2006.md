---
title: "MSBuild 錯誤 MSB2006 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB2006
**專案檔未包含根項目 \<{0}\>。**  
  
 可能是根項目名稱拼字不正確，或是 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 無法辨識這個名稱。  
  
### 若要更正這個錯誤  
  
-   檢查項目名稱的拼字是否正確。  
  
-   檢查專案檔是否已修改或毀損。  如果專案已經修改或損毀，請使用當初建立這個專案的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本開啟、儲存，然後嘗試再轉換一次。  
  
## 請參閱  
 [Project File Schema Reference](../Topic/MSBuild%20Project%20File%20Schema%20Reference.md)   
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)