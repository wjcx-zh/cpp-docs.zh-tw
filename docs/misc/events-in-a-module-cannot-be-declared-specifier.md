---
title: "在模組中的事件不可以宣告為 &#39;&lt;規範&gt;&#39; | Microsoft Docs"
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
  - "bc30434"
  - "vbc30434"
helpviewer_keywords: 
  - "BC30434"
ms.assetid: ac6a63e3-89a6-4fbb-ade1-4fa033252379
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在模組中的事件不可以宣告為 &#39;&lt;規範&gt;&#39;
您已經在 `Module` 陳述式內使用對事件無效的規範。 模組絕不會執行個體化、不支援繼承，且不能實作介面。  
  
 **錯誤 ID：**BC30434  
  
### 更正這個錯誤  
  
-   請移除規範。  
  
## 請參閱  
 [Module Statement](../Topic/Module%20Statement.md)