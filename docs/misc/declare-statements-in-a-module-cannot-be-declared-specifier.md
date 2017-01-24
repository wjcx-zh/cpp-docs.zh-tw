---
title: "模組中的 Declare 陳述式不可以宣告為 &#39;&lt;規範&gt;&#39; | Microsoft Docs"
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
  - "vbc30786"
  - "bc30786"
helpviewer_keywords: 
  - "BC30786"
ms.assetid: 488b855f-72ea-414b-bffc-a5b63e97d289
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 模組中的 Declare 陳述式不可以宣告為 &#39;&lt;規範&gt;&#39;
`Declare` 宣告的規範在 `Module` 宣告內無效。 模組絕不會執行個體化、不支援繼承，且不能實作介面。  
  
 **錯誤 ID︰**BC30786  
  
### 更正這個錯誤  
  
-   請移除規範。  
  
## 請參閱  
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Module Statement](../Topic/Module%20Statement.md)