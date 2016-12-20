---
title: "MSBuild 錯誤 MSB2008 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB2008
**這個 Visual Studio 專案系統無法轉換 "{0}" 專案。  它只能用來轉換 C\# 和 VB 用戶端專案。**  
  
 只有有效的 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 與 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案可以使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 進行轉換。  
  
### 若要更正這個錯誤  
  
-   如果專案屬於 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案，請檢查專案檔是否已修改或毀損。  如果專案已經修改或損毀，請使用當初建立這個專案的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本開啟、儲存，然後嘗試再轉換一次。  
  
-   如果不是 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 專案，請使用適當的工具進行轉換。  
  
## 請參閱  
 [其他資源](../Topic/Additional%20MSBuild%20Resources.md)