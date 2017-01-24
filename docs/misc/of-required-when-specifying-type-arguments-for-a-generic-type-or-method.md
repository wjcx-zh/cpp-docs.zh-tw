---
title: "為泛型類型或方法指定類型引數時需要 &#39;Of&#39;。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32093"
  - "vbc32093"
helpviewer_keywords: 
  - "BC32093"
ms.assetid: 9a1baf12-a4a4-442d-9baa-852ad30a956b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 為泛型類型或方法指定類型引數時需要 &#39;Of&#39;。
陳述式嘗試透過泛型類型建構類型或呼叫泛型方法，但未使用 [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md) 子句。  
  
 針對泛型類型的 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 語法會呼叫類型參數和類型引數，以由 `Of` 關鍵字引入。 此外，類型參數清單或類型引數清單必須括在括弧內。  
  
 **錯誤 ID：**BC32093  
  
### 更正這個錯誤  
  
-   在類型引數清單開頭包含 `Of` 關鍵字，並將整個清單括在括弧內。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [如何：使用泛型類別](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)