---
title: "前置的 &#39;.&#39; 或 &#39;!&#39; 不能出現在常數運算式中 | Microsoft Docs"
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
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 前置的 &#39;.&#39; 或 &#39;!&#39; 不能出現在常數運算式中
成員存取 \(.\) 和字典成員存取 \(\!\) 需要有一個運算式指定大部分時間包含該成員的項目，包括常數運算式。 下列宣告無效。  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **錯誤 ID：**BC30995  
  
### 更正這個錯誤  
  
-   請指定包含您想要存取之成員的執行個體。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [如何：宣告匿名類型的執行個體 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Const Statement](../Topic/Const%20Statement%20\(Visual%20Basic\).md)