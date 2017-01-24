---
title: "泛型類型 &#39;&lt;泛型類型名稱&gt;&#39; 無法匯入多次 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 泛型類型 &#39;&lt;泛型類型名稱&gt;&#39; 無法匯入多次
[Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md) 指定了使用不同類型參數化匯入的泛型類型。  
  
 您可以宣告來自泛型類型的多個建構類型，因為您未藉由宣告建構類型來重新定義泛型類型。 不過，如果您多次匯入泛型類型，這相當於多次定義。  
  
 **錯誤 ID︰**BC32086  
  
### 更正這個錯誤  
  
1.  如果包含此 `Imports` 陳述式的原始程式檔也包含另一個指定相同泛型類型的 `Imports` 陳述式，請移除其中一個。  
  
2.  如果您需要使用不同的類型參數化匯入相同的泛型類型，請使用多個原始程式檔。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)