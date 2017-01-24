---
title: "在模組中的變數不可以宣告為 &#39;&lt;規範&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30593"
  - "vbc30593"
helpviewer_keywords: 
  - "BC30593"
ms.assetid: 2500b776-7fa4-4272-8cc7-204593706651
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在模組中的變數不可以宣告為 &#39;&lt;規範&gt;&#39;
您已在 `Module` 陳述式的變數上使用規範 \(例如 `MustInherit`\)。 模組絕不會執行個體化、不支援繼承，且不能實作介面。  
  
 **錯誤 ID︰**BC30593  
  
### 更正這個錯誤  
  
-   請移除規範。  
  
## 請參閱  
 [Module Statement](../Topic/Module%20Statement.md)