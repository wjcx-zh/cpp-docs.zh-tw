---
title: "Imports 別名上不允許類型字元 | Microsoft Docs"
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
  - "vbc31398"
  - "BC31398"
helpviewer_keywords: 
  - "BC31398"
ms.assetid: 0620669d-b529-49f3-9deb-aeda4dacc58a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports 別名上不允許類型字元
`Imports` 陳述式中的匯入別名包含至少一個識別項類型字元。  
  
 匯入別名必須是有效的 Visual Basic 名稱。 允許的字元不包括任何識別項類型字元 \(`%`、`&`、`@`、`!`、`#` 和 `$`\)。 請參閱 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC31398  
  
### 更正這個錯誤  
  
-   請從匯入別名中移除一個或多個類型識別項字元。  
  
## 請參閱  
 [Type Characters](../Topic/Type%20Characters%20\(Visual%20Basic\).md)   
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [NOTINBUILD：當多個變數擁有相同名稱時解析參考](http://msdn.microsoft.com/zh-tw/9601e39f-1911-44e1-ace5-3f6e090408b9)