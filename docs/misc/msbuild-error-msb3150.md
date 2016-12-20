---
title: "MSBuild 錯誤 MSB3150 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3150
**MSB3150: 沒有可用來建置啟動載入器文化特性 '{0}' 的字串資源。**  
  
 如果找到了 setup.xml 但沒有包含字串節點，就會發生這個錯誤。  此 XML 檔案可能已經毀損。  
  
### 若要更正這個錯誤  
  
-   移至 \[**控制台**\]，選取 \[**新增或移除程式**\]，然後修復 Visual Studio SDK，或者將檔案複製到適當的目錄 \(\<SDK install path\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\)。