---
title: "&#39;?&#39; 字元不能用於此 | Microsoft Docs"
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
  - "bc36637"
  - "vbc36637"
helpviewer_keywords: 
  - "BC36637"
ms.assetid: a54c46e7-8fd8-4941-9fce-72f2b41b5e24
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;?&#39; 字元不能用於此
'?' 字元可以用來指定可為 Null 的實值類型或結構。 它在其他情況下的使用受到限制。 例如，下列程式碼會造成這個例外狀況。  
  
```  
' Not valid. ' #Const found = True?  
```  
  
 **錯誤 ID︰**BC36637  
  
### 更正這個錯誤  
  
-   請從宣告中移除 '?' 字元。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)