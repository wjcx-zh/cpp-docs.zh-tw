---
title: "&#39;&lt;類型名稱&gt;&#39; 類型無法繼承自類型參數 | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 類型無法繼承自類型參數
類別或介面包含可指定泛型類型參數的 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
 類型無法繼承自尚未定義的類型。 繼承涉及重複使用基底類別成員的功能，因此需要定義這些成員。 泛型類型參數是一個預留位置，該位置會由類型引數所提供的特定類型所取代。 因此，類型無法繼承自該預留位置。  
  
 **錯誤 ID：**BC32055  
  
### 更正這個錯誤  
  
-   如果繼承類型必須繼承自其他類型，請使用特定的類型而不是類型參數。  
  
-   如果基底類型必須由泛型類型參數代表，則其他類型皆不可繼承自該基底類型。 請移除 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)